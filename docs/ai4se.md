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

### Step 2: Try a classical model

* Classical models run significantly faster than deep learners, and can often perform as well as deep learners.
* You can use algorithms like DODGE [[17]](#references) to tune multiple learners with multiple configs each in minutes.
* Moreover, classical models are more interpretable, which can be preferable [[18]](#references).
* That said: classical learners, like any learner in a non-convex landscape, can fall into local optima--moreover, neural networks distilled into soft decision trees can perform better than decision trees trained directly on the data, due to dark knowledge [[19]](#references).
  * **Brownie points:** I've noticed this is true, at least for defect prediction, even when you distill into a hard decision tree--can you code this up?

### Step 3: Use a deep learner

* Why? Some preliminary results with classical learners did poorly.
* Obviously, we need to use hyper-parameter optimization (why? because hyper-parameters affect the number of piecewise linear regions of the decision boundary; see [[20]](#references)).
  * **Brownie points:** derive a greedy approach to find the optimal theoretical architecture based on Theorem 5 of this paper, given the number of linear regions required to separate the data. (And if you can find a way to compute the number of linear regions needed, you're strongly encouraged to join the lab!)
* And by the way, we need to oversample, since we have imbalanced data; the trivial way to do this is to use a weighted loss function.

$$
\mathcal{L}^1(y_i, \hat{y_i}) = \frac{w_i}{n}\sum_{\substack{i=1 \\ y_i = c_0}}^m \mathcal{L}(y_i, \hat{y_i}) + \sum_{\substack{i=1 \\ y_i \neq c_0}}^m \mathcal{L}(y_i, \hat{y_i})
$$

(Credits: I am the author of the paper this figure is from, and I permit myself to use it.)

* In fact, oversampling is as good as any other method to deal with imbalanced data, at least for convolutional networks [[21]](#references)--but there's no reason it shouldn't work for feedforward networks, right?.
* Weighted losses are also computationally efficient (why?).

### Step 4: Define a preprocessing operator

* The above didn't work well at all, so we need a new hypothesis.
* This hypothesis is that the decision boundary gets too close to data samples, and therefore we may have samples that are accidentally on the other side (motivation: SVMs)

<img src="/etc/img/svm.webp">

(Credits: [[22]](#references))

<img src="/etc/img/wfo.png">

* Note here the difference between this method of pushing data samples away vs. the SVM way: the SVM uses a convex optimization problem to find the optimal decision boundary, while this method uses a computational method of doing so. This makes the SVM more efficient, but you may need a softer margin to get the same results.

### Step 5: Iterate on the solution

* We can apply fuzzy sampling to the majority class as well.
* Fuzzy sampling creates the opposite class imbalance problem (ironically, the same problem we had before), but we can use SMOTE to solve it.
  * **Brownie points:** How many times can you apply fuzzy sampling (and then end it with SMOTE) before you get worse results? Can you explain why too many rounds of fuzzy sampling is bad, aside from the computational cost?
  * **Brownie points:** Can you find an issue with this approach? Hint: something here is unnecessary.

Congrats--you are now the SOTA for defect prediction! Until the next guy comes along, that is.

### Lessons learned

* We were very AI-centric about our approach--the actual data itself, or its source never impacted our decisions.
* We did need to come up with a novel preprocessing operator, perhaps because we failed to include domain knowledge.
* Although we used a feature set from 2005, we beat state-of-the-art approaches that used language models to mine features. 

## Options, options, options

* The number of options to tune can be daunting.
* In software configuration, for example, MySQL has 461 options, which is $10^{138}$ possible configurations [[23]](#references). Most of these have little to no effect.
* This is true for machine learning, but especially so for deep learning:
  * Learning rate [[24]](#references)
  * Activation function [[25-26]](#references) (the latter activation function has its own Twitter account--[no, really](https://twitter.com/SELUAppendix))
  * Batch normalization [[27]](#references) or dropout [[28]](#references), but not both [[29]](#references).
  * Initialization [[30, 41]](#references)
  * Loss functions
* How do we tackle this?
  * Hyper-parameter optimization [[17, 31-39]](#references)
  * Neural architecture search [[40, 42-55]](#references)

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

# X vs Y

* Decision trees vs. SVMs
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
[17] Agrawal, Amritanshu, et al. "How to “dodge” complex software analytics." IEEE Transactions on Software Engineering 47.10 (2019): 2182-2194.
[18] Rudin, Cynthia. "Stop explaining black box machine learning models for high stakes decisions and use interpretable models instead." Nature Machine Intelligence 1.5 (2019): 206-215.  
[19] Frosst, Nicholas, and Geoffrey Hinton. "Distilling a neural network into a soft decision tree." arXiv preprint arXiv:1711.09784 (2017).  
[20] Montufar, Guido F., et al. "On the number of linear regions of deep neural networks." Advances in neural information processing systems 27 (2014).  
[21] Buda, Mateusz, Atsuto Maki, and Maciej A. Mazurowski. "A systematic study of the class imbalance problem in convolutional neural networks." Neural networks 106 (2018): 249-259.  
[22] <a href="https://commons.wikimedia.org/wiki/File:SVM_margin.png">Larhmam</a>, <a href="https://creativecommons.org/licenses/by-sa/4.0">CC BY-SA 4.0</a>, via Wikimedia Commons. 
[23] Xu, Tianyin, et al. "Hey, you have given me too many knobs!: Understanding and dealing with over-designed configuration in system software." Proceedings of the 2015 10th Joint Meeting on Foundations of Software Engineering. 2015.  
[24] Yedida, Rahul, Snehanshu Saha, and Tejas Prashanth. "Lipschitzlr: Using theoretically computed adaptive learning rates for fast convergence." Applied Intelligence 51.3 (2021): 1460-1478.  
[25] Saha, Snehanshu, et al. "Evolution of novel activation functions in neural network training for astronomy data: habitability classification of exoplanets." The European Physical Journal Special Topics 229.16 (2020): 2629-2738.  
[26] Klambauer, Günter, et al. "Self-normalizing neural networks." Advances in neural information processing systems 30 (2017).  
[27] Ioffe, Sergey, and Christian Szegedy. "Batch normalization: Accelerating deep network training by reducing internal covariate shift." International conference on machine learning. PMLR, 2015.  
[28] Srivastava, Nitish, et al. "Dropout: a simple way to prevent neural networks from overfitting." The journal of machine learning research 15.1 (2014): 1929-1958.  
[29] Li, Xiang, et al. "Understanding the disharmony between dropout and batch normalization by variance shift." Proceedings of the IEEE/CVF conference on computer vision and pattern recognition. 2019.  
[30] He, Kaiming, et al. "Delving deep into rectifiers: Surpassing human-level performance on imagenet classification." Proceedings of the IEEE international conference on computer vision. 2015.  
[31] Bergstra, James, et al. "Algorithms for hyper-parameter optimization." Advances in neural information processing systems 24 (2011).  
[32] Bergstra, James, and Yoshua Bengio. "Random search for hyper-parameter optimization." Journal of machine learning research 13.2 (2012).  
[33] Bergstra, James, Daniel Yamins, and David Cox. "Making a science of model search: Hyperparameter optimization in hundreds of dimensions for vision architectures." International conference on machine learning. PMLR, 2013.  
[34] Bergstra, James, et al. "Hyperopt: a python library for model selection and hyperparameter optimization." Computational Science & Discovery 8.1 (2015): 014008.  
[35] Loshchilov, Ilya, and Frank Hutter. "CMA-ES for hyperparameter optimization of deep neural networks." arXiv preprint arXiv:1604.07269 (2016).  
[36] Falkner, Stefan, Aaron Klein, and Frank Hutter. "BOHB: Robust and efficient hyperparameter optimization at scale." International Conference on Machine Learning. PMLR, 2018.  
[37] Pedregosa, Fabian. "Hyperparameter optimization with approximate gradient." International conference on machine learning. PMLR, 2016.  
[38] Bardenet, Rémi, et al. "Collaborative hyperparameter tuning." International conference on machine learning. PMLR, 2013.  
[39] Lindauer, Marius, et al. "SMAC3: A Versatile Bayesian Optimization Package for Hyperparameter Optimization." J. Mach. Learn. Res. 23 (2022): 54-1.
[40] Liu, Chenxi, et al. "Auto-deeplab: Hierarchical neural architecture search for semantic image segmentation." Proceedings of the IEEE/CVF conference on computer vision and pattern recognition. 2019.  
[41] Zhang, Hongyi, Yann N. Dauphin, and Tengyu Ma. "Fixup initialization: Residual learning without normalization." arXiv preprint arXiv:1901.09321 (2019).  
[42] Elsken, Thomas, Jan Hendrik Metzen, and Frank Hutter. "Neural architecture search: A survey." The Journal of Machine Learning Research 20.1 (2019): 1997-2017.  
[43] Liu, Chenxi, et al. "Progressive neural architecture search." Proceedings of the European conference on computer vision (ECCV). 2018.  
[44] Zoph, Barret, and Quoc V. Le. "Neural architecture search with reinforcement learning." arXiv preprint arXiv:1611.01578 (2016).  
[45] Tan, Mingxing, et al. "Mnasnet: Platfor m-aware neural architecture search for mobile." Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition. 2019.  
[46] Pham, Hieu, et al. "Efficient neural architecture search via parameters sharing." International conference on machine learning. PMLR, 2018.  
[47] Jin, Haifeng, Qingquan Song, and Xia Hu. "Auto-keras: An efficient neural architecture search system." Proceedings of the 25th ACM SIGKDD international conference on knowledge discovery & data mining. 2019.  
[48] Mellor, Joe, et al. "Neural architecture search without training." International Conference on Machine Learning. PMLR, 2021.  
[49] Li, Liam, and Ameet Talwalkar. "Random search and reproducibility for neural architecture search." Uncertainty in artificial intelligence. PMLR, 2020.  
[50] Zhou, Hongpeng, et al. "Bayesnas: A bayesian approach for neural architecture search." International conference on machine learning. PMLR, 2019.  
[51] Wen, Wei, et al. "Neural predictor for neural architecture search." European Conference on Computer Vision. Springer, Cham, 2020.  
[52] Gong, Xinyu, et al. "Autogan: Neural architecture search for generative adversarial networks." Proceedings of the IEEE/CVF International Conference on Computer Vision. 2019.  
[53] Xie, Sirui, et al. "SNAS: stochastic neural architecture search." arXiv preprint arXiv:1812.09926 (2018).  
[54] Nayman, Niv, et al. "Xnas: Neural architecture search with expert advice." Advances in neural information processing systems 32 (2019).  
[55] Yang, Zhaohui, et al. "Cars: Continuous evolution for efficient neural architecture search." Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition. 2020.  
