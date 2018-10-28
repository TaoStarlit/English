# what kernel method is all about:


# 6 Kernel Method
GP is in Chapter 6 Kernel Mthods

###### question
1. why it is name kernel function.
   - ans: in the density estimation, k(u)=k(x,u), u is the centrel point of the cube/kernel, (kernel means to fix V and determine K), k(u) return whether x is in the cube u. Gaussian kernel, a smooth version to quentify, closeness between point (summation is to add up all the contribution of each point). So kernel  return a scalar the closeness between to point. eg. 1 in, 0 out.  large close, small far.  
1. why $phi(x)$ is mapping in $k(x,x')=\phi(x)^T\phi(x)$?
    - ans: let say mapping is identical or mirror. Then $x^T x$ is inner product. When x x' the same, large; orthrinal, 0; opposite, mimus. (we shall refer to this as the linear kernel) When it a mapping, then is the inner product after mapping. 
1. what is the basic regression function with regulation? why using kernel here?
    - ans: 3th chapter
1. new concepts list: memory-based method; kernel function; feature space; support vector machines; kernel trick/kernel substitution; stationary kernels; homogeneous kernels/radial basis functions(RBF,Gaussian);  6.1: design matrix(phi x); dual representation(obtain solution a, not w, w=phi^T a; phiK^phi=K); Gram matrix; valid kernel

kernel and the mapping, from A to B, also B to A
$$ 
\begin{array}{lll}
    k(\mathbf{x,z})&=(\mathbf{x^Tz})^2\\
    &=(x_1z_1+x_2z_2)^2 \\
    &=x_1^2z_1^2+2x_1z_1x_2z_2+x_2^2z_2^2 &\quad(\phi(x)^T \phi(z))\\
    &=(x_1^2,\sqrt 2x_1x_2,x_2^2)(z_1^2,\sqrt 2z_1z_2,z_2^2) \\
    &=\mathbf{(\phi(x)^T \phi(z))}
\end{array} 
$$

dual representation:  (here we consider a liear regression model whose parameters are determimed by minimizing a regularized sum-of-squares error function given by):
$J(\mathbf w)=\frac 1 2 \sum_{n=1}^N\{{\mathbf{w^T\phi(x_n)}-t^n}\}+\frac\lambda 2 \mathbf{w^Tw}$

where $\lambda\geq 0$. If we set the gradient (1/2 is convinient to calculate the derivative) of J(\bf w) with respect to \bf w equal to zero, we see that the solution for w takes the form of a linear combination of the vectors $\phi(x_n)$, with coefficients that are functions of w, of the form: $\mathbf w=- 1 \lambda \sum_{n=1}^N\{\mathbf{w^T\phi(x_n)}-t_n\}\mathbf{\phi(x_n)}=\sum_{n=1}^Na_n\mathbf{\phi(x_n)}=\mathbf{\Phi^T a}$

where $\mathbf \Phi$ is design matrix, whose $n^{th}$ row is given by $\phi(\mathbf x_n)^T$. Here the vector $a=(a_1,...,a_N)^T$, and we have defined:
 $a_n=-\frac 1 \lambda \{\mathbf{w^T\phi(x_n)}-t_n\}$
instead of working with the parameter vector w, we can now *reformulate* the least squares algorithm in term of the papameter vector a, giving rise to a dual representation. If we subsititute $\mathbf{w=\Phi^T a}$, we obtain: ...
where $\bf t$ is the observation of t. Gram matrix $\bf{K=\Phi\Phi^T}$, which is a NxN symmetric matrix with elements $K_{nm}=\mathbf{\phi(x_n)^T\phi(x_m)}=k(\mathbf{x_n,x_m})$

In terms of Gram matrix the sum-of-squars error function can be written as:
$J(\mathbf a)=\frac 1 2 \mathbf{a^TKKa}-\mathbf{a^TKt}+\frac 1 2 \mathbf{t^Tt}+\frac \lambda 2 \mathbf{a^TKa}$
Setting the gradient of J(\bf a) with respect to a to 0, we obtain the following solution $\bf a=(K+\mathit \lambda I_N)^{-1}t$
then we subsititude this back into the linear regression model, we obtain the following prediction for a new input x: $y(\bf x)=w^T\phi(\mathbf x)=a^T\Phi\phi(x)=k(x)^T(K+\lambda I_N)^{-1}t$, where we have define the vector k(x) with element k_n(x)=k(x_n,x) -- one n-th row of Gram matrix



we see the feature mapping takes the form $\mathbf{\phi(x)}=(x_1^2,\sqrt 2x_1x_2,x_2^2)^T$

we need a simple way to test whether a function constitutes a valid kernel without having to construct the feature mapping function explicitly.  **A necessary and sufficient condition** for a function k(x,x') to be a valid kernel is that the Gram matrix K, whose elements are given by k(x_n,x_m), should be posive semidefine for all possible choices of the set {x_n}.

### Gaussian kernel:
in this context it is not interpreted as a probability density, and hence the normalization coefficient is omitted. $k$


# gaussian kernel --> gaussian process

$k(\mathbf{x,x^\prime})=\exp(-\|\mathbf{x-x^\prime}\|^2/2\sigma)$

$\|\mathbf{x-x^\prime}\|=\mathbf{x^Tx}+(x^\prime)^T x^\prime-2x^T x^\prime$

$k(\mathbf{x,x^\prime})=\exp(-\mathbf{x^Tx}/2\sigma^2)\exp(-x^T x^\prime/\sigma^2)\exp(-(x^\prime)^T x^\prime/2\sigma^2)$

$k(\mathbf{x,x^\prime})=\exp\{-[k(x,x)+k(x',x')-2k(x,x')]/2\sigma^2\}$


$k(A_1, A_2)=2^{|A_1 \cap A_2}|$


$k(x,x')=p(x)p(x')$

$k(x,x')=\sum_i p(x|i)p(x'|i)p(i)$

$k(x,x')=\int p(x|z)p(x'|z)p(z)dz$

$k(X,X')=\sum_z p(X|Z)p(X'|Z)p(Z)$



- gaussian kernel
- why it is valid kernel: constructing new ker
- 
- new valid kernel come from from simple valid kernel

- replace the simplest linear kernel with nonlinear kernel k
- extention to inputs that are symblic, rather than simply vectors of real numbers. Kernel functions can be defined over objects as diverse graphs, sets, strings and text documents. eg: ~ where xx denotes the intersection of sets A1 and A2, and |A| denotes the number of subset in A.
- given a generative model p(x) we can define a kernel by: ~ we can interpret it as an inner product in the 1-D feature space defined by the the mapping p(x). 
- consider sums over products of different probability distributions, with positive weighting coefficients p(i), of the form: ~ this is equivalent, up to an overall multiplication constant, to a mixture distribution in which the components factorize, with the index i playing the role of a latent variable.
- a popular generative model for sequence is the hidden Markov model, which express the distrbution p(X) as a marginalization over a corresponding sequence of hidden states Z. Here, we can use this approach to define a kernel function measuring the similiarity of 2 sequences X and X by extending the mixture representation to give:


### conclusion of 6.2
in the limit of an infinite number of basis functions, a Bayesian neural network with an appropriate prior reduces to a Gaussian process, thereby providing a deeper link between neural networks and kernel methos. 

###### question
1. what is the advantage of k(x|x') compared to p(x)? 
2. Fisher kernel, fisher score, fisher information matrix -- how to link neural network and kernel methods?
   - using generative models to define kernel functions -- fisher kernel.  the goal is to find a kernel that measures the similarity of two vectors x and x' induced by the generative model.   
3. the purpose and usage of kernel function. 
   - simply the computation  -- UDML

# UDML Kernel methods
1. Embbedding into feature spaces
   - eg. |x|>2 y=1; others y=0; mapping: $\psi:\mathbb {R \to R^2}$, $\psi(x)=(x,x^2)$, then linearly separatable. We get w and b
   - VC-dimension increase -- need more samples
   - performing calculations in the high dimensional space might be costly.
2. the kernel trick:
   - inner product in the feature space, $K(x,x')=<\psi(x),\psi(x')>$
   - one can think of K as specifying similarity between instances and of the embedding \psi as mapping the domain X into a space where these similarities are realized as inner produces.
   - ... without having to specify points in that space or expressing the embedding psi explicitly.
   - repesenter therom: Assume that psi is a mapping from X to a Hilbert space. Then there exists a vector $\mathbf\alpha\in\mathbb R^m$ such that $\mathbf w= \sum_{i=1}^m\alpha_i \psi(\mathbf x_i)$ is an optimal solution of Equation. 
   - from the repesenter therom: we know we aim to learn the w (parameter in the high dimension, from orignal to feature space, w\psi is the predictive function), but we learn(optimaze) the alpha first, then w=s(alpha).  phi just a mapping, the w, the scalar multiplier of each dim need to be learning.

## new words 
1. induce: 
    - 1) succeed in persuading or influencing (someone) to do something.
    - the pickets induced many workers to stay away
    - synonyms: persuade, convince, prevail upon, get, make, prompt, move, inspire, influence, encourage, motivate, coax into, wheedle into, cajole into, talk into, prod into, twist someone's arm
    - 2) bring about or give rise to.
    - none of these measures induced a change of policy
    - synonyms: bring about, cause,

## 6.4 Gaussian Processes
#### 6.4.1 revisit regression
#### 6.4.2 gaussian processes for regression
here we extend the role of kernels to probabilitic discriminative models, leading to the framework of Gaussian process.

At first sight: difficult - distribution over the uncountably infinite space of functions. Howerver, as we shall see: finite training set - we only need to consider the values of the functions.

$y(\bf w)=w^T\phi(x)$

$p(\mathbf w)=\mathcal N(\mathbf{w|0}, \alpha^{-1} \mathbf I)$

$\bf y=\Phi w$

$E[y]=\Phi E[w]=0$

$cov[y]=E[yy^T]=\Phi E[ww^T]\Phi^T=\frac 1\alpha \Phi\Phi^T=K$

$K_{nm}=k(x_n,x_m)=\frac 1\alpha \phi(x_n)^T \phi(x_m)$

- consider a model defined in terms of a linear combination of M fixed basis functions given by the elements of the vector $\bf\phi(x)$ so that: ~ where x is the input vector and w is the M-dimension weight vector.  --? is the basis functions feature mapping?  --- w: Y-D --> M:D? wrong, it is phi that mapping; w just weighted vector.

- joint distribution over N variables y... is specified completely by the second-order statistics, namely the mean and the covariance.


#### 6.4.2 GP for regression

### question:
1. in gaussian kernel, the feature space has infinite dimensions, is there w of infinite? $\bf y=\Phi w$ .and what is the final preditive function y(x)?
   - ans: using dual representation. it is no need to calculate in the high(infinite dimension),but $\bf a$(N-dimension), and design matrix(N*M-dim, M is feature space); finally there are only $K(=\Phi\Phi^T)$ and k $\Phi$, i.e. $y(\mathbf x)=\mathbf{w^T \phi(x)}=\bf a^T\Phi\phi(x)=k(x)^T(K+\lambda I_N)^{-1}t$ if different observation, then $\bf y=\Phi w$, N_M M_1 =>N_1.
   - the PRML interpreation: /bf y is a linear combination of Gaussian distributed variables given by the elements of \bf w and hence is itself Gaussian.
2. what is the joint distribution means? here prior distribution $w$, and $\bf y=\Phi w$.  
   - ans: joint distribution means all the y elements:  the joint distribution over N variables $y_1, y_2, .. y_N$



### link 
1. chapter 3: regression model
    - prior / posterior in turns
1. 2.3.3 linear-gaussian model
### word
1. isotropic  [īsəˈträpik]
    - (of an object or substance) having a physical property that has the same value when measured in different directions.
    - Because the bonds are not symmetrical, glass is isotropic and has no definite melting point.
2. joint distribution of {X_t}_{t=1}^T, all X_t is in the common probability space $(\Omega,\mathcal F,P)$. Is the continuous space the t=1...N, or the out put of X, i.e the R of $P:\mathcal F \to \mathbb R$?  choose A or B??

##### marginal probability:
These concepts are "marginal" because they can be found by summing values in a table along rows or columns, and writing the sum in the margins of the table.

|notation|name|how|eg
|--|--|--|--|
|$\phi$|feature mapping|$\mathbb{R^D\to R^M}$|$x\to (x,x^2)$
|$\bf w$|weighted vector|linearly separate/regression in $\mathbb{R^M} space$| $argmin_{\mathbf w}\sum_{n=1}^N(\mathbf w^T\phi(x_n)-t_n)^2+R(\mathbf w)$
|$\bf \Phi$|design matrix|$\phi(x_n)^T$ is the n-th row|




关键词：连续域，正态分布，多元正态分布。

什么是高斯过程？简单的说，就是一系列(t=1...T)关于连续域R时间或空间）的随机变量的联合，而且针对每一个时间或是空间点上的随机变量都是服从高斯分布的。

A Gaussian process on a set T is a collection of random variables X = (Xt)t∈T on a common probability space such that for any n ≥ 1 and any t1,...,tn ∈ T, the vector (X(t1),...,X(tn)) has a normal distribution.
The joint distribution of X is determined by the mean function t → E[X(t)] and the covariance kernel K(t,s):=Cov(X(t),X(s))

http://math.iisc.ernet.in/~manju/GP/5-Gaussian%20process%20defn%20and%20examples.pdf
(a probability space: sample space, a set of events, assigment of probablity to to events.)

https://en.wikipedia.org/wiki/Sigma-algebra
understand what is field means in sigma-field.


1. $\sigma$-algebra:

(a field on a set   is   a collection of subsets of set)
a σ-algebra (also σ-field) on a set X is a collection Σ of subsets of X that includes the empty subset, is closed under complement, and is closed under countable unions and countable intersections. The pair (X, Σ) is called a measurable space or Borel space.


The main use of σ-algebras is in the definition of measures; specifically, the collection of those subsets for which a given measure is defined is necessarily a σ-algebra. 

Let X be some set, and let {\displaystyle {\mathcal {P}}(X)} {\mathcal {P}}(X) represent its power set. Then a subset {\displaystyle \Sigma \subseteq {\mathcal {P}}(X)} {\displaystyle \Sigma \subseteq {\mathcal {P}}(X)} is called a σ-algebra if it satisfies the following three properties:[3]

#### definition of sigma-algebra:
1. 
Let X be some set, and let  ${\mathcal {P}}(X)$ represent its power set(set of all subsets of X). Then a subset $\Sigma \subseteq \mathcal {P}(X)$ is called a σ-algebra if it satisfies the following three properties:
1. X is in Σ, and X is considered to be the universal set (a set which contain all objects) in the following context.
1. Σ is closed under complementation: If A is in Σ, then so is its complement, X \ A.
1. Σ is closed under countable unions: If A1, A2, A3, ... are in Σ, then so is A = A1 ∪ A2 ∪ A3 ∪ … 

##### GP and regression
https://zhuanlan.zhihu.com/p/31203558