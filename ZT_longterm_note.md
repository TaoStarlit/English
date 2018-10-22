# topic [algorithm, model, editor, program]
## what document and question, [solved/pending/plan], date


# algorithm, wiki
## MoEs - divide and conquer [plan] 20181010
https://en.wikipedia.org/wiki/Committee_machine#Dynamic_structures
A committee machine is a type of artificial neural network using a divide and conquer strategy in which the responses of multiple neural networks (experts) are combined into a single response.[1] The combined response of the committee machine is supposed to be superior to those of its constituent experts. Compare with ensembles of classifiers.
committee machine: 
1. static structure:  1 esemble averige; 2 boosting 
2. dynamic structure:
1 Mixture of experts
In mixture of experts, the individual responses of the experts are non-linearly combined by means of a single gating network.
2 Hierarchical mixture of experts -- several gating networks, not one gating network
In hierarchical mixture of experts, the individual responses of the individual experts are non-linearly combined by means of several gating networks arranged in a hierarchical fashion.
分类递归 $\in$算法导论，英文版自己处理一下！！  在 mendeley 里面， 我有第三版的pdf，第二版的 帮助文件，还有 读者自己写第二版的答案 -- 其他资料呢


# program, algorithm
## the 10 top algorithm in Data mining
a 2008 survey that identified the top 10 most influential algorithms in the data mining area. C4.5, k-Means, SVM, Apriori, EM, PageRank, AdaBoost, k-nearest neighborhood, naive Bayes, and classification and regression trees (CART), you can learning from Prof. Yang Qiang's paper, because the paper I read is refer to X. Wu, V. Kumar, J. R. Quinlan, J. Ghosh, Q. Yang, H. Motoda, G. J. McLachlan, A. Ng, B. Liu, P. S. Yu, Z.-H. Zhou, M. Steinbach, D. J. Hand, and D. Steinberg, “Top 10 algorithms in data mining,” Knowl. Inf. Syst., vol. 14, no. 1, pp. 1–37, 2008


# paper, algorithm
## MoEs suvery 20 years of MoEs [plan] 20181010
熟练用这个系统，你就能掌握很多算法！！ 毕业后出路几乎没有问题了
One of the major advantages of ME is that it is flexible
enough to be combined with a variety of different models. It has been combined with SVM [12]–[14] to partition the input space and to allocate different kernel functions for different input regions, which would not be possible with a single SVM. Recently, ME has been combined with GPs to make them accommodate nonstationary covariance and noise. A single GP has a fixed covariance matrix, and its solution typically requires the inversion of a large matrix. With the mixture of GP experts model [6], [7], the computational complexity of inverting a large matrix can be replaced with several inversions of smaller matrices, providing the ability to solve larger scale datasets. ME has also been used to make an HMM with time-varying transition probabilities that are conditioned on the input [4], [5].
- 问下学姐，这些公式
#### ans: 1022 自己仔细看
- the P can be used to denote any network with more information: eg.
    1. $P(y|x,\Theta)$ total probability of observing y (equal to certain value) given x
    2. $P(y,i|x,\Theta)$ from expert i, probability of observing y (equal to certain value) given x
    3. $P(i|x,\Theta_g)$ represents the gate's rating on expert i given x, which also denoted as $g_i(x,\Theta_g$
    4. $P(y|i,x,\Theta)$ is the probability of the i-th expert generating y given x, which will be denote by $P_i(y)$
- for classification/regression the gate is defined by softmax
    1. a smooth version of winer-take-all model
    2. gate i , means expert i win the a certain sample x againt. 
    3. $\beta_i(\mathbf{x,v})$ is the i-th component (vecter lenght is I) on x.      \usepackage{bm}    
    4. $\beta_i(\mathbf{x,v})=\mathbf v_i^T[\mathbf x, 1]$  bf in the parenthesis means in input is vector (not capital means not matrix).   v_i is the parameter (column vecter) for i. 
- different function for regression and classification
    1. classification, each expert i: $\hat y_{ik}=softmax_K(\mathbf w_{ik}^T[\mathbf x, 1])$ , softmax is k-th components over summation of K components
    2. last step $\hat y_k=\sum_i g_i(\mathbf{x,v})\hat y_{ik}$
    3. for regression, no softmax on $y_ik$, output is $\hat y_i$ directly. original ME regression is Gaussion model: $P(\mathbf x,\theta_i)=N(y|\hat y(\mathbf {x,w_i}), \sigma)$
- EM training: is an iterative method for finding the maximum likelihood of a probability model in which some random variables are observed and others are hidden.
    1. indicator variable
    2. product of gate and expert from n=1 to N $\to$ log sum of log gate and log expert from n=1 to N.

# model, paper, other topic
## the Yinhua Lijin's group [plan if you have time] 20181010
https://github.com/Hanjun-Dai/steady_state_embedding