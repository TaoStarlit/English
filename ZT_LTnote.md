# USML 2-5 agnotic PAC learnability, No-Free-Lunch
### 2 A Gentle Start
$\mathcal X$: feature space, domain set(if it is finite space, then the domain set is finte, eg. $\mathcal X=\mathcal Y=\{0,1\}$ 

$\mathcal Y$: label set $\{0,1\}$

$S={(x_1,y_1),...,(x_m,y_m)}$ training set is a finite sequence of pairs in $\mathcal X \times \mathcal Y$

$h:\mathcal X \to \mathcal Y$ The learner's output: a predictor or a hypothesis

$A(S)$   learner/learning algorithm returns $h_S$ upon receving the training sequence S.

$\mathcal D$  probability over $\mathcal X$, (the difference: $\mathcal X$ set, no repeat elements; $\mathcal D$ some elements are more or less, eg. $P(x=0)=0.8; P(x=1)=0.2$)

$f: \mathcal X \to \mathcal Y$ correct label function

$L_{\mathcal D,f}(h) =P_{x \sim D}[h(x)\neq f(x)]=D(\{x:h(x)\neq f(x)\})$ error of a hypothesis h. the critiria here is $\mathcal D,f$, the ground true  .  
- ?*how to interpret the D(x:)*

$L_{S}(h) = \frac {|\{i \in [m]: h(x)\neq y\}|} m$ traning error
- |.| means count the number, and $[m]=\{1,...,m\}$

$h_S=ERM_\mathcal H(S) = argmax_{h\in\mathcal H}L_S(h)$ ERM return h_S upon receiving S

$\delta$ the probability of getting a nonrepresentative sample (a sample means a sample set)

$1-\delta$ the confidence parameter of our prediction (the sample is representive, so we are confident)

$\epsilon$ accuracy parameter: $L_{\mathcal D,f}(h)\leq \epsilon$, then h is approximately correct predictor; $L_{\mathcal D,f}(h) > \epsilon$, then it is a failure of the learner
- here epsilon is the parameter for quality of prediction, latter is error and can be decomposed

$\mathcal D^m(\{S|_x: L_{\mathcal D,f}(h) > \epsilon\})\leq|\mathcal H_B|e^{-\epsilon m}\leq |\mathcal H|e^{-\epsilon m}$
- ? $\mathcal D^m$ denotes the probability over m-tuples  induced by applying $\mathcal D$  to pick each element of the tuple independently of the other members of the tuple. 

$m\geq\frac {\log (\mathcal H/\delta)} \epsilon$ m a integer satifies ~ then ..., it holds that $L_{\mathcal D,f}(h)\leq \epsilon$ (h is approximately correct predictor).   
- for a suffiently large m, the ERM rule over a finite hypothesis class will be probably (with confidence 1-\delta) approximately (upto an error \epsilon) corret.

### 3 A Formal Learning Model
?? sample more or small??
Corllary 3.2 Every finite hypothesi class is PAC learnable with the sample complexity $m_\mathcal H \leq \lceil\frac {\log (\mathcal H/\delta)} \epsilon \rceil$   
- ceil function: least integer that greater than or equal to x; 
- floor function: greatest integer that less than or equal to x

new rule: ground truth is the distribution, no label function any more. As now identical x_1 x_2 can have different y value based on probability.   remove realization assumption: no perfect $h^*$ now, we use $h^\prime$ for the optimal in $\mathcal H$

$\mathcal D$ distribution over $\mathcal X \times \mathcal Y$, so now $L_\mathcal D(h)$ is true error (no f anymore), $L_S(h)$ is also empirical error.

$L_{\mathcal D}(h_S)\leq \min_{h^\prime\in \mathcal H}L_\mathcal D(h^\prime)+\epsilon$, definition 3.3 Agnostic PAC Learnability.  
- The 2nd item is the loss of opimal hypothesis. if the realizability assumption holds, (=0) agnostic PAC learning provides the same guarantee as PAC learning.
  
### 4 Learning via uniform convergence
$L_{\mathcal D}(h_S)\leq \min_{h\in \mathcal H}L_\mathcal D(h)+\epsilon$  from Lemma 4.2 \epsilon-representative
 
### 5 The Bias-Complexity Tradeoff
$L_{\mathcal D}(h_S)= \epsilon_{app}+\epsilon_{est}$ ; where: $\epsilon_{app}=\min_{h\in \mathcal H}L_\mathcal D(h)$ - the approximation error: the minimum rish achievable by a predictor in the hypotheis. (due to the search scope of H)
- the estimation error: the difference between the approximation error and the error achieved by the ERM predictor. (trainig on S perfect, there are still estimation error)
- tradeoff: a very rich hypothesis class decreases the approximation error but might increase the estimation error,as a rich H might lead to overfitting. So the error not good;   On the other hand, small class H reduced the estimation error but increase the approximation error or, in other word, might lead to underfitting.


# PRML 2 Probability distribuion

## 2.1 binary variables
##### Bernouli
one coin: $p(x=1|\mu)=\mu$

$p(x=0|\mu)=1-\mu$

$Bern(x|\mu)=\mu^x(1-\mu)^{1-x}$  

$\mathbb E[x]=\mu$, $var[x]=\mu(1-\mu)$  

$p(x|\mu)$

$Likelihood=p(\mathcal D|\mu)=\Pi_{n=1}^N p(x_n|\mu)=\Pi_{n=1}^N\mu^{x_n}(1-\mu)^{1-x_n}$

$LogLikelihood=\ln p(\mathcal D|\mu)=\sum_{n=1}^N \ln p(x_n|\mu)=\sum_{n=1}^N [{x_n}\ln \mu + (1-x_n) \ln (1-\mu)]$

$\frac d {d\mu} \ln p(\mathcal D|\mu)=x_n/\mu+(1-x_n) /(1-\mu)(-1)=x_n/\mu-(1-x_n) /(1-\mu)$ 
$\therefore$
$\sum_{n=1}^N [x_n/\mu-(1-x_n) /(1-\mu)]=0$  
$\therefore$  $\sum_{n=1}^Nx_n(1-\mu)-\mu\sum_{n=1}^N(1-x_n)=0*denominator$ 
$\therefore$ $\sum x-\mu\sum x - \mu N - \mu\sum x=\sum x - \mu N=0$
- $\ln x= 1/x$
- $(1+y)/x+1/(x+1)=0$ $\therefore$ $(1+y)(x+1)+1x=0*denominator$
- $\sum_{n=1}^N(1-x_n)=N-\sum_{n=1}^N x_n$

$\mu= \sum_n x_n/N$

##### Binomial:
filp one coin N time: $bin(m|N,\mu)=C_N^m\mu^m(1-\mu)^{N-m}$

$\mathbb E[m]=N \mathbb E[Bern(x|\mu)]=N\mu; var[m]=N var[Bern(x|\mu)]=N\mu(1-\mu)$

###### writing
- the probability of x=1 will be denoted by the parameter \mu : where $..\geq..$
- the **probability distribution over x** can therefore be written in the form(exponential distribution): which is known as the Bernoulli distribution. 
- It is easily verified that this distribution is normalized and that it has mean and variance given by:
- observations are drawn independently from Bernouli distribution:
- we can estimate a value for mu by maximizing the likelihood function:
- or equivalently by maximizing the logarithm of the likelihood. The funtion is given by:
- we set the derivative of $\sum \ln p(\mathcal x_n|\mu)$ with respect to $\mu$ equal to zero:
- we obtain the maximum likelihood estimator:
####### question
1. not Gaussian, why var?
   - ans: every distribution has variance. Suppose we have a data set $\{x_i,x_2,...x_N\}$ of observed values of x.  Then $\hat\mu=\sum_i x_I$ $\hat \sigma=\frac 1 N \sum_i (x_i-\hat x_i)^2$
2. why MLE of exponential family distriubtion is easy?
   - ans: MLE using logrithm and the logarithm is the inverse function to exponentiation. in the exponential family the x is in the exponent part, the estimated parameter is in the base part, so after logarithm, x became the coefficient of ln, and parameter is in the ln)



###### 2.1.1 the beta distribution: a prior distribution p(\mu) over the papameter \mu, the form is designed for normalization and posterior will have the same functional form as the prior.
$Beta(\mu|a,b)=\frac {\Gamma(a+b)}{\Gamma(a)\Gamma(b)}\mu^{a-1}(1-\mu)^{b-1}$

$\int_0^1Beta(\mu|a,b)d\mu=1$

$\mathbb E[\mu]=\frac a {a+b}$

...

## 2.2

- the 3 times coins give severly over-fitted result for small data sets. In order to develop a Bayesian treament for this problem, we need to introduce a prior distribution over the parameter $\mu$. (over $\neq$ its)
- the gamma function. the coefficient ensure the beta distribution is normalized, so that:

## 2.2 Multimomial Variables
K state:
$p(\mathbf x| \mathbf \mu)=\Pi_{k=1}^K\mu_k^{x_k}$

x is one hot vector: $\mathbf x=(0,1,0,0)^T$; $\mathbf \mu=(\mu_1,...,\mu_K)^T$ are constrained to satisfy $u_k\geq 0$ and $\sum_k \mu_k = 1$

$\mathbb E[\mathbf x | \mathbf \mu]=\sum_\mathbf x p(\mathbf x|\mathbf \mu) \mathbf x = \mathbf\mu$

$p(\mathcal D|\mathbf \mu)=\Pi_{n=1}^N \Pi_{k=1}^K\mu_k^{x_{nk}}=\Pi_{k=1}^K\mu_k^{\sum_nx_{nk}}$

$m_k=\sum_n x_{nk}$

$\ln p(\mathcal D|\mathbf \mu)=\sum_{k=1}^K \ln \mu_k^{m_k}=\sum_{k=1}^K {m_k} \ln \mu_k$

$\sum_{k=1}^K {m_k} \ln \mu_k + \lambda (\sum_k \mu_k - 1)$

###### writing
- a generation of Bernouli distribution to more than 2 outcome or to K states:
- we encounter discrete variables that take on one of K possible mutually exclusive states. Although there are various alternative ways to express such variables, we shall see shortly that a particularly convenient representation is the 1-of-K (one hot) scheme, in which the variable is represented by a K-dimensional vector x in which one of the elements x_k equals to 1, and all remaining elements equal 0.
- the mean of variable x
- Now condider a data set D of N independent observations $\bf {x_1,...,x_N}$
- m, which represent the number of observation of x_k=1.
- to find the maximum likelihood solution for $\mu$, we need to maximize $\ln p(\mathcal D|\mathbf\mu)$ with respect to $\mu_k$:
- (Lagrange) Taking accout of the constraint that the $\mu_k$ must sum to one. This can be achieved using a Lagrange multipier lambda and maximizing. (**constrain=0, with summation --> use Lagrange multipier**)

###### question
1. why Lagrange
   - because the constrain ($\sum =1$) in optimization problem (maximum likelihood)

###### 2.2.1 The dirichlet distribution
- in order to obtain the normalization coefficient we note that our of N coin flips, we have to add up all the possible ways of obtaining m heads, so that the binomial distribution can be written:
- C_N^m is the number of ways of choosing m objects out of a total of N
- (using exersice 1.10)For independent events, the mean of the sum is the sum of the means,
- and the variance of the sum is the sum of the variances, we have:


### new word
Bernouli, exponential; logarithm (algorithm,before Rithm, both a and o are light), denominator
Binomial, Multinoimal; lagrange (laGrange) multiplier (Oo,oo). dirichlet: (Oo k,let)



# 1024  GP<-Gassian Kernel;  EM<-exponential familiy<-PRML chapter2
GP: is about Gassian Kernel.

the gate has no analytical solution due to the non-linearity of softmax, so using Iteratively reweighted least squares(IRLS) in the EM iteration.  I don't know the indicator so I don't know the EM iteration here. 
1. reference 46, 4.3 is indicator
    1.  when the underlying complete data come from an exponential family whose maximum-likelihood estimates are easily computed, then each maximization step of an EM algorithm is likewise easily computed. --- MLE of exponential family distribution is easy!! what is exponential (PRML:probability distribution + generative model)

to avoid the inner loop iteration, Xu introduce an alternative gate function: I don't know why joint distribution can help get a analytical solution of the gate. 









