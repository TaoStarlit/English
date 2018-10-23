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
### EM Q function
$L(\theta)=\log(Y|\theta)=\log\sum_ZP(Y,Z|\theta)=\log\sum_Z P(Z|Y,\theta)P(Z|\theta)$ 这里的困难是 包含有1)隐藏变量 还有 2)累加和（积分）的对数

   - $P(Y,Z)=P(Y|Z)P(Z)$ Joint Probability is the product, Marginal Probability as condition is denominator

对于某一次迭代的参数，我们的似然函数是 $L(\theta^{(i)})=\log P(Y|\theta^{(i)})$

$L(\theta)-L(\theta^{(i)})$ 再用jenson不等式，得到$L(\theta)$下界:
$L(\theta)-L(\theta^{(i)})\geq \sum_Z P(Z|Y,\theta^{(i)}) \log \frac {P(Y|Z,\theta)P(Z|\theta)} {P(Z|Y,\theta^{(i)})P(Y|\theta^{(i)})}$
$L(\theta)\geq L(\theta^{(i)})+\sum_Z P(Z|Y,\theta^{(i)}) \log \frac {P(Y|Z,\theta)P(Z|\theta)} {P(Z|Y,\theta^{(i)})P(Y|\theta^{(i)})}=B(\theta,\theta^{(i)})$

优化下界就是优化Q函数（把下界里面的$\theta^{(i)}$当作常数）：
$\theta^{(i+1)}=arg\max_\theta B(\theta,\theta^{(i)})=arg\max_\theta \sum_Z P(Z|Y,\theta^{(i)}) \log P(Y|Z,\theta)P(Z|\theta)=arg\max_\theta \sum_Z P(Z|Y,\theta^{(i)}) \log P(Y,Z|\theta) = arg\max_\theta Q(\theta,\theta^{(i)})$
  1. jenson inequality: 积分（累加和）的凸函数(log)$\geq$凸函数(log)的积分（累加和） ==>把累计和从log里面拿出来
  1. 在极大化$B(\theta,\theta^{(i)})$ 过程中 $\theta^{(i)}$ 算是常数，直接消掉

conclusion: EM是通过 不断求解下界（B函数）的极大化(上一代参数当常数，变为Q函数)，逼近所求似然函数极大化的方法，（下界取了最大值，不代表原来函数就取了最大值 ）。 Q 函数里面，就是 $\sum_Z P(Z|Y,\theta^{(i)}) \log P(Y,Z|\theta)$
  1. 通过 上代参数，观测值 逐个求隐藏值 $P(Z|Y,\theta^{(i)})$, 逐个所以没有概率什么事，当作$Z=f(Y,\theta^{(i)})$
  1. 对完全数据的似然函数进行极大化，原来似然怎么求，现在就怎么求? 看原来的

### naive Bayes
在李航书里面，朴素贝叶斯方法（求生成模型+先验概率，进而得到最大后验概率--也就是最小期望风险）可以用极大似然来解,也可用贝叶斯估计来求解（多了个拉普拉斯平滑）
1. 贝叶斯公式： 后验概率=先验概率*条件概率/边沿概率
2. 条件概率这里是生成模型，参数太多：比如基于现有的数据（书中例子为离散）统计出 P(x|y=1) P(x|y=0) 如果x, d个维度, v个取值，$v^d$个则 $P(x|y=1)$ 就有 给你算（eg. $P(x=(0,1)|y=1)=?; P(x=(1,1)|y=1)=?$ ...） 总的是 $K*v^d$个参数
3. 减少参数的方法，假设每个feature（x每个维度）都是独立的，那么现在只需要$P(x_0=0|y=1)=2/3; P(x_0=10|y=1)=1/3$  参数个数瞬间变成了$K*v*d$(先验的参数少两个量级，先忽略不计)
4. 回到贝叶斯公式$P(y=c_k|x)$ 由于对任何y的取值，在边沿概率都完全相等，因此最后的模型我们就这样：后验概率=先验概率*条件概率。 尽管除以一个小于1的书，看起来后验概率偏小，但是我们是对比$P(y=1|x) P(y=0|x)$ 大小的，所以结果，无影响。 
5. 极大似然估计，上面的参数表 先验概率*条件概率 是用极大似然估计，通过样本估估计出来的，其中指示函数，就是数数的： $P(y=c_k)=\sum_i^N I(y=c_k)/N,k=1,2,..K$ (这里左边有下标，所以是表示K个标量了)，条件概率也是数数 $P(x^{(i)}=a_{iv}|y=c_k)=\sum_i^N I(x^{(i)}=a_{jv},y=c_k)/\sum_i^N I(y=c_k)$,然后得到了参数表格
6. 贝叶斯估计用来代替的极大似然估计的，加入了拉普拉斯平滑（Laplace smooth) $\lambda$参数。用来减少概率值接近0时，后验概率性能受到影响。因为当概率相差太大时，这个平滑保持相对大小关系，而减小了彼此差距 如：1/9 4/9 4/9 平滑后变成了 1/6 5/12 5/12


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
- in a [link](https://people.cs.pitt.edu/~milos/courses/cs2750-Spring03/lectures/class20.pdf)  it said hidden variable is g's output(similar to the out put of first coins in 3 coins problem)

# model, paper, other topic
## the Yinhua Lijin's group [plan if you have time] 20181010
https://github.com/Hanjun-Dai/steady_state_embedding

# book list:
在李航-统计机器学习（国内教材的风格）的书里面是，极大似然估计是属于朴素贝叶斯； 在USML里面，朴素贝叶斯是属于生成模型 
prml（算是舍近求远的贝叶斯）和esl（机器学习：统计学家的方法） 也许会比李航的书好点，
1. 复习数学： b站3blue1brown的十几集视频
2. 在线课程：网易公开课上麻省理工Patrick Winston人工智能6.034课程视频二十几集
3. 机器学习实战里的Python代码随便跑跑