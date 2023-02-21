---
layout: post
title:  2022 Affective Computing and Intelligent Interaction Conference
date:   2022-12-06
categories: dialog conferences emo20q ACII emotion
# naming: `YEAR-MONTH-DAY-title.MARKUP`
# Where `YEAR` is a four-digit number, `MONTH` and `DAY` are both two-digit numbers, and `MARKUP` is the file extension representing the format used in the file. After that, include the necessary front matter. Take a look at the source for this post to get an idea about how it works.

---

I attended a very interesting conference a few weeks ago, the 10th
[Affective Computing and Intelligent Interaction
(ACII)](https://acii-conf.net/2022/). I wanted to share some
interesting topics that I learned about. I hope this will disseminate
some of the important ideas of the conference and some of the ethical
considerations related to technologies presented at the conference. I
think the ACII conference did a good job of highlighting these ethical
considerations and also it is incumbent on people who work in these
areas to share information about the new technologies to the public. I
won't be able to go through the whole four day conference but I'll try
to briefly describe the conference and mention some of the main
presentations that stuck out to me. I'll also describe the study I
presented, Emotion Twenty Questions Dialog System for Lexical
Emotional Intelligence.


First, the conference gets its name from Affective Computing, a field
that's been around in some form for a while, but whose name was coined
Rosalind Picard of the MIT Media Lab (they are hosting [next year's
ACII](https://acii-conf.net/2023/)). The basic premise of this field
is that computers, devices, and other systems that are aware of human
emotions (affect) will enable better human-computer interaction. The
conference has been around since 2003 and it's the 10th conference, so
it has been held approximately every other year (last year it became
annual after being biennial). In the period since the ACII conference
was started, the types and capabilities of computers and devices has
changed a lot (e.g. smartphones, social media, deep learning), so the
field of affective computing has changed a lot too. The theme of [last
year's ACII conference](https://www.acii-conf.net/2021/) was "ethical
affective computing" and this year's theme was "affective computing
and mental health". I think these trends show that the field is
addressing some of the negative possibilities of affective computing
technologies.

One famous example of a negative use of affective computing
technologies was an experiment at Facebook/Meta where researchers
experimented with changing the proportion of positive and negative
stories in users' timelines in a study called [Emotional Contagion in
Social
Networks](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4066473/). Of
course, people rightfully felt like they were being manipulated in an
experiment without explicit consent.


One of the keynote lectures of ACII this year explored this topic of
consent in affective computing. In this keynote, Rafael A. Calvo, of
the Dyson Institute (yes, the institute founded by Sir James Dyson of
Dyson vacuum fame), used [the Skinner-Rogers debate in 1962 at the
University of Minnesota Duluth (yay,
Minnesota!)](https://cehsp.d.umn.edu/articles/skinner-and-rogers) to
illustrate the theme of manipulation in psychology. This "debate of
the century" pitted the behavioralist psychologist B.F. Skinner
against the humanist psychologist Carl Rogers (there is also another
famous "debate of the century" between Skinner and Noam
Chomsky). Though Skinner had achieved a lot of success in exploring
and leveraging animal and human learning in his work (and he was very
persuasive and funny in his arguments), Rogers was prescient in his
intuitive skepticism about trying to manipulate people's behavior and
the long-term consequences of a purely behavioralist
approach. Prof. Calvo suggested that the audience consider Roger's
perspective and showed the importance of the idea of autonomy in
several AI declarations, such as the [EU AI
Act](https://artificialintelligenceact.eu/). The [whole Skinner-Rogers
debate "A Dialog on Education and Control" can be found on
Youtube](https://www.youtube.com/watch?v=olg4Az_hV4Y). It's 4 hours
long, but it was good stuff.

Another keynote was given by Jeffrey Cohn, a psychologist at the
University of Pittsburg. Actually he had other papers and
presentations as well as the keynote, so I may be combining ideas from
each. One term that really stuck out was smile ballistics, i.e. the
trajectory of a smile from resting face to smile and back again. One
of the areas of affective computing under rapid development right now
is facial recognition of users' expressions and another is simulating
emotions in robots and avatars. For the latter, if the smile
ballistics are not right, the robot or avatar will look artificial or
["uncanny"](https://en.wikipedia.org/wiki/Uncanny_valley). There are
many applications for this technology: facial animation (The Walt
Disney Company was one of the conference sponsors) and behavioral
analytics (ETS, the Educational Testing Service, was another
sponsor. Prof. Cohn had a very novel application of facial emotion
recognition: deep brain stimulation surgery for intractable obsessive
compulsive disorder (OCD). When a patient's OCD is so bad, the only
thing they want to do is the obsessive behavior, which in the extreme
can completely prevent them from living a normal, healthy life. These
compulsive behaviors give the patient pleasure in a way, but disrupt
normal functioning. Implanting a brain stimulator in the cingulate
corpus disrupts this by producing a wave of happiness separate from
the OCD behavior. The way that surgeons can measure that the electrode
is in the right place is by a very big smile on the patient, called
the mirth response, and measuring the maximum trajectory of the smile
is a quantitative way to determine that the electrode is in the right
place. Going back to the ethics issue, of course this kind of surgery
is very invasive, so the ethical issues are more similar to medical
ethics than AI ethics, so the facial recognition aspect is less of a
concern in this case compared to surveillance applications of facial
recognition. This type of surgery was pioneered for Parkinson's
disease.


Besides memorable terms like smile ballistics and mirth response,
another interesting term I learned at ACII was eustress, a positive
form of stress. When we hear the word "stress" there is a negative
connotation (distress). However, we can think of a positive form of
stress where this is some form of strain or exertion, but it is
enjoyable or beneficial. Dimitra Dritsa and Dr. Nimish Biloria from
the Universities of Eindhoven, Sidney, and Johannesburg did a study of
stress in the context of architecture and urban design for a smart
city application. Subjects would wear a sensor that measured galvanic
skin response (skin conductance) so it measured both good and bad
stress reflected in sweat or clammy skin. I went back to read the
paper and I think "eustress" actually came up from the audience
questions, not the paper, but the idea was that the devise would
register a similar response if the stress was negative (being lost in
a noisy, traffic-y, unfamiliar neighborhood) or when vigorously
exploring an exciting, new place. This resonated with me because the
conference enabled me to visit Japan for the first time and I think
something like "eustress" kept me going despite the long plane ride,
jetlag, and different language and culture. The eustress/distress
distinction also illustrates a way of modeling emotion as a two
dimensional space of pleasure and arousal. In this case eustress and
distress are both highly aroused, but differ in terms of the pleasure
dimension (positive/pleasure vs negative/displeasure) . Certain
emotion recognition methods may be able to identify one dimension
better than another. In this case the physiological signal of
electro-dermal response is able to recognize the arousal in the stress
but not the pleasure dimension. Another study by Han Yu, Thomas
Vaessen, Inez Myin-Germeys, and Akane Sano at Rice University and Ku
Leuven did a similar study measuring subjects in daily life with
electrocardiograms in addition to galvanic skin response and looked at
building personalized machine learning models.

Another paper where the eustress/distress distinction came up
explicitly a study to measure workplace stress in remote workers by
Mehrab Bin Morshed, Javier Hernandez, Daniel McDuff, Jina Suh, Esther
Howe, Kael Rowan, Marah Abdin, Gonzalo Ramos, Tracy Tran, and Mary
Czerwinski from Microsoft Research, Georgia Tech, and
Berkeley. Besides using the term eustress, they also used another
well-fitting, evocative term, digital phenotype, which is a profile of
a user's digital activity. The information they used to build this
digital phenotype was from surveys (both before, during, and after the
study) about sleep, emotions, workload, food, and drink; email,
calendar, and other application usage; face position and facial action
units; and other physiological data from the user's webcam (I remember
meeting Javier Hernandez, one of the authors, at ACII 2011 when he
presented about using webcams to measure heart rate). This paper had a
component that surveyed they subjects about how comfortable they were
with different data collection modalities and data storage scenarios
(local or remote), so I think this is a good example of the affective
computing field being ethically aware of the study and its
implications. Of course it's possible to imagine dystopian
possibilities where companies police their workers' emotions, but if
used correctly, it may be a way to create an optimal work environment
where employees have enough, but too much stimulation and the digital
phenotype information would be collected consensually.

This brings up another set of well-fitting terms that illustrates the
ethical concerns of such technology, surveillance vs sousveillance. In
surveilance, people are monitored by others without their consent and
not generally for their benefit (sur-, over, -veillance, to watching),
while in sousveillance, people have consent and control over the data
that is collected about them for their benefit (sous-,
under/subservient like a sous-chef is subservient to the chef, the
data collection is subservient to the user).

Another good example of facial recognition that I saw at the
conference was the FaceGame demo by Krist Shingjergji, Deniz Iren,
Corrie Urlings, and Roland Klemke. It is an experiment that uses a
game to collect facial expression data. It is hard to collect facial
expression data because emotion expression is ephemeral and often
rare. Also, not everyone is an actor that can produce precise
expressions on demand. The FaceGame experiment uses facial action
codes to generate a face with a precise expression and then asks the
user/subject to copy that expression. The system then automatically
analyzes the user's facial action units to give feedback (i.e., raise
your left eyebrow and flair your nostrils a bit, so that the user will
replicate the expression faithfully. This was one presentation that
came with a demo so it was cool to see the software in
action, [you can try here](https://facegame.org/).


My presentation was also a demo of a data collection game called
Emotion Twenty Questions (EMO20Q) that I made with two students, Ola
Sanusi and Summer (Huihui) Nie from the University of St. Thomas
Graduate Programs in Software and Data Science. Like the FaceGame, the
goal of my team's demo was to collect emotional data, but in our case
we wanted to collect text-based data of users describing emotions in a
dialog setting (speaking of dialog, Apple was one of the sponsors of
the conference and I had a chance to talk to someone from the Siri
group). In EMO20Q two players try to guess the emotion that the other
is thinking, like the normal twenty questions game, but with emotion
words. If our efforts to put the demo online are still working, you
can try it at [emo20q.org](https://emo20q.org).  In the past (when I
was a grad student working on my dissertation) I made an automated
agent that played the question-asking role, but the question-answering
role was harder because the when the user is asking questions he/she
has the dialog initiative (i.e. it becomes a user initiative dialog
setting rather than system initiative setting). However, now 10 years
after my grad school days, natural language processing technology
(NLP) has advanced so much that the question-answering role is much
easier due to large language models (LLMs) like BERT. We used BERT to
encode emotion questions into BERT's typically two-sentence slot imput
format: "\<CLS\> emotion \<SEP\> question". For example, if the
question-answering agent picked the emotion "stress" and the user
asked "is it a positive emotion?", the BERT input would be "\<CLS\>
stress \<SEP\> is it a positive emotion?". The output vector of the
\<CLS\> token is used by the agent's machine learning model classify the
input into "yes", "no", or "maybe" by fine-tuning the pre-trained BERT
model with older data that I collected when I was a grad
student. Actually the first time I attended ACII was when I was a grad
student finishing my dissertation, so this was somewhat of a patient
(or lazy) way of completing the project by waiting for the technology
to solve the problem that had stumped me when I was doing my PhD. You
can see [our demo paper at Arxiv "Emotion Twenty Questions Dialog System for Lexical motional"](https://arxiv.org/pdf/2210.02400.pdf). We also
published code for the
[dialog agent](https://github.com/abecode/emo20q) and
[web frontend](https://github.com/abecode/emo20q-web).

Finally, to return to the topic of ethics, I also wanted to mention a
layer of ethics review that happens at universities before starting a
project of this kind of research. Universities that conduct research
have an Institutional Review Board (IRB) that vets and documents
research projects that have human subjects. This is especially
important in medical studies (e.g brain implants for OCD), but many
other fields dial with human subjects, including participants of
statistical surveys, interviewees in historical research, and users of
computer programs. The University of St. Thomas has a very active IRB
(thanks Sarah Muenster-Blakley!) that does this vetting and also runs
seminars a few times a semester.


This wasn't a complete overview of the ACII 2022 conference by any
means, just a quick taste of some of the things that stood out and I
felt like relaying to the general public here on on my blog. For more
information, the proceedings can be found at the [IEEE Explore
website](https://ieeexplore.ieee.org/xpl/conhome/9597394/proceeding),
although the demo system and doctoral consortium papers are not posted
yet.

