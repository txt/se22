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

Example: for automated microservice partitioning [[1]](#references)

<img src="/etc/img/eq.png">

* Optimization can be black-box (e.g., using a neural network) or white-box (e.g., using a linear programming solver); for state-of-the-art results, the former is more popular.

## The SE perspective

* SE problems are first-class citizens.
* We can use AI to solve them, but we're more interested in the **underlying problem** and **pragmatics**.
* Closer to the [Working Backwards approach](https://www.productplan.com/glossary/working-backward-amazon-method/).

In either case, the knowledge assumptions are different. When looking through the AI perspective, optimization, designing loss functions, and the theoretical results are "obvious". When looking through the SE perspective, the underlying problem is "obvious", and the theoretical results are less important.

# What can AI do for SE?

Once framed as an optimization problem, nearly *anything*. See:

* Recognizing actionable static code warnings [[2]](#references)
* Self-admitted technical debt detection [[3]](#references)
* Human-in-the-loop optimization [[4]](#references)
* Automated microservice partitioning [[1, 5]](#references)
* Assisting developers in writing code [[6]](#references)
* Defect prediction [[7]](#references)

## A quick walkthrough: AI for SE

* Our case study: defect prediction
* Our bias: we will use the AI lens to look at the problem.

### Step 1: Obtain data

* Use the PROMISE repository (from 2005!) [[8]](#references)
* This is *tabular* data, containing 21 attributes--lines of code, number of public methods, depth of inheritance tree, etc.

### Step 2: Use a deep learner

* Why? Some preliminary results with classical learners did poorly.
* Obviously, we need to use hyper-parameter optimization (why? because hyper-parameters affect the number of piecewise linear regions of the decision boundary; see [[9]](#references)).
* And by the way, we need to oversample, since we have imbalanced data; the trivial way to do this is to use a weighted loss function.

<img src="/etc/img/weighted.png">

(Credits: I am the author of the paper this figure is from, and I permit myself to use it.)

* In fact, oversampling is as good as any other method to deal with imbalanced data, at least for convolutional networks [[10]](#references)--but there's no reason it shouldn't work for feedforward networks, right?.
* Weighted losses are also computationally efficient.

### Step 3: Define a preprocessing operator

* The above didn't work well at all, so we need a new hypothesis.
* This hypothesis is that the decision boundary gets too close to data samples, and therefore we may have samples that are accidentally on the other side (motivation: SVMs)

<img src="/etc/img/svm.webp">

(Credits: [[11]](#references))

<img src="/etc/img/wfo.png">

# But what about SE4AI?

* It exists, and it's called **MLOps**.

# References

[1] Desai, Utkarsh, Sambaran Bandyopadhyay, and Srikanth Tamilselvam. "Graph neural network to dilute outliers for refactoring monolith application." Proceedings of the AAAI Conference on Artificial Intelligence. Vol. 35. No. 1. 2021.
[2] Yedida, Rahul, et al. "How to Find Actionable Static Analysis Warnings." arXiv preprint arXiv:2205.10504 (2022).
[3] Tu, Huy, and Tim Menzies. "DebtFree: minimizing labeling cost in self-admitted technical debt identification using semi-supervised learning." Empirical Software Engineering 27.4 (2022): 1-37.
[4] Lustosa, Andre, et al. "SNEAK: Faster Interactive Search-based SE." arXiv preprint arXiv:2110.02922 (2021).
[5] Yedida, Rahul, et al. "An Expert System for Redesigning Software for Cloud Applications." arXiv preprint arXiv:2109.14569 (2021).
[6] Chen, Mark, et al. "Evaluating large language models trained on code." arXiv preprint arXiv:2107.03374 (2021).
[7] Yedida, Rahul, and Tim Menzies. "On the value of oversampling for deep learning in software defect prediction." IEEE Transactions on Software Engineering (2021).
[8] Shirabad, J. Sayyad, and Tim J. Menzies. "The PROMISE repository of software engineering databases." School of Information Technology and Engineering, University of Ottawa, Canada 24 (2005): 3.
[9] Montufar, Guido F., et al. "On the number of linear regions of deep neural networks." Advances in neural information processing systems 27 (2014).
[10] Buda, Mateusz, Atsuto Maki, and Maciej A. Mazurowski. "A systematic study of the class imbalance problem in convolutional neural networks." Neural networks 106 (2018): 249-259.
[11] <a href="https://commons.wikimedia.org/wiki/File:SVM_margin.png">Larhmam</a>, <a href="https://creativecommons.org/licenses/by-sa/4.0">CC BY-SA 4.0</a>, via Wikimedia Commons