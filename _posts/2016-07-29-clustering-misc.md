---
layout: post
title:  Clustering misc
date:   2016-07-29 17:22:47
category: clustering
tags: [gsoc16]
---

I spent the last couple of days to implement miscellaneous functions helping with clustering. Among others: saving clustering results into JSON, label statistics per cluster, comparing a new sample to in-memory clustering and basic version of anomaly detection.<!--more-->  
Moreover, I've started developing a Jupyter Notebook to showcase all the implemented code during GSoC'16.

### Clustering statistics ###
It seems worth discovering per cluster structure. The easiest way is to produce a bar plot that counts ground truth (VirusTotal) labels per discovered cluster.  
To get this kind of plots 
A snipped to produce results of clustering for variety of parameters settings.

{% highlight python%}
from cuckooml import Loader
from cuckooml import ML

loader = Loader()
loader.load_binaries("../../sample_data/dict")

ml = ML()
ml.load_simple_features(loader.get_simple_features())
ml.load_features(loader.get_features())
ml.load_labels(loader.get_labels())
ml.cluster_hdbscan(ml.features, 1, 6)

# assess clustering fit (various metrics - see previous post)
ml.assess_clustering(ml.clustering["hdbscan"]["clustering"], ml.labels, ml.features)

# get label statistics per cluster
ml.clustering_label_distribution(ml.clustering["hdbscan"]["clustering"], ml.labels, True)
{% endhighlight %}

See the plots below for the visualisations.
<h4>-1 cluster statistics</h4>
<a href="{{ site.baseurl }}/img/hdbscan_cluster_structure/cluster_-1.png"><img src="{{ site.baseurl }}/img/hdbscan_cluster_structure/cluster_-1.png" alt="-1 cluster" style="width: 470px; display: block;"/></a>
<h4>0 cluster statistics</h4>
<a href="{{ site.baseurl }}/img/hdbscan_cluster_structure/cluster_0.png"><img src="{{ site.baseurl }}/img/hdbscan_cluster_structure/cluster_0.png" alt="0 cluster" style="width: 470px; display: block;"/></a>
<h4>1 cluster statistics</h4>
<a href="{{ site.baseurl }}/img/hdbscan_cluster_structure/cluster_1.png"><img src="{{ site.baseurl }}/img/hdbscan_cluster_structure/cluster_1.png" alt="1 cluster" style="width: 470px; display: block;"/></a>
<h4>2 cluster statistics</h4>
<a href="{{ site.baseurl }}/img/hdbscan_cluster_structure/cluster_2.png"><img src="{{ site.baseurl }}/img/hdbscan_cluster_structure/cluster_2.png" alt="2 cluster" style="width: 470px; display: block;"/></a>
<h4>3 cluster statistics</h4>
<a href="{{ site.baseurl }}/img/hdbscan_cluster_structure/cluster_3.png"><img src="{{ site.baseurl }}/img/hdbscan_cluster_structure/cluster_3.png" alt="3 cluster" style="width: 470px; display: block;"/></a>
<h4>4 cluster statistics</h4>
<a href="{{ site.baseurl }}/img/hdbscan_cluster_structure/cluster_4.png"><img src="{{ site.baseurl }}/img/hdbscan_cluster_structure/cluster_4.png" alt="4 cluster" style="width: 470px; display: block;"/></a>
<h4>5 cluster statistics</h4>
<a href="{{ site.baseurl }}/img/hdbscan_cluster_structure/cluster_5.png"><img src="{{ site.baseurl }}/img/hdbscan_cluster_structure/cluster_5.png" alt="5 cluster" style="width: 470px; display: block;"/></a>
<h4>6 cluster statistics</h4>
<a href="{{ site.baseurl }}/img/hdbscan_cluster_structure/cluster_6.png"><img src="{{ site.baseurl }}/img/hdbscan_cluster_structure/cluster_6.png" alt="6 cluster" style="width: 470px; display: block;"/></a>
<h4>7 cluster statistics</h4>
<a href="{{ site.baseurl }}/img/hdbscan_cluster_structure/cluster_7.png"><img src="{{ site.baseurl }}/img/hdbscan_cluster_structure/cluster_7.png" alt="7 cluster" style="width: 470px; display: block;"/></a>
<h4>8 cluster statistics</h4>
<a href="{{ site.baseurl }}/img/hdbscan_cluster_structure/cluster_8.png"><img src="{{ site.baseurl }}/img/hdbscan_cluster_structure/cluster_8.png" alt="8 cluster" style="width: 470px; display: block;"/></a>
<h4>9 cluster statistics</h4>
<a href="{{ site.baseurl }}/img/hdbscan_cluster_structure/cluster_9.png"><img src="{{ site.baseurl }}/img/hdbscan_cluster_structure/cluster_9.png" alt="9 cluster" style="width: 470px; display: block;"/></a>
<h4>10 cluster statistics</h4>
<a href="{{ site.baseurl }}/img/hdbscan_cluster_structure/cluster_10.png"><img src="{{ site.baseurl }}/img/hdbscan_cluster_structure/cluster_10.png" alt="10 cluster" style="width: 470px; display: block;"/></a>
<h4>11 cluster statistics</h4>
<a href="{{ site.baseurl }}/img/hdbscan_cluster_structure/cluster_11.png"><img src="{{ site.baseurl }}/img/hdbscan_cluster_structure/cluster_11.png" alt="11 cluster" style="width: 470px; display: block;"/></a>

### Updating JSONs ###
To update the JSONs with clustering results use the following code:
{% highlight python%}
from cuckooml import Loader
from cuckooml import ML

loader = Loader()
loader.load_binaries("../../sample_data/dict")

ml = ML()
ml.load_simple_features(loader.get_simple_features())
ml.load_features(loader.get_features())
ml.load_labels(loader.get_labels())

# perform clustering and save the results in-memory
ml.cluster_hdbscan(ml.features, 1, 6)

ml.save_clustering_results(loader, "../../sample_data/dict_cluster")
{% endhighlight %}

### Compare a new sample to already fitted data
To compare a new sample to alredy existing clustering you can use the code snipped given below. It will return *cluster ID*, *cluster membership* probability, and *outlier score*.

{% highlight python%}
from cuckooml import Instance
from cuckooml import Loader
from cuckooml import ML

loader = Loader()
loader.load_binaries("../../sample_data/dict")

ml = ML()
ml.load_simple_features(loader.get_simple_features())
ml.load_features(loader.get_features())
ml.load_labels(loader.get_labels())
ml.cluster_hdbscan(ml.features)

# get a new sample
new_sample = Instance()
# get a new sample and save it in-memory as *5_new*
new_sample.load_json("../../sample_data/dict/5", "5_new")
new_sample.label_sample()
new_sample.extract_features()
new_sample.extract_basic_features()

# compare the new sample
ml.compare_sample(new_sample)
{% endhighlight %}
 
### Anomaly detection
Anomaly detection for new malware - especially in clustering scenario - is a complicated task. The first attempt (and implementation) returns anomalies considered in variety of aspects.  
At the moment these are: *outliers* detected by HDBSCAN algorithm, samples with high *outlier score*, elements from clusters that are not *homogeneous*, and per cluster samples with low probability of belonging to that cluster.

{% highlight python%}
from cuckooml import Loader
from cuckooml import ML

loader = Loader()
loader.load_binaries("../../sample_data/dict")

ml = ML()
ml.load_simple_features(loader.get_simple_features())
ml.load_features(loader.get_features())
ml.load_labels(loader.get_labels())
ml.cluster_hdbscan(ml.features)

ml.anomaly_detection()
{% endhighlight %}

### `cuckooml` showcase (Jupyter Notebook)
Finally, I decided to pull together all of the code snippets placed on the blog so far into one Jupyter Notebook. I think that this will be a great way to showcase `cuckooml` capabilities. Additionally, it is incredibly easy way to introduce new users and potential contributors to the project. I'll publish a new post dedicated to this topic anytime soon.
