# abecode.github.io

[Ebrahim (Abe) Kazemzadeh's github homepage and blog](https://abecode.github.io "Ebrahim (Abe) Kazemzadeh's github homepage and blog")


to serve locally using Jekyll
```
bundle exec jekyll serve
```

ugh, stupid Ruby, instead of wasting time installing on mac, use Docker/Rancher:

```
nerdctl pull jekyll/jekyll
nerdctl run  -it -p8123:80 -v "$PWD:/srv/jekyll" jekyll/jekyll /bin/bash
jekyll build
```

finally, install by brew, use full paths:
```
/Users/kaze7539/homebrew/opt/ruby@3.1/bin/gem install jekyll bundler
```

reminder to self: don't use jekyll in the future!