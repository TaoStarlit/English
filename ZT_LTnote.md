# PRML 2 Probability distribuion

# 2.1 binary variables
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
### writing
- the probability of x=1 will be denoted by the parameter \mu : where $..\geq..$
- the **probability distribution over x** can therefore be written in the form(exponential distribution): which is known as the Bernoulli distribution. 
- It is easily verified that this distribution is normalized and that it has mean and variance given by:
- observations are drawn independently from Bernouli distribution:
- we can estimate a value for mu by maximizing the likelihood function:
- or equivalently by maximizing the logarithm of the likelihood. The funtion is given by:
- we set the derivative of $\sum \ln p(\mathcal x_n|\mu)$ with respect to $\mu$ equal to zero:
- we obtain the maximum likelihood estimator:
### question
1. not Gaussian, why var?
   - ans: every distribution has variance. Suppose we have a data set $\{x_i,x_2,...x_N\}$ of observed values of x.  Then $\hat\mu=\sum_i x_I$ $\hat \sigma=\frac 1 N \sum_i (x_i-\hat x_i)^2$
2. why MLE of exponential family distriubtion is easy?
   - ans: MLE using logrithm and the logarithm is the inverse function to exponentiation. in the exponential family the x is in the exponent part, the estimated parameter is in the base part, so after logarithm, x became the coefficient of ln, and parameter is in the ln)
### new word
Bernouli, exponential; logarithm (algorithm,before Rithm, both a and o are light), denominator





# 1024  GP<-Gassian Kernel;  EM<-exponential familiy<-PRML chapter2
GP: is about Gassian Kernel.

the gate has no analytical solution due to the non-linearity of softmax, so using Iteratively reweighted least squares(IRLS) in the EM iteration.  I don't know the indicator so I don't know the EM iteration here. 
1. reference 46, 4.3 is indicator
    1.  when the underlying complete data come from an exponential family whose maximum-likelihood estimates are easily computed, then each maximization step of an EM algorithm is likewise easily computed. --- MLE of exponential family distribution is easy!! what is exponential (PRML:probability distribution + generative model)

to avoid the inner loop iteration, Xu introduce an alternative gate function: I don't know why joint distribution can help get a analytical solution of the gate. 









