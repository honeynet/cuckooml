---
layout: default
title: CuckooML&#58; Machine Learning for Cuckoo Sandbox
---

# CuckooML&#58; Machine Learning for Cuckoo Sandbox #

## Introduction ##

CuckooML is a project that aims to deliver the possibility to find similarities between malware samples based on static and dynamic analysis features. By using anomaly detection techniques, such mechanism will be able to cluster and identify new types of malware and will constitute an invaluable tool for security researchers.  
Through the project, state of the art data science and machine learning approaches will be implemented and integrated into the Cuckoo Sandbox and will be made accessible as a command-line toolkit and as a web based interface.  
At first the project seems pretty straightforward: load the data and press classify button, i.e. run the data through some clustering algorithm in scikit-learn. (Un)fortunately it’s not that easy, the project holds a number of hidden pitfalls that can undermine its success. I’ll try to address most if not all of them in this proposal.

## Project Goals ##

### Datasets ###

Malware datasets tend to be relatively **large** and **spare**. They are mostly made of categorical and string data hence there is a strong need for feature forming techniques such as vectorisation [Back to the Future: Malware Detection with Temporally Consistent Labels; Miller B., et al.]. Moreover, as this field is a continuous arms race between malware and antivirus developers, dataset **drift** is more than possibility. Therefore, chosen clustering approach needs to be either easy to *re-train* or be able to *adapt* to the drift (with the latter option being more viable).

For such a big datasets the choice of clustering algorithm is critical as most of the algorithms require distance matrix hence their computational complexity becomes \\(O(n^2)\\) or sometimes even \\(O(n^3)\\). Moreover, the dynamic evaluation of new samples can be overwhelming given large number of submissions in short time.  
There are variety of approaches to address these issues. For instance, information about the model can be stored and updated only with the new samples to avoid re-training; or distance matrix can be stored therefore only new entries have to be append and distances for them computed (tradeoff between time and memory). Additionally, clustering algorithm can be initialised in a smart way and the algorithm can be parallelised (relatively easy with Python) to improve the overall performance.

### Features ###

To begin with, it is widely known that the classification - clustering in particular - can only be as good as the features that are used. To this end, representative features based on the malware analysis reports need to be engineered.  
Sometimes (see below) multiple set of features need to be created to solve variations - change of context - of the same problem. Moreover, to better capture this variation in the data it might be necessary to use large number of features therefore the clustering may suffer from overwhelming dimensionality. This could result in features being relatively **sparse** hence need for **dimensionality reduction** mechanisms to improve the process.  
If successfully completed, most of clustering algorithms should deliver good results.

### Clustering, Prototypes, and Anomaly Detection ###

The most popular clustering algorithms belong to **crisp** family: their output is restricted to class assignment. In presented scenario simple clustering might not be enough; it seems more natural to use **fuzzy** (*soft*) techniques which return probability of belonging to given class or cluster.  
This approach would also facilitate **calibration** of chosen clustering algorithm therefore achieving best possible result for given problem.  
Moreover, probabilities returned by fuzzy classifiers can be easily adapted for *anomaly detection* purposes by setting (calibrated) rejection threshold.  
**Rejection classification** could be another option: it is relatively easy to use with a classifier that returns probabilities and gives great results for detecting new classes in the data. Alternatively, **subgroup discovery** algorithm could be used to identify more complex structures in the data.  
Finally, deriving *prototypes* from such clustering is as simple as finding the most probable sample from each cluster (distribution).

An interesting approach that could be evaluated during development is semi-supervised learning: **active learning** in particular. With such approach small number of annotated samples could be used to transform purely *descriptive* model into somehow *predictive* one.  
**Constrain clustering** could also be beneficial: introducing some expert knowledge into the problem might sometimes yield significant improvements.

There are also couple of caveats associated with choosing appropriate clustering algorithm. First of all, the number of clusters pose a problem: either it needs to be fixed therefore clustering problem needs to be well defined; alternatively algorithm which detects number of clusters can be chosen nevertheless, this might not be as effective as the first approach. Furthermore, high dimensionality of feature space, calibration and overconfidence of chosen approach might pose some problems.  
Finally, clustering is *never right or wrong*: the results always depend on our interpretation.

### Heuristics (Context) ###

Data clustering is usually very subjective. There are many categories - heuristics - by which malware can be categorised e.g. stealing data / removing data / encrypting data / altering data. Many more categories can be named like posing similar threats, attacking similar files, attacking similar platforms, etc.  
It seems incredibly important to allow the user to choose the context of operation (or if possible define their own context) and then identify corresponding prototypes.  
Moreover it might be possible to use one classifier for all these contexts, hence, avoid costly retraining phase, by creating a *versatile* (reusable) model.

### Publication ###

Finally, I hope that during the development various discoveries and interesting artifacts can be found leading to material that can be formed into publishable scientific paper.

## Implementation ##

Some of the above ideas are prototyped in the Jupyter Notebook linked at the top of this proposal as a GitHub Gist.  
In general, the objective is to (re-)use already existing Python packages and libraries and any other relevant code. If necessary I am prepared to write customised clustering algorithm from scratch. In the later case it might also be worth to try and merge the (maybe more general) implementation into some machine learning package like *scikit-learn* or *scikit-fuzzy* or even create a custom Python package with the clustering algorithm; so to say two birds with one stone. I plan to keep the code fully documented, as universal as possible and maintain it through its lifetime.

---
CuckooML development is supported by the [Google Summer of Code 2016](https://summerofcode.withgoogle.com/) and mentored by [The Honeynet Project](https://www.honeynet.org/).

<script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
