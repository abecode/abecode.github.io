---
layout: post
title:  "Logging Twitter for Years with Tweepy, POSIX/UNIX Signals, Logrotate, Systemd, and S3"
date:   2021-07-23 10:00:0 -0500
categories: twitter devops linux aws
# naming: `YEAR-MONTH-DAY-title.MARKUP`
# Where `YEAR` is a four-digit number, `MONTH` and `DAY` are both two-digit numbers, and `MARKUP` is the file extension representing the format used in the file. After that, include the necessary front matter. Take a look at the source for this post to get an idea about how it works.

---

I've been running a Twitter listener for about 2 years and it's done a
pretty good job of staying up and running during that time.  In this
post I want to explain a bit about how it works.  Using utilities
outside of Python like `logrotate`, `systemd` and `aws s3` make the
Python code look very simple but the interaction of all these is a bit
complex.  Also, even though the python script is pretty short, there
are a few tricks.

First, let's look at the python script. the code is in the
[listen-and-log.py
file](https://github.com/abecode/twitter-logger/blob/main/listen-and-log.py). The
first 19 lines are imports and environment variables:

<script src="http://gist-it.appspot.com/http://github.com/abecode/twitter-logger/raw/main/listen-and-log.py?slice=0:20"></script>

Tweepy is the library that actually connects to Twitter, the json
library parses the json respons, the os library is used for retrieving
environment variables, the signal library is how logrotate signals the
script when it's time to rotate the logfile, sys is used for printing
to stderr, and urllib3 is used to catch a type of error (it looks like
I commented that exception out.

Then I get environment variables.  Environment variables are a good
way to pass contextual configuration information to the script.
Search 12-factor app, principle 3 for more information. The first
environment variable `TWITTER_USER` is the user whose friendswe will
follow.  In this case, I'm getting data from an account that I set up
with username `abestockmon` (i.e., it's a dummy account to monitor
stock news ("fintwit").  The following environment variables are
tokens provided by Twitter. To get this information from Twitter, you
need to get a developer account and create a project.  Since I set
this up two years ago I don't remember exactly what each of these do
but you can see their usage later in the script.

Finally, the last line opens the log file.  This is where the json
from Twitter will be saved.  It's slightly different from the normal
file opening in python.  First, it's opening a gzip file, so
everything that's written will be saved as gzip.  Second, it doesn't use the normal 

```python
with open(file) as f:
  ...
```

idiom.  This is because we want the file handle to be available to the next function:

<script src="http://gist-it.appspot.com/http://github.com/abecode/twitter-logger/raw/main/listen-and-log.py?slice=22:30"></script>

This function is called when the HUP (hangup) signal is received.
Signals are kind of cool because unlike ordinary Python function calls
they can get called from outside the Python script and they are called
in the middle of the script execution, interrupting the script.  So
the script is running, writting json from Twitter and it receives the
HUP signal.  Wherever the script is, it will run this function.  It
takes the filehandle `f`, saves it to the `f_old` variable, then opens
a new file, and closes the old file.  Anything that was being written
will go to the old file, but anything that runs after this function is
going to the new file.  It looks like these would be the same file,
but actually logrotate has changed the file name outside of the python
script (the old file is renamed to `twitter.log.gz.1`).


The next chunk defines a stream listener class that simply writes the
received json from Twitter to the logfile:

<script src="http://gist-it.appspot.com/http://github.com/abecode/twitter-logger/raw/main/listen-and-log.py?slice=32:39"></script>

The following function takes the stream and a list of twitter users
and filters the stream bast on this followlist:

<script src="http://gist-it.appspot.com/http://github.com/abecode/twitter-logger/raw/main/listen-and-log.py?slice=40:50"></script>


The main function below sets up the signal handler, the Twitter
credentials, gets the users that the `abestockmon` user follows,
creates the stream, and then runs `filter` on the stream:

<script src="http://gist-it.appspot.com/http://github.com/abecode/twitter-logger/raw/main/listen-and-log.py?slice=51:68"></script>


If this running script did not receive any signal from outside, it
would keep writing to its logfile, which would grow and grow.  We can
manually send a HUP signal like this:

```bash
kill -HUP $(pgrep -f listen-and-log.py)
```

This is what I did when I was testing the script, but logrotate does
it automatically and the logrotation is specified declaratively in the
logrotate.conf file:

<script src="http://gist-it.appspot.com/http://github.com/abecode/twitter-logger/raw/main/logrotate.conf"></script>

This config file tells the logrotate UNIX/Linux command where the
logfile is, minimally how often to rotate it, what the maximum size
should be before it is rotated, and how many old log files are saved.
The `postrotate` block specifies what happens after the log is
rotated, i.e., renaming the twitter.log.gz file to twitter.log.gz.1.
The main thing is that `logrotate` sends the Python script to send the
HUP signal and then it copies the old log file to aws S3.  This
prevents logfiles from accumulating on the server and offloads them to
AWS S3. 

Finally, every now and then there can be transient issues that will
cause the script to fail and die.  It could happen in the middle of
the night and I wouldn't know about it so I wanted to make sure that
it restarted automatically.  To do this, I created a Systemd service
unit file:

<script src="http://gist-it.appspot.com/http://github.com/abecode/twitter-logger/raw/main/listen-and-log.service"></script>

A service unit file will make the script run as a daemon in the
background. It reads an enviroment variable file and it will restart
the process after two seconds if it fails.  Waiting two seconds is
good because if you try to restart too quickly you could overload the
system. The final line makes the script start automatically when the
AWS Linux VM starts.

This looks simple but it took some work to get it working right.  I
learned this pattern from my old boss Kim Scheibel, then at Adly, now
at Google (thanks Kim!).  Back then we used Upstart instead of Systemd
(Systemd is still relatively new although now it is the default).

This approach does lose data when the script restarts.  In a more
critical system, we would have multiple listeners running in different
availability zones so that if a problem happened to one, then there
would be another that would most likely still be running.  This would
require a deduplication phase and so it gets a lot more complex than
what I've shown here.

