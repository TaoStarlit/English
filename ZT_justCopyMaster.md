# 1024 from the master stream longtern
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
