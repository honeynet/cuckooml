---
layout: post
title:  "Automatic malware labelling"
date:   2016-06-06 22:58:56
categories: labelling
---

## Normalising variety of virus-total malware names ##
*Week 2* has been a lot of hard work to transform mediocre VT names normalisation implemented in `lib.cuckoo.common.virustotal` into something that can be used as a labeller necessary for later malware clustering.<!--more-->

For starters, I decided to introduce 5 different categories that need to be revised before proceeding to the next step of the project, namely choosing a strategy to pick a representative set of labels from all normalised VT predictions for given binary. These 5 categories are:

* Platform - an OS that the binary can harm;
* CVE (what's that?);
* Meta-type - one of **trojan** (*clicker, downloader, dropper, notifier, proxy, spyware, backdoor*) and **riskware** (these **types**: *adware, softwarebundler, hacktool, rogue* or any other not important enough threat like: grayware, hktl, keygen, onlinegames, scareware, startpage, suspicious, unwanted);
* Type - any of: *adware, behavior, browsermodifier, constructor, ddos, dialer, dos, exploit, hacktool, joke, misleading, monitoringtool, program, pws, ransom, remoteaccess, riskware, rogue, rootkit, settingsmodifier, softwarebundler, spammer, spoofer, tool, trojan, clicker, downloader, dropper, notifier, proxy, spyware, backdoor, virtool, virus, worm*;
* Family - all the remaining tokens which are not blacklisted.

## Normalisation results for some binaries ##
<h3>#20</h3>
<a href="{{ site.baseurl }}/img/labelling/201platform.png"><img src="{{ site.baseurl }}/img/labelling/201platform.png" alt="#20 platform" style="width: 470px; display: block;"/></a>
<a href="{{ site.baseurl }}/img/labelling/203metatype.png"><img src="{{ site.baseurl }}/img/labelling/203metatype.png" alt="#20 meta-type" style="width: 470px; display: block;"/></a>
<a href="{{ site.baseurl }}/img/labelling/204type.png"><img src="{{ site.baseurl }}/img/labelling/204type.png" alt="#20 type" style="width: 470px; display: block;"/></a>
<a href="{{ site.baseurl }}/img/labelling/205family.png"><img src="{{ site.baseurl }}/img/labelling/205family.png" alt="#20 family" style="width: 470px; display: block;"/></a>

<h3>#22</h3>
<a href="{{ site.baseurl }}/img/labelling/221platform.png"><img src="{{ site.baseurl }}/img/labelling/221platform.png" alt="#22 platform" style="width: 470px; display: block;"/></a>
<a href="{{ site.baseurl }}/img/labelling/223metatype.png"><img src="{{ site.baseurl }}/img/labelling/223metatype.png" alt="#22 meta-type" style="width: 470px; display: block;"/></a>
<a href="{{ site.baseurl }}/img/labelling/224type.png"><img src="{{ site.baseurl }}/img/labelling/224type.png" alt="#22 type" style="width: 470px; display: block;"/></a>
<a href="{{ site.baseurl }}/img/labelling/225family.png"><img src="{{ site.baseurl }}/img/labelling/225family.png" alt="#22 family" style="width: 470px; display: block;"/></a>

<p><h3>#97</h3>
<a href="{{ site.baseurl }}/img/labelling/971platform.png"><img src="{{ site.baseurl }}/img/labelling/971platform.png" alt="#97 platform" style="width: 470px; display: block;"/></a>
<a href="{{ site.baseurl }}/img/labelling/973metatype.png"><img src="{{ site.baseurl }}/img/labelling/973metatype.png" alt="#97 meta-type" style="width: 470px; display: block;"/></a>
<a href="{{ site.baseurl }}/img/labelling/974type.png"><img src="{{ site.baseurl }}/img/labelling/974type.png" alt="#97 type" style="width: 470px; display: block;"/></a>
<a href="{{ site.baseurl }}/img/labelling/975family.png"><img src="{{ site.baseurl }}/img/labelling/975family.png" alt="#97 family" style="width: 470px; display: block;"/></a>
</p>

<p><h3>#138</h3>
<a href="{{ site.baseurl }}/img/labelling/1381platform.png"><img src="{{ site.baseurl }}/img/labelling/1381platform.png" alt="#138 platform" style="width: 470px; display: block;"/></a>
<a href="{{ site.baseurl }}/img/labelling/1383metatype.png"><img src="{{ site.baseurl }}/img/labelling/1383metatype.png" alt="#138 meta-type" style="width: 470px; display: block;"/></a>
<a href="{{ site.baseurl }}/img/labelling/1384type.png"><img src="{{ site.baseurl }}/img/labelling/1384type.png" alt="#138 type" style="width: 470px; display: block;"/></a>
<a href="{{ site.baseurl }}/img/labelling/1385family.png"><img src="{{ site.baseurl }}/img/labelling/1385family.png" alt="#138 family" style="width: 470px; display: block;"/></a>
</p>

<p><h3>#149</h3>
<a href="{{ site.baseurl }}/img/labelling/1491platform.png"><img src="{{ site.baseurl }}/img/labelling/1491platform.png" alt="#149 platform" style="width: 470px; display: block;"/></a>
<a href="{{ site.baseurl }}/img/labelling/1492cve.png"><img src="{{ site.baseurl }}/img/labelling/1492cve.png" alt="#149 cve" style="width: 470px; display: block;"/></a>
<a href="{{ site.baseurl }}/img/labelling/1493metatype.png"><img src="{{ site.baseurl }}/img/labelling/1493metatype.png" alt="#149 meta-type" style="width: 470px; display: block;"/></a>
<a href="{{ site.baseurl }}/img/labelling/1494type.png"><img src="{{ site.baseurl }}/img/labelling/1494type.png" alt="#149 type" style="width: 470px; display: block;"/></a>
<a href="{{ site.baseurl }}/img/labelling/1495family.png"><img src="{{ site.baseurl }}/img/labelling/1495family.png" alt="#149 family" style="width: 470px; display: block;"/></a>
</p>

<p><h3>#154</h3>
<a href="{{ site.baseurl }}/img/labelling/1541platform.png"><img src="{{ site.baseurl }}/img/labelling/1541platform.png" alt="#154 platform" style="width: 470px; display: block;"/></a>
<a href="{{ site.baseurl }}/img/labelling/1543metatype.png"><img src="{{ site.baseurl }}/img/labelling/1543metatype.png" alt="#154 meta-type" style="width: 470px; display: block;"/></a>
<a href="{{ site.baseurl }}/img/labelling/1544type.png"><img src="{{ site.baseurl }}/img/labelling/1544type.png" alt="#154 type" style="width: 470px; display: block;"/></a>
<a href="{{ site.baseurl }}/img/labelling/1545family.png"><img src="{{ site.baseurl }}/img/labelling/1545family.png" alt="#154 family" style="width: 470px; display: block;"/></a>
</p>

<p><h3>#172</h3>
<a href="{{ site.baseurl }}/img/labelling/1721platform.png"><img src="{{ site.baseurl }}/img/labelling/1721platform.png" alt="#172 platform" style="width: 470px; display: block;"/></a>
<a href="{{ site.baseurl }}/img/labelling/1723metatype.png"><img src="{{ site.baseurl }}/img/labelling/1723metatype.png" alt="#172 meta-type" style="width: 470px; display: block;"/></a>
<a href="{{ site.baseurl }}/img/labelling/1724type.png"><img src="{{ site.baseurl }}/img/labelling/1724type.png" alt="#172 type" style="width: 470px; display: block;"/></a>
<a href="{{ site.baseurl }}/img/labelling/1725family.png"><img src="{{ site.baseurl }}/img/labelling/1725family.png" alt="#172 family" style="width: 470px; display: block;"/></a>
</p>

<p><h3>#192</h3>
<a href="{{ site.baseurl }}/img/labelling/1921platform.png"><img src="{{ site.baseurl }}/img/labelling/1921platform.png" alt="#192 platform" style="width: 470px; display: block;"/></a>
<a href="{{ site.baseurl }}/img/labelling/1923metatype.png"><img src="{{ site.baseurl }}/img/labelling/1923metatype.png" alt="#192 meta-type" style="width: 470px; display: block;"/></a>
<a href="{{ site.baseurl }}/img/labelling/1924type.png"><img src="{{ site.baseurl }}/img/labelling/1924type.png" alt="#192 type" style="width: 470px; display: block;"/></a>
<a href="{{ site.baseurl }}/img/labelling/1925family.png"><img src="{{ site.baseurl }}/img/labelling/1925family.png" alt="#192 family" style="width: 470px; display: block;"/></a>
</p>
