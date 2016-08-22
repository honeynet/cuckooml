---
layout: post
title:  GSoC16 summary
date:   2016-08-21 16:29:38
category: cuckooml
tags: [gsoc16]
---

The time has come to say goodbye to *Google Summer of Code 2016*. It was a great summer and a lot of experience gained while working for [The Honeynet Project](https://www.honeynet.org/) and [Cuckoo Sandbox](https://www.cuckoosandbox.org/) in particular.<!--more-->

All the code created during GSoC16 can be found [here](https://github.com/honeynet/cuckooml/commits/master?author=so-cool) as a list of GitHub commits.  
Additionally, [this blog](https://honeynet.github.io/cuckooml) has accompanied the project so far, with all the blog posts created during GSoC:
<ls>
  {% for p in site.tags.gsoc16 %}
      <li><a href="{{ p.url | prepend: site.baseurl }}">{{ p.title }}</a></li>
  {% endfor %}
</ls>
<br>

Finally, to showcase the `cuckooml` possibilities and features I've created a *Jupyter Notebook*. It's read-only version is available at [GitHub](https://render.githubusercontent.com/view/ipynb?commit=482f1411e3686bffbb071c2073a5b5306620c1e3&enc_url=68747470733a2f2f7261772e67697468756275736572636f6e74656e742e636f6d2f686f6e65796e65742f6375636b6f6f6d6c2f343832663134313165333638366266666262303731633230373361356235333036363230633165332f6578616d706c65732f6375636b6f6f6d6c2e6970796e62&nwo=honeynet%2Fcuckooml&path=examples%2Fcuckooml.ipynb&repository_id=56984886#cuckooml).

<blockquote style="width: 410px; overflow: hidden; border: 1px solid #002a35; background: #002a35; color: #000000;">
    <span style="display: block; width: 100%; margin-bottom: 5px; font-weight: bold; font-size: 13px; text-shadow: 0px 1px 0px #00c8e8; padding: 6px 11px; background: #4CB697; border-top: 1px solid #00c8e8; border-bottom: 1px solid #00c8e8;">
        Sir Winston Churchill, Speech in November 1942
        </span>
        <p style="line-height: 19px; margin-bottom: 10px; font-style: italic; padding-left: 15px; background: #002a35; color: #2AA198;">
            Now this is not the end. It is not even the beginning of the end. But it is, perhaps, the end of the beginning.
        </p>
</blockquote>
