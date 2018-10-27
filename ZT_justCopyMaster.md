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

$$ 
\begin{array}{lll}
    k(\mathbf{x,z})&=(\mathbf{x^Tz})^2\\
    &=(x_1z_1+x_2z_2)^2 \\
    &=x_1^2z_1^2+2x_1z_1x_2z_2+x_2^2z_2^2 &\quad(\phi(x)^T \phi(z))\\
    &=(x_1^2,\sqrt 2x_1x_2,x_2^2)(z_1^2,\sqrt 2z_1z_2,z_2^2) \\
    &=\mathbf{(\phi(x)^T \phi(z))}
\end{array} 
$$
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
   - Assume that psi is a mapping from X to a Hilbert space. Then there exists a vector $\mathbf\alpha\in\mathbb R^m$ such that $\mathbf w= \sum_{i=1}^m\alpha_i \psi(\mathbf x_i)$ is an optimal solution of Equation. 
   - from the repesenter therom: we know we aim to learn the w (parameter in the high dimension, from orignal to feature space), but we learn(optimaze) the alpha first, then w=s(alpha).  phi just a mapping, the w, the scalar multiplier of each dim need to be learning.

## new words 
1. induce: 
    - succeed in persuading or influencing (someone) to do something.
    - the pickets induced many workers to stay away
    - synonyms: persuade, convince, prevail upon, get, make, prompt, move, inspire, influence, encourage, motivate, coax into, wheedle into, cajole into, talk into, prod into, twist someone's arm
    - bring about or give rise to.
    - none of these measures induced a change of policy
    - synonyms: bring about, cause,

## 6.4 Gaussian Processes
here we extend the role of kernels to probabilitic discriminative models, leading to the framework of Gaussian process.

At first sight: difficult - distribution over the uncountably infinite space of functions. Howerver, as we shall see: finite training set - we only need to consider the values of the functions.


### link 
1. chapter 3: regression model
    - prior / posterior in turns
### word
1. isotropic  [īsəˈträpik]
    - (of an object or substance) having a physical property that has the same value when measured in different directions.
    - Because the bonds are not symmetrical, glass is isotropic and has no definite melting point.