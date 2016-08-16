---
layout: post
title:  "Binary feature extraction"
date:   2016-06-19 13:45:11
category: features
tags: [gsoc16]
---
In this post I will describe my fight with [Issue #5](https://github.com/honeynet/cuckooml/issues/5) aka feature extraction.<!--more-->

To start with we decided that the first set of features will be based on *Reviewer Integration and Performance Measurement for Malware Detection* by *B Miller et al* available [here](http://arxiv.org/abs/1510.07338).  
Most of those has been implemented and is pending testing and review. To see extracted information you can do the following:
{% highlight python%}
from modules.cuckooml.cuckooml import Instance
Instance()
a.load_json("path/to/a/cuckoo/report")
a.extract_features()

from pprint import pprint
pprint(a.features)
{% endhighlight %}
to print it.

Probably the next thing to do is for somebody to have a look at it and provide me some feedback (missing, misunderstood concepts form the paper), with the discussion taking place in `Issue 5` thread on GitHub.  
The problems I'm aware of are *Windows API calls* and *filesystem operations*. I could find overview of API calls in `behavior->apistats` but the paper mentions that the exact sequence can be extracted form the "raw Cuckoo sandbox output". Is it located in `strings` in the JSONs? Any ideas how to extract it?  
Moreover, I have troubles interpreting some of the file operations listed in the `behavior->summary`:

* `files_opened`,
* `files_exists`, and
* `files_failed`.

What do they mean?

---
The next step with feature construction is to apply techniques such as vectorisations and free-string formatting to make them usable by any ML clustering algorithm. Here the code developed alongside aforementioned paper comes handy. Especially `code/feature_extraction/feature_tools.py` file. As reinventing the wheal is not the best thing to do in software engineering I lean toward using some of functions already implemented therein. They won't be *copy-pasted*, they will only serve as an inspiration but the right question to ask is: is there a need to reference this code?

Additionally it seems natural to me to question the approach of feature vectorisation described in the paper. As many of the features are text based or categorical features from finite yet enormous set, *categorising* them cause number of dimensions to explode. Therefore, it seems worthwhile to think about alternative feature representations...
