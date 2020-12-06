---
layout: post
title:  "Welcome to Jekyll and Github Pages!"
date:   2020-12-05 15:33:43 -0600
categories: jekyll update
# naming: `YEAR-MONTH-DAY-title.MARKUP`
# Where `YEAR` is a four-digit number, `MONTH` and `DAY` are both two-digit numbers, and `MARKUP` is the file extension representing the format used in the file. After that, include the necessary front matter. Take a look at the source for this post to get an idea about how it works.

---

This was my first time using Jekyll after using Github Pages
(gh-pages) a couple of times for several projects, e.g. generating
[some pages to display Chinese emo20q
data](https://abecode.github.io/emo20q-cn/), which were generated
programatically from the data into the default gh-pages and [a site I
use for teaching SEIS 631](https://abecode.github.io/631-rtopics/),
the stats and R data analysis at UST GPS, which was created using
RStudio and RMarkdown.


I'll also test out code snippets:

I don't use Ruby too much but it's the language of Jekyll:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}


Python, my main language:

{% highlight python %}
def print_hi(name):
  print(f"hi {name}")

print_hi('Tom')
#=> print 'hi Tom' to STDOUT.
{% endhighlight %}

R, my recent go-to language and what I've been teaching:

{% highlight R %}
print_hi <- function(name){
  cat("hi", name)
}
print_hi('Tom')
#=> print 'hi Tom' to STDOUT.
{% endhighlight %}


Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
