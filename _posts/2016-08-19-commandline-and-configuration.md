---
layout:   post
title:    Command line and configuration
date:     2016-08-19 15:49:37
category: integration
tags:     [gsoc16]
---
To integrate my code with the *Cuckoo Sandbox* I've created a command line interface and a simple way to invoking the clustering with all the configuration stored in a single file: `conf/cuckooml.conf`.<!--more-->

To do clustering with default parameters it's enough to do:
{% highlight bash %}
python cuckoo.py --ml
{% endhighlight %}

You can also cluster from python interface with these two simple lines of code:
{% highlight Python %}
    from modules.cuckooml.cuckooml import init_cuckooml
    init_cuckooml()
{% endhighlight %}

These commands will produce `csv` files with all sort of statistics about clustering:

* clustering *results*,
* clustering *fit*,
* *label distribution* among clusters,
* samples that behave *abnormally*,
* *anomalies* among samples, and
* clustering of *test samples*.

A set of these files --- for CuckooML run with the default configuration on [this](https://gist.github.com/So-Cool/8ca88add639b41d33b13228f18be6baa) sample of malware reports --- can be found [here]({{ site.baseurl }}/files/cuckooml_output.zip).
