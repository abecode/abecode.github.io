---
layout: post
title:  BERT-Assisted Semantic Annotation Correction for Emotion-Related Questions
date:   2022-01-17
categories: BERT NLP writing conferences emo20q annotation paraphrase
# naming: `YEAR-MONTH-DAY-title.MARKUP`
# Where `YEAR` is a four-digit number, `MONTH` and `DAY` are both two-digit numbers, and `MARKUP` is the file extension representing the format used in the file. After that, include the necessary front matter. Take a look at the source for this post to get an idea about how it works.

---

I recently got a paper [BERT-Assisted Semantic Annotation Correction
for Emotion-Related Questions](/assets/2022007804.pdf) accepted at the
[ARDUOUS 2022 workshop (Annotation of useR Data for UbiquitOUs
Systems)](https://text2hbm.org/arduous/) of the [IEEE Pervasive
Computing (PerCom) conference](https://www.percom.org/).  It was going
to be in Pisa, Italy, but unfortunately due to Covid it is now
virtual/online.

I wanted to make a short post to describe the paper and share some
resources that can be used to replicate it.

First, to summarize, the paper is about using machine learning (ML)
models, BERT in particular, to assist annotation by correcting
incorrect annotations. There's been a lot of work in automating the
annotation task and this is one take on it (other directions in this
area are preannotation, using ML to roughly annotate the data first
and having humans fix problems, and online, incremental, and active
learing to complete either learn while the humans annotate and/or
choosing informative examples for humans to annotate).

I was inspired to look at this because I realized that the BERT models
performed so well that they identified errors in my earlier
annotations.  When I was a grad student I did annotation by myself and
didn't have the opportunity to check inter-annotator agreement.  I had
already used funding to collect data on mturk and the performance of
my system was good so I skipped the inter-annotator agreement, but it
was always something I thought I should do at some point.  This
current paper didn't give inter-annotator agreement but it solved the
issue of finding annotation errors, which is one of the reasons to find
inter-annotator agreement.

The data came from EMO20Q, a dialog system to play an emotion-guessing
game (20 questions, but limited to emotions).  More info about the
EMO20Q project and data can be found at the [github
repo](https://github.com/abecode/emo20q).  The most relevant previous
paper is
[here](https://scholar.google.com/scholar?oi=bibs&hl=en&cluster=7144330598938288097)
and
[here](https://scholar.google.com/citations?view_op=view_citation&hl=en&user=9Bma3uAAAAAJ&sortby=pubdate&citation_for_view=9Bma3uAAAAAJ:Wp0gIr-vW9MC)
[are](https://scholar.google.com/citations?view_op=view_citation&hl=en&user=9Bma3uAAAAAJ&sortby=pubdate&citation_for_view=9Bma3uAAAAAJ:4DMP91E08xMC)
[some](https://scholar.google.com/citations?view_op=view_citation&hl=en&user=9Bma3uAAAAAJ&sortby=pubdate&citation_for_view=9Bma3uAAAAAJ:M3ejUd6NZC8C)
[other](https://scholar.google.com/citations?view_op=view_citation&hl=en&user=9Bma3uAAAAAJ&sortby=pubdate&citation_for_view=9Bma3uAAAAAJ:0EnyYjriUFMC)
[older](https://scholar.google.com/citations?view_op=view_citation&hl=en&user=9Bma3uAAAAAJ&sortby=pubdate&citation_for_view=9Bma3uAAAAAJ:LkGwnXOMwfcC)
[publications](https://scholar.google.com/citations?view_op=view_citation&hl=en&user=9Bma3uAAAAAJ&sortby=pubdate&citation_for_view=9Bma3uAAAAAJ:hqOjcs7Dif8C)
as well as a [newer poster by a student, Shanshan
Kong](https://scholar.google.com/citations?view_op=view_citation&hl=en&user=9Bma3uAAAAAJ&sortby=pubdate&citation_for_view=9Bma3uAAAAAJ:YlPif8NxrbYC).

Thanks to the ease of sharing via github and the convenient GPU
notebook platform Colab, it's possible to easily reproduce the work.
If you are interested, please see [this notebook for
details](https://colab.research.google.com/drive/1sXqTT2DoJ1hFBR02iM8W4GKZe5OxCYJy?usp=sharing).
