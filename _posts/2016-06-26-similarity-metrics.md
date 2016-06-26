---
layout: post
title:  "Binaries similarity metrics"
date:   2016-06-26 11:27:24
categories: features
---
Working with features extraction last week ade me think more about possible *similarity metrics* and *heuristics* in malware clustering. The two simple concepts are **feature scoping** and **feature grouping**.<!--more-->

## Feature scoping ##
Some features exhibit implicit hierarchy which is very often overlooked. Let's take filesystem operations as an example:

```
filesystem operations
|----files touched
|----|----files read
|----|----|----files opened
|----|----|----files copied
|----|----|----files moved
|----|----files written
|----|----|----files copied
|----|----|----files moved
|----|----|----files created
|----|----files deleted
|----|----|----files moved
|----|----|----files removed
```
By implementing hierarchy aware features user could choose a detail of clustering per feature family.

## Feature grouping ##
Another approach to *similarity metric* for malware can be grouping certain features together and using only those for clustering. For instance if one wants to compare only the networking behaviour of a set of binaries the possibility to select relevant features for clustering (and not the whole feature set available) may be important.  
There's no easy way to tell this without experiments so we will see what happens.

---
Finally I couldn't help to notice `signatures` field in the JSONs. It might be a good source of high level threat description for the planned Cuckooml interface or even as a very simple set of features. Example entry in `signatures` list is:

```
{u'description': u'One or more potentially interesting buffers were extracted, these generally contain injected code, configuration data, etc.',
  u'families': [],
  u'marks': [],
  u'name': u'dumped_buffer',
  u'references': [],
  u'severity': 2}
```
Is it worth making a simplistic set of features for very basic clustering? Where are those entries created in the cuckoo code? Any comments on my comments?
