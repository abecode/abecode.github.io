---
layout: post
title:  "Using Django to Teach Databases"
categories: django stthomas databases 630
# naming: `YEAR-MONTH-DAY-title.MARKUP`
# Where `YEAR` is a four-digit number, `MONTH` and `DAY` are both two-digit numbers, and `MARKUP` is the file extension representing the format used in the file. After that, include the necessary front matter. Take a look at the source for this post to get an idea about how it works.

---

I've been trying using Django's ORM to teach some database topics:
object-relational-mapping, foreign keys, automatically generated
intersection tables vs association tables (Django model "through"
attribute), forward and reverse engineering, and migrations.  [Here's
a basic django model that I've been using in the class (SEIS
630)](https://github.com/abecode/630_django_example).  You can check
out the code but it's better to go through the steps using
`django-admin` and `manage.py`.
