  <a name=top><p>&nbsp;<hr>
  <p align=center>
  &nbsp;<a href="/README.md#top">home</a> &nbsp; | &nbsp;
  <a href="/docs/syllabus.md#top">syllabus</a> &nbsp; | &nbsp;
  <a href="https://docs.google.com/spreadsheets/d/1KuW-SH46KmFW0grEX2wT01jicUSew_5sr1QdGuSrweU/edit#gid=0">groups</a> &nbsp; | &nbsp;
  <a href="https://moodle-courses2223.wolfware.ncsu.edu/course/view.php?id=1771">moodle</a> &nbsp; | &nbsp;
  <a href="https://ncsu.hosted.panopto.com/Panopto/Pages/Sessions/List.aspx#folderID=%22389b8ebf-2f29-4c15-8231-aee9000e3f05%22">video</a> &nbsp; | &nbsp;
  <a href="/docs/review.md">review</a> &nbsp; | &nbsp;
  <a href="/LICENSE.md#top">&copy; 2022</a></p>
  <hr>
  <p align=center><a href="/README.md#top"><img  width=700 src="/etc/img/banner.png"></a></p>

# AI ❤️ SE

## What is AI?

* Machine intelligence
* Our focus: machine learning, and specifically, data-driven algorithms.
* In particular, we will focus on *applied* ML.
* We will use the term "AI" to refer to machine learning algorithms.
  
# AI4SE: The different perspectives

## The AI perspective

* Most SE tasks can be formulated as an **optimization problem**. 
* We can then use optimization theory in AI to solve the problem.
* There are several papers that do this:
  * Project management [[1-3]](#references)
  * Design [[4]](#references)
  * Security [[5]](#references)
  * Software quality [[6-8]](#references)

Example: for automated microservice partitioning [[9]](#references)

<img src="/etc/img/eq.png">

* Optimization can be black-box (e.g., using a neural network) or white-box (e.g., using a linear programming solver); for state-of-the-art results, the former is more popular.

## The SE perspective

* SE problems are first-class citizens.
* We can use AI to solve them, but we're more interested in the **underlying problem** and **pragmatics**.
* Closer to the [Working Backwards approach](https://www.productplan.com/glossary/working-backward-amazon-method/).

In either case, the knowledge assumptions are different. When looking through the AI perspective, optimization, designing loss functions, and the theoretical results are "obvious". When looking through the SE perspective, the underlying problem is "obvious", and the theoretical results are less important.

# What can AI do for SE?

Once framed as an optimization problem, nearly *anything*. See:

* Recognizing actionable static code warnings [[10]](#references)
* Self-admitted technical debt detection [[11]](#references)
* Human-in-the-loop optimization [[12]](#references)
* Automated microservice partitioning [[9, 13]](#references)
* Assisting developers in writing code [[14]](#references)
* Defect prediction [[15]](#references)

## A quick walkthrough: AI for SE

* Our case study: defect prediction
* Our bias: we will use the AI lens to look at the problem.

### Step 1: Obtain data

* Use the PROMISE repository (from 2005!) [[16]](#references)
* This is *tabular* data, containing 21 attributes--lines of code, number of public methods, depth of inheritance tree, etc.

### Step 2: Use a deep learner

* Why? Some preliminary results with classical learners did poorly.
* Obviously, we need to use hyper-parameter optimization (why? because hyper-parameters affect the number of piecewise linear regions of the decision boundary; see [[17]](#references)).
  * **Brownie points:** derive a greedy approach to find the optimal theoretical architecture based on Theorem 5 of this paper, given the number of linear regions required to separate the data. (And if you can find a way to compute the number of linear regions needed, you're strongly encouraged to join the lab!)
* And by the way, we need to oversample, since we have imbalanced data; the trivial way to do this is to use a weighted loss function.

<img src="/etc/img/weighted.png">

(Credits: I am the author of the paper this figure is from, and I permit myself to use it.)

* In fact, oversampling is as good as any other method to deal with imbalanced data, at least for convolutional networks [[18]](#references)--but there's no reason it shouldn't work for feedforward networks, right?.
* Weighted losses are also computationally efficient (why?).

### Step 3: Define a preprocessing operator

* The above didn't work well at all, so we need a new hypothesis.
* This hypothesis is that the decision boundary gets too close to data samples, and therefore we may have samples that are accidentally on the other side (motivation: SVMs)

<img src="/etc/img/svm.webp">

(Credits: [[19]](#references))

<img src="/etc/img/wfo.png">

* Note here the difference between this method of pushing data samples away vs. the SVM way: the SVM uses a convex optimization problem to find the optimal decision boundary, while this method uses a computational method of doing so. This makes the SVM more efficient, but you may need a softer margin to get the same results.

### Step 4: Iterate on the solution

* We can apply fuzzy sampling to the majority class as well.
* Fuzzy sampling creates the opposite class imbalance problem (ironically, the same problem we had before), but we can use SMOTE to solve it.
  * **Brownie points:** How many times can you apply fuzzy sampling (and then end it with SMOTE) before you get worse results? Can you explain why too many rounds of fuzzy sampling is bad, aside from the computational cost?
  * **Brownie points:** Can you find an issue with this approach? Hint: something here is unnecessary.

Congrats--you are now the SOTA for defect prediction! Until the next guy comes along, that is.

### Lessons learned

* We were very AI-centric about our approach--the actual data itself, or its source never impacted our decisions.
* We did need to come up with a novel preprocessing operator, perhaps because we failed to include domain knowledge.
* Although we used a feature set from 2005, we beat state-of-the-art approaches that used language models to mine features. 

## But why is AI4SE not more widespread?

* The AI community is not very interested in SE problems.
  * This point was generated by Codex, but I ask you: how wrong is it?
* The SE community is not very interested in AI.
  * This point was also generated by Codex, but at ICSE 2022, *all* our papers were rejected, partly for this reason. I'd rewrite this point as: there is some resistance within the SE community to AI--and the politics of academia are out of scope of this class.
  * Note: we do not talk about ICSE '22.
* Researchers are notoriously bad at writing production-grade code, or documentation. Moreover, companies also expect additional things such as community support and a license permitting commercial use without needing to open-source the product itself.


# But what about SE4AI?

* It exists, and it's called **MLOps**.
* We cannot possibly cover everything in this class, but we refer you to [Full-Stack Deep Learning](https://fullstackdeeplearning.com/course/2022/).

## Why?

* Experimenting with models on datasets creates many artifacts.
* You may also want to use an older idea from your tinkering to try new things.
* This creates a need for a way to track and manage these artifacts.
* Most MLOps frameworks today will offer the following features:
  * Experiment tracking
  * Model versioning
  * Model deployment
  * Visualization
  * Reproducing experiments

## How?

There are many contenders in this field, but the most popular ones are:
* MLFlow
* Weights & Biases
* DVC
* Comet
* ClearML

## Todo

* [ ] Add a demo of MLOps
* [ ] Add a section on the fairness in AI4SE

# X vs Y

* Deep learning vs. classical machine learning
* AI4SE vs SE4AI
* Manual tracking vs MLOps


# References

[1] Kumar, K. Vinay, et al. "Software development cost estimation using wavelet neural networks." Journal of Systems and Software 81.11 (2008): 1853-1867.
[2] Minku, Leandro L., and Xin Yao. "Software effort estimation as a multiobjective learning problem." ACM Transactions on Software Engineering and Methodology (TOSEM) 22.4 (2013): 1-32.
[3] Sarro, Federica, Alessio Petrozziello, and Mark Harman. "Multi-objective software effort estimation." 2016 IEEE/ACM 38th International Conference on Software Engineering (ICSE). IEEE, 2016.
[4] Du, Xin, et al. "An evolutionary algorithm for performance optimization at software architecture level." 2015 IEEE Congress on Evolutionary Computation (CEC). IEEE, 2015.
[5] Sadiq, Ali Safaa, et al. "An efficient ids using hybrid magnetic swarm optimization in wanets." IEEE Access 6 (2018): 29041-29053.
[6] De Carvalho, Andre B., Aurora Pozo, and Silvia Regina Vergilio. "A symbolic fault-prediction model based on multiobjective particle swarm optimization." Journal of Systems and Software 83.5 (2010): 868-882.
[7] Liu, Yi, Taghi M. Khoshgoftaar, and Naeem Seliya. "Evolutionary optimization of software quality modeling with multiple repositories." IEEE Transactions on Software Engineering 36.6 (2010): 852-864.
[8] Abdessalem, Raja Ben, et al. "Testing vision-based control systems using learnable evolutionary algorithms." 2018 IEEE/ACM 40th International Conference on Software Engineering (ICSE). IEEE, 2018.
[9] Desai, Utkarsh, Sambaran Bandyopadhyay, and Srikanth Tamilselvam. "Graph neural network to dilute outliers for refactoring monolith application." Proceedings of the AAAI Conference on Artificial Intelligence. Vol. 35. No. 1. 2021.
[10] Yedida, Rahul, et al. "How to Find Actionable Static Analysis Warnings." arXiv preprint arXiv:2205.10504 (2022).
[11] Tu, Huy, and Tim Menzies. "DebtFree: minimizing labeling cost in self-admitted technical debt identification using semi-supervised learning." Empirical Software Engineering 27.4 (2022): 1-37.
[12] Lustosa, Andre, et al. "SNEAK: Faster Interactive Search-based SE." arXiv preprint arXiv:2110.02922 (2021).
[13] Yedida, Rahul, et al. "An Expert System for Redesigning Software for Cloud Applications." arXiv preprint arXiv:2109.14569 (2021).
[14] Chen, Mark, et al. "Evaluating large language models trained on code." arXiv preprint arXiv:2107.03374 (2021).
[15] Yedida, Rahul, and Tim Menzies. "On the value of oversampling for deep learning in software defect prediction." IEEE Transactions on Software Engineering (2021).
[16] Shirabad, J. Sayyad, and Tim J. Menzies. "The PROMISE repository of software engineering databases." School of Information Technology and Engineering, University of Ottawa, Canada 24 (2005): 3.
[17] Montufar, Guido F., et al. "On the number of linear regions of deep neural networks." Advances in neural information processing systems 27 (2014).
[18] Buda, Mateusz, Atsuto Maki, and Maciej A. Mazurowski. "A systematic study of the class imbalance problem in convolutional neural networks." Neural networks 106 (2018): 249-259.
[19] <a href="https://commons.wikimedia.org/wiki/File:SVM_margin.png">Larhmam</a>, <a href="https://creativecommons.org/licenses/by-sa/4.0">CC BY-SA 4.0</a>, via Wikimedia Commons