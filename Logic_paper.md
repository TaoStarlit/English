## Progressive Stochastic Learning for Noisy Labels
1. from the reliable lables to the noisy sample.
    1. curriculum: calculate the score of every observations
    2. if is above the threshold, using it to update the weight variable
    3. update the threhold, repeat
1. is there the problem of above basic method, in fact, no! but from machnisam to realization, need define now losses:
    1. a cluster of bounded loss: sequanced from reliable region to noisy region
    2. in the noisy region the gradient of losses is zero -- resist the adverse effect of noisy sample
1. can we use the machinism algorithm directly?
    1. what is the update f I,II and the compute Q I, Q II. update Q I Q II?
        1. Qs are gradients, update is get new weight variables. so the problem is the f I, II
        2. $\alpha, \beta$ is the parameters of the screen losses. 
        3. G is Globle ERM (Empirical risk minimization);  g is instance-wise error; 
            1. The Augmented Restriced Strong Convexity is give a parameter $alpha$, the difference of extrapolation $G(w)$ and $G(\tilde w)$, and the gradient descent are less then L2 of point $w$ and point $\tilde w$
            2. the Augmented Restricted SMoothness, replace G as g.  
            3. convexity is the optimization level of whole problem. SMooth is only on instance level, to test whether $g_i(w) - g_i(\tilde w) - <\nabla g_i(\tilde w), w-\tilde w> \leq \frac \beta 2\|w-\tilde w\|^2$ 
        4. Augmented Restricted SMoothness and Augmented Restricted Strong Convexity are only the conditions. now we need the loss function meet these two conditions.
        5. I , II is using loss 1 or loss 2, both of them satisfy the ARSC and ARSM
    2. using the ARSM, get an inequation : $\mathbb E[\|w^{(t)}-w^*\|^2]\leq ... G(w^{(t-1)}) , G(w)^*$.  and then Bregman divergence generator.  $D_F(p,q)=F(p)-F(q)-<\nabla F(p), p-q>$  , easy (the tanent at $x_0$ and $f(x_0)$ )https://en.wikipedia.org/wiki/Bregman_divergence
    3. the experiment: 3 baseline:  not POSTAL but same loss function -- verify the effectiveness of the mechanism; not POSTAL not loss function -- effectiveness and robustness; uSGD -- robustness?
   


### write the paper:
#### abstract
1. problem & current situation
2. what is wrong in the existing methods  -- (remind me of the meta-review of our paper : the reviewer said the idea of systhetic image is well-known.   
3. specifically what is wrong, in what situation and progress: SGD.
4. now it is what we do: new mechanism, of robust SGD, named POSTAL, integrade CL with vanilla SGD -- it is also explicitly mention a well-known term what is that to make it clear, whichis like what i did previously.   is it different from the way I mentioned CVAE? 
5. what is the inspiration: from progressive process, namely  easy-complex tasks.
6. the inspiration maps to our idea -- this also show the difference: from easy to complex task --> reliable to noisy labels. 
7. now from the idea (how to solve the what wrong in the existing technique) level,  
 maps to the implementment level (design loss, which + the purpose. --- only one point, but it is probably OK)
8. sum up: the general procedure of training, key progress and when is finished. 
9. theory contribution 1: derivation the convergence rate
10. meanwhile+theory contribution 2: robustness analysis 
11. experimental result on UCI + Amazon data
(abstract -- half a page)

#### Introduction:   eg. 21 means 2nd paragraph, 1 sentence
11. the problem, exist situation(use a method). show 2 reasons  (avoid repeating the sentence from abstract).
12. The instance of reason 1, give the reference (the existing method is good to some extent).
13. reason 2, example 2
14. in this situation. What is wrong and give evidence(reference)  (Step into result and lead a key technique SGD) 
15. the wrong from the situation degenerate the technique of SGD.
- (how to avoid repeating the sentence in abstract -- give more reason/process. one sentence -> two sentence)
21. what is the SGD:  prevalent, and show the reason why it is prevalent: 2 merits
22. reasoning and make claim about the chanllenge using this technique(SGD)
- (the avoid line is data from crowdsouring; what is wrong; degenerate the performance of opt, including SGD; What is SGD, how it is degenerated) 
31. what we do:  to address, we introduce xx, called xx, that integrates xx and xx (map to our paper: imbalanced problem, reason, what is wrong, analysis and show the chanllenge) 
32. generally how it comes from: our inspiration springs from xx, namely .._easy to understand term_..
33. what is the aim to do in our method ... sequence lable
34. implement: to provide this (sth about the aim), we design a xx loss. 
35. sum up the procedure again: first, subsequent epoches
36. contribution 1)I36: contribution 1)mechanism 2)loss function 3)convergence/robustness +   I37:organization of the paper
- (my first time to understand what are contributions: a mechanism idea; the key implement; the key thoery analysis. These are high depenpent, not just put/knocked together)  -- introduction less than 1 page
#### related work
1. 11-15. the existing technique(SGD); eg. as application; variants; but have some problem: strong assumption of free of noise;
2. 21-23. the techniuque that give inspiration(CL); how it work; but, this technique has not been applied into the update process of SGD for noisy labels. R24: claim the novelty using this inspiration
3. 31-33. what is related to the loss function(contribution 2) in the implement part
4. 41-44. other works deal with the problem noisy label: 1 2 3 4 has deficiency. not SGD(didn't put them in the basic line)
#### PrOgressive STochAstic Learning
O. how organize the writing about our method: prelimianry notations; mechanism; realization: design losses; derive the convergence rate; analyze the robustness
A. Preliminary notations
B. Mechanism: contribution one
1. MB1 from real-world application, the issue inevitably degenerate the performance of conventional SGD.
2. MB2: what motivate our method: CL    (remind me, the mechanism is inspired by the ada-boost --but boost is imbalanced learning, choosing sample?? no)
3. MB3: a very good interpretation: me too, (learn and check and generalization): reading,(get the class) rewrite. check whether it is remain the same class: if not read more sample the same class and motify writing, writing and check.   -- article is not code, you should make article clear at the first time, even code should has a very clear logic. 
4. MB4(next paragraph): name + incorporate/combine exsting techniques
5. M5: detail: "noisy" using "Double quotes" is inviting the reviewer to ask you how to define "noisy".  Therefore, it is followed fig, and explanation
6. M6: (np)use the fig, write the detail, answer the term "noisy"
7. MB7: (def)definition key metric: curriculum
8. MB8: (remark)after definition, remark the how to use the defined metric
9. MB9: (np)whole process, subtitude the metric(curriculum) into the previous notation/equation in MA
10. M10: again "reliable" double quote raises attention and then is followed by a solution: gradually reduce the dynamic therhold
11. M11:(alg) use remark2 to point out the important point in the algorithm. previously, remark1 is important definition
    1. In MB remark 2 r1: two key steps
    2. r2: here outline the difference with SGD (sequently vs randomly)  me originally vs in the latent space
    3. r3: for simplicity, SVM as classification.   what if to compare with complex baseline  -- see last experiment
    4. r4: I can realize in deep learning: good.  --( my model can use SVM in UCI data set. and more simple synthetic data)
    5. r5: based on same principle, so it also can use in xxx

C. Realization: contribution two
0. MCO: from machnism to realization,( is similar to  from framework to implement in our paper)
1. MC1: to realize to design a cluster of bounded losses
    1. 1 ordered label sequence;
    2. bounded->non-convex  when minimizing the adverse effect
2. before deling into a cluster of screening losses:  two foundation def, and two augmented defs. -- (I find it is augmented or Increment)
3. MC3: def of the screening loss, the conditions
4. MC4: remark 3 illustrate the above conditions in details
5. MC5: we present two screen losses
6. MC6: upgrade version of the algorithm 1 -- new loss function, and using Ball,   c, a, parameter
7. MC7: summary of what screening loss serve as ...

D. Analysis: contribution three -- currently, it probably difficult for me, maybe prepared it the paper in 3rd year or last year of PhD.

... ...

#### Experiments
....

question: 
1. Is it SGD $w^{(k)}=w^{(k-1)}-\eta g(x_i)$, one iteration one sample
    1. average/sum gradient descent: evaluating the sum-gradient may require expensive evaluations of the gradients from all summand functions;  $w:=w-\eta\nabla Q(w)=w-\eta\sum_{i=1}^n\nabla Q_i(w)/n$; 
    2. stochastic gradient descent:  the true gradient of $Q(w)$ is approximated by a gradient at a single example: $w:=w-\eta\nabla Q_i(w)$. 





