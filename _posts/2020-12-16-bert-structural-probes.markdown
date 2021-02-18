---
layout: post
title:  "BERT Structural Probes"
date:   2020-12-05 15:33:43 -0600
categories: jekyll update
# naming: `YEAR-MONTH-DAY-title.MARKUP`
# Where `YEAR` is a four-digit number, `MONTH` and `DAY` are both two-digit numbers, and `MARKUP` is the file extension representing the format used in the file. After that, include the necessary front matter. Take a look at the source for this post to get an idea about how it works.

---



c.f. [John Hewitt's Structural Probes Github repo](https://github.com/john-hewitt/structural-probes)



use virrtualenv instead of conda
```{bash}
mkvirtualenv structuralprobe -p $(which python3.7)
```

use pip instead of conda
```{bash}
pip install -r requirements.txt
```

install pytorch
```{bash}
pip install torch torchvision torchaudio
pip install pytorch-pretrained-bert
```
