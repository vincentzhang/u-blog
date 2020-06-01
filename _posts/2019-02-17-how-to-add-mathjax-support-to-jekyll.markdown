---
layout: post
title:  "How to add mathjax support to jekyll"
date:   2019-02-17
categories: coding setup
usemathjax: true
---

I came across this excellent [tutorial][1] when I tried to add mathjax support to my jekyll site. 

Here's a brief summary:

* In the `_config.yml`, add the following lines:
```
    # Build settings
    markdown: kramdown
```

* On the top of the posts that you'd like to add mathjax support (it's called the YAML ''front matter'')
, add the following line:
```
    usemathjax: true
```

* Add these lines to `_includes/head.html`:
  ```
    {% raw %}
      <!-- for mathjax support -->
      {% if page.usemathjax %}
        <script type="text/x-mathjax-config">
          MathJax.Hub.Config({
          TeX: { equationNumbers: { autoNumber: "AMS" } }
          });
        </script>
        <script type="text/javascript" async src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
      {% endif %}
    {% endraw %}
  ```
  <!-- <script type="text/javascript" async src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML"> </script> -->


* After that, simply wrap the math symbols with two double-dollar sign `$$`:
```
  $$E=mc^2$$
``` 
  You should be able to see it in your post as: 
  $$E=mc^2$$

## Reference:

\[1\]: https://alan97.github.io/random/mathjax/

[1]: https://alan97.github.io/random/mathjax/
