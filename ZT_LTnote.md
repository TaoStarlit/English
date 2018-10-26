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
- ?*how to interpret the D(x:)*, here all D mean distribution, D also the probablity over the space X (eg. P(x=1)=0.8, p(x=0)=0.2)
  - ans: x is sample from this distribution D, orinally D(x) represent the probability x status, now is the probability that h(x)\neq f(x)

$L_{S}(h) = \frac {|\{i \in [m]: h(x)\neq y\}|} m$ traning error
- |.| means count the number, and $[m]=\{1,...,m\}$

$h_S=ERM_\mathcal H(S) = argmax_{h\in\mathcal H}L_S(h)$ ERM return h_S upon receiving S

$\delta$ the probability of getting a nonrepresentative sample (a sample means a sample set)

$1-\delta$ the confidence parameter of our prediction (the sample is representive, so we are confident)

$\epsilon$ accuracy parameter: $L_{\mathcal D,f}(h)\leq \epsilon$, then h is approximately correct predictor; $L_{\mathcal D,f}(h) > \epsilon$, then it is a failure of the learner
- here epsilon is the parameter for quality of prediction, latter is error and can be decomposed

$\mathcal D^m(\{S|_x: L_{\mathcal D,f}(h_S) > \epsilon\})\leq|\mathcal H_B|e^{-\epsilon m}\leq |\mathcal H|e^{-\epsilon m}$
- ! $\mathcal D^m$ denotes the probability over m-tuples  induced by applying $\mathcal D$  to pick each element of the tuple independently of the other members of the tuple.
    - ans: upon S with m observations that are sampled according to D, the probability of failure of the learner. (m up -- good, or \epsilon up -- more tolerant, then the upper bound down, probability of failure down)

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
- The 2nd item is the loss of opimal hypothesis. if the realizability assumption holds, (=0) agnostic PAC learning provides the same guarantee as PAC learning (not need use ' but *, if assumption holds).
  
### 4 Learning via uniform convergence
$L_{\mathcal D}(h_S)\leq \min_{h\in \mathcal H}L_\mathcal D(h)+\epsilon$  from Lemma 4.2 \epsilon-representative
 
### 5 The Bias-Complexity Tradeoff
$L_{\mathcal D}(h_S)= \epsilon_{app}+\epsilon_{est}$ ; where: $\epsilon_{app}=\min_{h\in \mathcal H}L_\mathcal D(h)$ 
- the approximation error: the minimum rish achievable by a predictor in the hypotheis. (due to the search scope of H), note $h$ not $h_S$
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
- we can estimate a value for \mu by maximizing the likelihood function:
- or equivalently by maximizing the logarithm of the likelihood. The funtion is given by:
- we set the derivative of $\sum \ln p(\mathcal x_n|\mu)$ with respect to $\mu$ equal to zero:
- we obtain the maximum likelihood estimator:
- (Binomial) in order to obtain the normalization coefficient we note that our of N coin flips, we have to add up all the possible ways of obtaining m heads, so that the binomial distribution can be written:
- C_N^m is the number of ways of choosing m objects out of a total of N
- (using exersice 1.10)For independent events, the mean of the sum is the sum of the means,
- and the variance of the sum is the sum of the variances, we have:


###### question
1. not Gaussian, why var?
   - ans: every distribution has variance. Suppose we have a data set $\{x_i,x_2,...x_N\}$ of observed values of x.  Then $\hat\mu=\sum_i x_I$ $\hat \sigma=\frac 1 N \sum_i (x_i-\hat x_i)^2$
2. why MLE of exponential family distriubtion is easy?
   - ans: MLE using logarithm and the logarithm is the inverse function to exponentiation. In the exponential family the x is in the exponent part, the estimated parameter is in the base part, so after logarithm, x became the coefficient of \ln (just sum the observations), and parameter is in the \ln. Therefore, it is easy to derivate and set the derivative with respect to the parameter equal to 0, and then obtain the value of the estimated parameter.



###### 2.1.1 the beta distribution: a prior distribution p(\mu) over the papameter \mu, the form is designed for normalization and posterior will have the same functional form as the prior.
$Beta(\mu|a,b)=\frac {\Gamma(a+b)}{\Gamma(a)\Gamma(b)}\mu^{a-1}(1-\mu)^{b-1}$

$\int_0^1Beta(\mu|a,b)d\mu=1$

$\mathbb E[\mu]=\frac a {a+b}$

...

###### writing:
- the 3 times coins give severly over-fitted result for small data sets. In order to develop a Bayesian treament for this problem, we need to introduce a prior distribution over the parameter $\mu$. (over $\neq$ its)
- the gamma function. the coefficient ensure the beta distribution is normalized, so that:

## 2.2 Multinomial Variables
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
- we encounter discrete variables that take on one of K possible mutually exclusive states. Although there are various alternative ways to express such variables, we shall see shortly that a particularly convenient representation is the 1-of-K (one hot) scheme, in which the variable is represented by a K-dimensional vector \mathbf x in which one of the elements x_k equals to 1, and all remaining elements equal 0.
- the mean of variable \mathbf x
- Now condider a data set D of N independent observations $\bf {x_1,...,x_N}$, the coorisponding likelihood function take the form as:
- m, which represent the number of observation of x_k=1.
- to find the maximum likelihood solution for $\mu$, we need to maximize $\ln p(\mathcal D|\mathbf\mu)$ with respect to $\mu_k$:
- (Lagrange) Taking accout of the constraint that the $\mu_k$ must sum to one. This can be achieved using a Lagrange multipier lambda and maximizing. (**constrain=0, with summation --> use Lagrange multipier**)

###### question
1. why Lagrange
   - because the constrain ($\sum =1$) in optimization problem (maximum likelihood)

###### 2.2.1 The dirichlet distribution
binomial <-- prior  Beta
multimoimal <-- prior  Dirichlet

## 2.3 Gaussian distribution
The Gaussian distribution airses in many different contexts and can be motivated from a variety of different perspectives.
1. for a single variable, the distribution that maximizes the entropy is the Gaussian. This property applies also to the multivariate Gaussian.
2. the sum of multiple random variables. ~ has a distribution that becomes increasing Gaussian as the number of terms in the sum increase.

we strongly encourage the reader to become proficient in manipulating Gaussian distribution using the techniques presented here  as this will prove invaluable in understanding the more complex models presented in later chapters.
1. the covariance matrix can be taken to be symmetric, without loss of generality, because any antisymmetric component would disappear from the exponent.

$\mathcal N(x|\mu,\sigma^2)=\frac 1 {(2\pi\sigma^2)^{1/2}}\exp\{-\frac 1 {2\sigma^2} {(x-\mu)}^2\}$

$\mathcal N(x|\mathbf \mu,\Sigma)=\frac 1 {(2\pi)^{D/2}|\Sigma|^{1/2}}\exp\{\Delta^2\}$

$\Delta^2=(\mathbf{x-\mu})^T \mathbf\Sigma^{-1}(\mathbf{x-\mu})$,     for 1-D: $\Sigma^{-1}=1/\sigma^2$

$\mathbf{y=U(x-\mu)}$

$j_{ij}=\frac {\partial x_i}{\partial y_j}=U_{ji}$

- in the case of single variable x, the Gaussian distribution can be written in the form: ~ where \mu is the mean and \sigma^2 is the variance.
- For D-dimensional vector x, the multivariate Gaussian distribution takes the form ~ where \bf\mu is the a D-dimension mean vector, \bf\Sigma is a DxD covariance matrix, and |\bf\Sigma| denotes the determinant of \bf\Sigma.
- We begin by considerting the geometrical form of the Gaussian distriubtion. The functional dependence of the Gaussian on \bf x is through the quandratic form: ~ which appears in the exponent. The quantity \Sigma is called *Mahalanobis distance* from \bf\mu to \bf x   and reduces to the Euclidean distance when \Sigma is the identity matrix.  -- identity means: no deviation, no relation between different dimension.
- eigenvector equation for the convariance matirx
- we can interpret {y_i} as a new coordinate system defined by the orthonormal vectors \bf\mu_i that are shifted and rotated with respect to the original x_i coordinates. From the vector y=tran(x), we have:
- In going to from the x to the y coordinate system, we have a Jacobian matrix J with element given by:~ where U_{ji} are the elements of the matrix \mathbf U^T  --> the normalization (1.48) ($\int_{-\infty}^\infty p(x|\theta)dx$) of the Gaussian.
- We now look at the moments of the Guassian distribuion and thereby provide an interpretation of the parameters \mu and \Sigma.


###### questions:
1. why 1? where have we seen that?
2. this distribution how to get the mahalanobis/Euclidean distance that is between two points, not distrbution.  
   - ans: x is an observation, then the \Delta is the distance from \mu. if D=1, it is 1/sigma^2 \times Euclidean distance.
3. symmetric matirx, antisymmetric component, orthonormal set.
   - orthognal matrix: $\mathbf{UU^T=I}$
4. what is surface and constant?
5. it is necessary for all of the eigenvalues \lambda_i of the covariance matrix to be strictly positive (\Sigma is positive definite), otherwise the distribution cannot be properly normalized. again normalized??

#### 2.3x mixture Gaussian, likelihood ...

## 2.4 the Exponential family:
Members of the exponential family have many important properties in common, ant it is illuminating to discuss these properties in some generality.

$p(\mathbf{x|\eta})=h(\mathbf x)g(\mathbf\eta)\exp\{\mathbf{\eta^T u(x)}\}$

$g(\eta)\int h(x)\exp\{\eta^T u(x)\}dx=1$, (omit \bf here)

- The exponential family of distributions over x, given parameter \eta, is defined to be the set of distribution of the form: ~ where x may be scalar or vector, and may be discrete or continuous. Here \eta are call the *natural parameters* of the distribution, and u(x) is some function of x.
- The function g(\eta) can be interpreted as the coeffcient that ensures that the distribution is **normalized** and therefore satisfies: ~ where the integration is replaced by summation if x is a discrete variable.

##### 2.4.1 Maximum likelihood and sufficient statistics; 
##### 2.4.2 Conjugate priors
##### 2.4.3 Noninformative priors



## 2.5 Nonparametric Methods
the Parametric approach to density modelling:we use probability distributions having specific functional forms governed by a small number of parameters whose values *are to be determined* from a data set.

An important limitation of this approach is that: the chose density (eg.Gaussian, unimodal) might be a poor model of the distribution (eg.xx, mulitmodal) that generates the data, which can result in poor predictive performance.

nonparametric approaches to density estimation that make few assumptions about the form of the distribution.

Histogram methods for density estimation (modelling a distribution), which we have already encountered in the context of marginal and conditional distribution.

Standard histograms simply partition x into distinct bins of width $\Delta_i$ and then count the number $n_i$ of observations of x falling in bin i. 

$p_i=\frac {n_i} {N\Delta_i}$

- in order to turn this count into a normalized probability density, we simply divide by the total number N of observations and by the width $\Delta_i$ of the bins to obtain probability values of each bin given by: $p_i=$ ~ for which it is easily seen that $\int p(x)dx=1$
- One obvious problem is that the estimated density has A... Another major limitation of the histogram approcah is its B...  (A,B are the following Cons)

when \Detal is very small, the density model is very spiky, with a lot of structure that is not present in the underlying distribution that generated the data set;
too large, too smooth that consequently fails to capture the **bimodal** (2 Gaussians mixture) property of the green curve.
The best results are obtained for some intermediate value of \Delta (middle figure). 

Pro: 1) once the histogram has been computed, the data set itself can be discarded, which can be advantageous if the data set is large. -- **it is nonparametric, but also not memory based (Gaussian kernel estimation is).** 2)The histogram approach is easily applied if the data points are arriving sequentlly.

Con: 1)dicontinuities that are due to the bin edges rather than any property(mu var) of the underlying distribution that generated the data. 2) scaling with dimensionality. If we divide each variable in a D-dim space into M bins, then the total number of bins will be {M^D}. 

two lessons
1. to estimate the probability density at a particular location, we should consider the **data points lie within some local neighbourhood** of that point. (Note that the concept of locality requires that we assume some form of distance measure, and here we have been assuming Euclidean distance.)
2. the value of the **smoothing parameter** should be neither too large nor too small in order to obtain good results. 
(this is reminiscent of the choice of model complexity in polynomial curve fitting, or alternatively the value \alpha or the regularization parameter, was optimal for some intermediate value, neither too large nor too small)

--**Armed with these insights, we** turn now to a discussion of 2 widely used nonparametric techniques for density estimation, kernel estimators and nearest neighhours, which have better **scaling with** dimensionalty than the simple histogram model.

# 2.5.1 Kernel density estimators
$P=\int_\mathcal R p(x)dx$

$\mathbb E[K/N]=P$;  $var[K/N]=P(1-P)/N$

$p(x)\approx\frac K {KV}$;  $P\approx p(x)V$

$p(x)=\frac K{NV}$

$$ k(\mathbf u) = \left\{ \begin{array}{ll}
            1, & \quad |u_i|\leq 1/2, i=1,...,D \\
            0, & \quad otherwise
        \end{array} \right.$$
$\mathbf u= (\mathbf{x-x_n})/h$

$K=\sum_{n=1}^N k(\frac {(\mathbf {x-x_n})} n)$

$p(\mathbf x)=\frac 1 N \sum_{n=1}^N \frac 1 {h^D} k(\frac {(\mathbf{x-x_n})} h)$

$p(\mathbf x)=\frac 1 N \sum_1^N \frac 1 {(2\pi h^2)-^{1/2}}exp\{-\frac {\|\mathbf{x-x_n\|^2}} {2h^2} \}$

$$\begin{array}{ll}
            k(\mathbf u) & \quad \geq \quad 0 \\
            \int k(u)d\mathbf u, & \quad = \quad 1
        \end{array}$$

- some small region $\mathcal R$ containing $x$. The probability mass associated with this region (integral over this region) is given by: ~ the total K of points that lie inside R will be distributed according to the binomial(just for example) distribution :
- the mean fraction of points falling inside the region is:
- the variance around this mean is:
- For large N, this distribution will be *sharply peaked* around the mean and so:
- If, however (opposite to large N), we also assume the region R is *suffiently small* that probability density p(x) is roughly constant over the region, then we have:
- combine large N and small R (2 contradictory) assumptions, we obtain our density estimate (differnt with P of falling in a region) in the form p=K/NV:
    1. fix K and determine V --> K-nearest-neighbour technique
    2. fix V and determine K --> the kernel approach
- kernel (piece-wise function) in order to count the number of K of points falling within this region, it is convenient to define the following function: ~ which represent a unit cube centred on the orign.  
    - k(\bf u) is an example of a *kernel function*, and in this context is also called *Parzen window*.
    - (\bf u, the origin distance map to new D dimension or only stretch or fix. k of u: determine if its in on out based on {u_i}_{i=1}^D)
- the data x_n lies inside a cube of side h centerd on x.
- The total number of data points lying inside this cube will be therefor be:
- substituting this expression into p=K/NV then gives the estimated density at x: 
    - Using the symmetry of the function $k(\mathbf u)$, re-interpret this equation, not as a single cube centered on x but as the sum over N cubes *centred* on the N data and points x_n.
    - this estimator will suffer from one of the same problems that the histogram method sufferd from, namely the **presence of artificial discontinuties**, in this case at the boundaries of the cubes.
- We can obtain a smoother density model if we choose a smoother kernel function, and a common choice is the Gaussian, which gives rise to the following kernel density model:  ~ where h represents the standard deviation of the Gaussian components. 
    - our density model is obtained by *placing a Gaussian over each data point*, and then adding up the contributions over the whole data set
    - and then dividing by N so that the density is correctly normalized.
    - (to deal with the discontinuties of the k(\bf u) : we it close the point 1, far from 0, and exp(-x) is good and smooth! other parts are just for adding up and normalization).  recap: 1-D gaussian: $exp(-(x-u)^2/\2sigma^2)$  2-D gaussian: $exp((x-\mu)^T \Sigma^{-1}(x-\mu))$ if $\Sigma=diag(h^2)$
    - now h act as a smooth parameter. Like the $\Delta$ in histogram model, if h set too small, the result is a very noisy density model (spiky, not present in the underly distribution that generated dada), whereas if it is set too large, if fail to capture the binmodal distribution. (the binmodal nature of the underly distribution is washed out). The best density model is obtained for some intermediate value of h.    --- trade-off between sensitivity to noise at small h and over-smoothing at large h.
- any other function $k(\mathbf u)$ subject to the conditions: ~ which ensure that the resulting probability distribution is nonnegative everywhere and integrates to one.

now I know why the training of Kivi is slow: kernel has a great merit that the computaional cost of evaluating the density (kivi distance) grows linearly with the size of the data set.     Kernel method is a nonparametric approach (memory-based), a nerual network is a parametric approach (model-based), do you think combining them together is a good idea? 

what I concern is that: using kernel methods, there is no computation involved in training, because it simply requires storage of training data, but the computation of evaluating the density/distance for grow linearly with the size of training set.   Using network, although it needs training, the testing is quite swift as the computation only related to the trained parameters.  Combine them together, both merits disappear, there are only weaknesses of them. Any idea to address it?


##### question
1. bimodal, unimodal, multimodal?
2. what different between the kernel in Kernel density estimators and Gaussian kernel?
3. why binomail: fliping one coin N times.
    1. each data point has **a probability P of falling** with R, (all data points are/every data point is independent to each other), so the total number K of points that lie inside R will be distributed according to the binoimal distribution
4. ? what is that the distribution will be sharply peaked around the mean?   <-- sufficient large N that the number K of points falling inside the region is sufficient for the binomial distribution to be sharply peaked. 
5. ? why N suffient large to guarantee the binomial? 
6. converge to the true probability density in the limit $N\to\infty$ provided   V shrink suitably with N; and K grows with N. what is shirnk with and grow with ??
7. parzen window

##### new words


### new word
1. reminiscent
2. histogram [ˈhistəˌgram] program [O,o]
3. discontinuities [ˌdiskäntnˈ(y)o͞oitē]
4. Gaussian, Parzen [ˈpäzən], bayes, bayesian   [ˈbāzēən  ]
5. parametric, nonparametric [ˌnänparəˈmetrik]

illuminate[iˈlo͞oməˌnāt] =lighten, generality[ˌjenəˈralitē] =recap

same word different meanings: motivated from xx perspectives. property
proficient, manipulate:  become proficient in manipulating xx
geometrical form, functional dependence, quadratic [kwäˈdratik] form, Mahalanobis distance
ellipsoids[əˈlipsoid]: a three-dimensional figure whose plane sections are ellipses[əˈlips] or circles.


Bernouli, exponential; logarithm (algorithm,before Rithm, both a and o are light), denominator
Binomial, Multinoimal; lagrange (laGrange) multiplier (Oo,oo). dirichlet: (Oo k,let)
base, exponent








# 1024  GP<-Gassian Kernel;  EM<-exponential familiy<-PRML chapter2
GP: is about Gassian Kernel.

the gate has no analytical solution due to the non-linearity of softmax, so using Iteratively reweighted least squares(IRLS) in the EM iteration.  I don't know the indicator so I don't know the EM iteration here. 
1. reference 46, 4.3 is indicator
    1.  when the underlying complete data come from an exponential family whose maximum-likelihood estimates are easily computed, then each maximization step of an EM algorithm is likewise easily computed. --- MLE of exponential family distribution is easy!! what is exponential (PRML:probability distribution + generative model)

to avoid the inner loop iteration, Xu introduce an alternative gate function: I don't know why joint distribution can help get a analytical solution of the gate. 









