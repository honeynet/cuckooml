---
layout: post
title:  Abnormal behaviour detection
date:   2016-07-13 13:46:53
category: functionality
tags: [gsoc16]
---

I was suggested to develop a mechanism to detect binaries that behave abnormally. To this end, I used *count* features that count numerous operations performed by the binaries like number of files written, number of network connections, etc. As a method for the outlier detection I used classic *boxplots*.<!--more-->

## Results ##
Below you can find anomaly detection results and boxplot visualisation. The numbers are file names i.e. sample IDs.

------------------------------------------------------------
:count:dimp  
Outliers:  
Suspected outliers:  

------------------------------------------------------------
:count:dns  
Outliers:  105, 131, 146, 154, 170, 189, 192, 26, 27, 29, 43, 62, 75, 93, 95  
Suspected outliers:  117, 14, 151, 18, 46, 5  

------------------------------------------------------------
:count:file:all  
Outliers:  105, 106, 109, 128, 137, 144, 146, 147, 152, 153, 157, 158, 163, 170, 173, 18, 192, 195, 20, 24, 27, 32, 48, 55, 57, 60, 70, 75, 78, 93, 94  
Suspected outliers:  187, 40, 65  

------------------------------------------------------------
:count:file:copied  
Outliers:  
Suspected outliers:  49, 69  

------------------------------------------------------------
:count:file:deleted  
Outliers:  152, 18, 78  
Suspected outliers:  116, 125, 132, 133, 143, 166, 59, 85, 96  

------------------------------------------------------------
:count:file:exists  
Outliers:  105, 106, 109, 128, 137, 144, 146, 147, 153, 157, 158, 163, 170, 187, 192, 195, 20, 24, 27, 32, 40, 55, 60, 65, 75, 93, 94  
Suspected outliers:  121, 135, 141, 19, 49, 56, 64, 84, 9  

------------------------------------------------------------
:count:file:failed  
Outliers:  173, 18, 48, 57, 70  
Suspected outliers:  20, 60  

------------------------------------------------------------
:count:file:opened  
Outliers:  105, 106, 109, 128, 137, 144, 146, 147, 152, 153, 157, 158, 163, 170, 173, 18, 192, 195, 20, 24, 27, 32, 48, 55, 57, 60, 70, 75, 78, 93, 94  
Suspected outliers:  

------------------------------------------------------------
:count:file:read  
Outliers:  105, 146, 152, 170, 173, 192, 20, 27, 48, 57, 60, 70, 75, 78, 93  
Suspected outliers:  

------------------------------------------------------------
:count:file:renamed  
Outliers:  105, 115, 130, 138, 139, 140, 146, 148, 162, 165, 168, 169, 170, 187, 191, 192, 194, 196, 2, 20, 27, 38, 42, 60, 65, 75, 79, 89, 90, 93  
Suspected outliers:  

------------------------------------------------------------
:count:file:written  
Outliers:  105, 146, 152, 153, 170, 18, 192, 20, 27, 60, 75, 78, 93  
Suspected outliers:  106, 109, 128, 137, 144, 147, 157, 158, 163, 187, 195, 24, 32, 40, 49, 55, 65, 9, 94  

------------------------------------------------------------
:count:http  
Outliers:  10, 105, 11, 110, 117, 118, 127, 131, 135, 141, 145, 146, 151, 154, 155, 160, 161, 168, 170, 174, 175, 176, 179, 18, 185, 190, 192, 20, 26, 27, 29, 36, 43, 47, 5, 51, 54, 60, 62, 68, 75, 9, 93, 95  
Suspected outliers:  

------------------------------------------------------------
:count:lang  
Outliers:  
Suspected outliers:  

------------------------------------------------------------
:count:mutex  
Outliers:  
Suspected outliers:  18  

------------------------------------------------------------
:count:proc  
Outliers:  
Suspected outliers:  105, 146, 170, 27, 75, 93  

------------------------------------------------------------
:count:reg:del  
Outliers:  105, 106, 109, 121, 128, 13, 135, 137, 141, 142, 144, 146, 147, 149, 152, 153, 157, 158, 163, 170, 171, 175, 179, 187, 19, 195, 24, 27, 32, 40, 49, 55, 56, 64, 65, 75, 84, 9, 93, 94  
Suspected outliers:  192  

------------------------------------------------------------
:count:reg:write  
Outliers:  105, 106, 109, 121, 128, 13, 135, 137, 141, 142, 144, 146, 147, 149, 153, 157, 158, 163, 170, 171, 175, 179, 187, 19, 195, 24, 27, 32, 40, 49, 55, 56, 64, 65, 75, 84, 9, 93, 94  
Suspected outliers:  152, 174, 192  

------------------------------------------------------------
:count:simp  
Outliers:  
Suspected outliers:  198  

------------------------------------------------------------
:count:tcp  
Outliers:  105, 146, 170, 192, 20, 27, 43, 60, 62, 75, 93  
Suspected outliers:  18, 26, 29  

------------------------------------------------------------
:count:udp  
Outliers:  
Suspected outliers:  

------------------------------------------------------------
:count:wapi  
Outliers:  
Suspected outliers:  

------------------------------------------------------------
:meta:size  
Outliers:  
Suspected outliers:  

------------------------------------------------------------
:simp:count  
Outliers:  198  
Suspected outliers:  

------------------------------------------------------------

Box plots for these results are presented below.

<h4>:count:dimp</h4>
<a href="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_dimp.png"><img src="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_dimp.png" alt="count:dimp" style="width: 470px; display: block;"/></a>

<h4>:count:dns</h4>
<a href="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_dns.png"><img src="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_dns.png" alt="count:dns" style="width: 470px; display: block;"/></a>

<h4>:count:file:all</h4>
<a href="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_file_all.png"><img src="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_file_all.png" alt=":count:file:all" style="width: 470px; display: block;"/></a>

<h4>:count:file:copied</h4>
<a href="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_file_copied.png"><img src="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_file_copied.png" alt=":count:file:copied" style="width: 470px; display: block;"/></a>

<h4>:count:file:deleted</h4>
<a href="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_file_deleted.png"><img src="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_file_deleted.png" alt=":count:file:deleted" style="width: 470px; display: block;"/></a>

<h4>:count:file:exists</h4>
<a href="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_file_exists.png"><img src="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_file_exists.png" alt=":count:file:exists" style="width: 470px; display: block;"/></a>

<h4>:count:file:failed</h4>
<a href="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_file_failed.png"><img src="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_file_failed.png" alt=":count:file:failed" style="width: 470px; display: block;"/></a>

<h4>:count:file:opened</h4>
<a href="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_file_opened.png"><img src="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_file_opened.png" alt=":count:file:opened" style="width: 470px; display: block;"/></a>

<h4>:count:file:read</h4>
<a href="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_file_read.png"><img src="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_file_read.png" alt=":count:file:read" style="width: 470px; display: block;"/></a>

<h4>:count:file:renamed</h4>
<a href="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_file_renamed.png"><img src="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_file_renamed.png" alt=":count:file:renamed" style="width: 470px; display: block;"/></a>

<h4>:count:file:written</h4>
<a href="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_file_written.png"><img src="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_file_written.png" alt=":count:file:written" style="width: 470px; display: block;"/></a>

<h4>:count:http</h4>
<a href="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_http.png"><img src="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_http.png" alt=":count:http" style="width: 470px; display: block;"/></a>

<h4>:count:lang</h4>
<a href="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_lang.png"><img src="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_lang.png" alt=":count:lang" style="width: 470px; display: block;"/></a>

<h4>:count:mutex</h4>
<a href="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_mutex.png"><img src="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_mutex.png" alt=":count:mutex" style="width: 470px; display: block;"/></a>

<h4>:count:proc</h4>
<a href="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_proc.png"><img src="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_proc.png" alt=":count:proc" style="width: 470px; display: block;"/></a>

<h4>:count:reg:del</h4>
<a href="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_reg_del.png"><img src="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_reg_del.png" alt=":count:reg:del" style="width: 470px; display: block;"/></a>

<h4>:count:reg:write</h4>
<a href="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_reg_write.png"><img src="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_reg_write.png" alt=":count:reg:write" style="width: 470px; display: block;"/></a>

<h4>:count:simp</h4>
<a href="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_simp.png"><img src="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_simp.png" alt=":count:simp" style="width: 470px; display: block;"/></a>

<h4>:count:tcp</h4>
<a href="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_tcp.png"><img src="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_tcp.png" alt=":count:tcp" style="width: 470px; display: block;"/></a>

<h4>:count:udp</h4>
<a href="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_udp.png"><img src="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_udp.png" alt=":count:udp" style="width: 470px; display: block;"/></a>

<h4>:count:wapi</h4>
<a href="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_wapi.png"><img src="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__count_wapi.png" alt=":count:wapi" style="width: 470px; display: block;"/></a>

<h4>:meta:size</h4>
<a href="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__meta_size.png"><img src="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__meta_size.png" alt=":meta:size" style="width: 470px; display: block;"/></a>

<h4>:simp:count</h4>
<a href="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__simp_count.png"><img src="{{ site.baseurl }}/img/abnormal_behaviour/abnormal_behaviour__simp_count.png" alt=":simp:count" style="width: 470px; display: block;"/></a>
