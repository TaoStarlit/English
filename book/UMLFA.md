# Unit
## date and section
- the original text
    1. new word: pronunciation in phonetic symbols
        - explanation
        - example sentence
        - your sentence
        - compared word
- your compared word list
    1. the word
        - explanation
        - example sentence
        - your sentence
- grammar, terminology, word formation

# timetable
- 20181002 read 1.1-1.3; 1003, writedown the new words
- 20181003 read chapter 5: link in 1.1 the stronger prior, the easier it is to learn, but the less flexible the learning is -- it is bound, a priori, by the commitment to these assumptions
- 20181005 read the chapter 2: to figure out what is $\delta, \epsilon$. The former one is probability of getting a nonrepresentive sample, the latter one is the about the True Loss, we will discuss in Chapter 3 PAC.
- 20181007 read the chapter 7 VC dimension: about the infinite hypothesis is also PAC learnable. the chapter 4: uniform convergence, also dicusses about the sample complexity. figure what does the first 6 chapters discuss about:
## recap
  1. Introduction: explains the meaning of learning, gives classical example, mentions: bias, prior knowledge (Unit 2-8 are theory fundations, then is from theory to algorithms) 
  2. A Gentle Start: gives the statistical learning framework. 
      1. notation of statistical leanring
      2. empirical risk minimization, overfitting
      3. Inductive Bias, finite hypothesis classes: Union Bound
  3. A Formal Learning Model
      1. PAC Learning:
      2. releasing the realizability assumption - Agnostic PAC Learning. The Scope of Learning Problem Modeled (other learning beyond binary classification)
  4. Learning via Uniform Convergence
      1. Uniform Convergence is Sufficient for learnability
      2. Finite Classes Are Agonostic PAC Learnable
  5. The Bias-Complexity Tradeoff
      1. The No-Free-Lunch Theroem prior knowledge(prevent the learning failures, can be expressed by restricting our hypothesis class)
      2. Error decomposition: approximation error ($\min_{h \in \mathcal H}L_\mathcal D (h)$, determined by the hypothesis class chosen) & estimation error($S$, $\mathcal D$, depends on the training set size).
  6. The VC-Dimension
      1. Infinite-Size Classes Can Be Learnable (chapter 4: finite classes, and sample complexity is upper bounded by the log of the size the finite hypothesis class)
      2. The VC-Dimension
      3. Examples: Threshold Functions; Intervals; Axis Aligned Rectangles; Finite Classes; VC-Dimension and the Number of Parameters
      4. The Fundamental of Theorem of PAC Learning
- 20181012 Seach the EM, so read Unit 24 Generative Models
    1. model the data distribution with a specific parametric form, and our goal is to estimate the parameters of the model
    2. 24.1 MLE: Maximum Likelihood Estimator.  eg. $\hat \theta$ is an unbiased estimator or an MLE (different interpretation)
      1. for continuous Random Variables
      2. ML and Empirical Risk Minimization
      3. Generalization Analysis -- measure how good is the MLE
    3. 24.2 Naive Bayes -- simplify the Bayes optimal classifier. eg. $2^d$ parameters to $2d+1$ parameters.
    4. 24.3 Linear Discriminant Analysis   

- important word: agonostic, suffice, Therome, definition, lamma, corollary  - today 3,4,5, 6 new word! --- 1-6 what is PAC learning
- important example: the infinte hypotheses in VC - unit
- important equation/notation: the $\mathcal D^m$ function
- important inequation of proof: $1-\epsilon \leq e^{-\epsilon}$

## important definitions:
- 2.3 Definition 2.1 The Realizability Assumption: There exists $h^* \in \mathcal H$ s.t. $L_{(\mathcal {D,f})}(h)=0$. It **implies**: with probability 1, $L_S(h^*)=0$
- 2.3 Inductive bias: the search space is restricted, that is we bias learner toward a particular set of predictors. Such restriction often called an inductive bias
- 3.1 PAC Learnability: ... if realizable assumption holds with respect to $\mathcal{H,D,f}$, then $m\geq m_{\mathcal H}(\epsilon, \delta)$ i.i.d. examples genearate and labeld by $\mathcal {D, f}$, the algorithm returns a hypothesis h such that, with probability of at least $1-\delta$ (over the choice of the examples), $L_{(\mathcal{D,f})}(h)\leq \epsilon$. 
- 3.2 the sample complexity of PAC learnable finite hypothesis classes. The log of its size. 
- 3.3 Agnostic PAC Learnability: (not $\mathcal {D,f}$, but $\mathcal {X \times Y}$) ... at least  $1-\delta$ (over the choice of the examples), $L_{(\mathcal{D})}(h)\leq \min_{h\prime in \mathcal H}L_{mathcal D)(h\prime)+\epsilon$. -- if the realizability assumption holds ($L_{(\mathcal {D,f})}(h)=0$),  agnostic PAC learning provides the same guarantee as PAC learning.  
- 3.4 Agnostic PAC Learnability for General Loss Functions: ... loss function $l:\mathcal{H \times Z} \to \mathbb R_+$  ($Z=\mathcal{X \times Y}$) ...
- 3.2 Remark 3.1 ... $l(h,.): Z\to \mathbb R_+$ is measurable. Formally, we assume that there is a $\sigma$-algebra of subsets of Z, over which the probability $\mathcal D$ is defined, and that the preimage of every initial segment in $\mathbb R_+$ is in this $\sigma$-algebra
- 3.2 Remark 3.2 Proper versus Representation-Independent Learning: the algorithm return a hypothesis but not from $\mathcal H$
- 4.1 Definition 4.1 $\epsilon$-representive sample: A training set $S$ is called ~, if $\forall h \in \mathcal H, |L_S(h)-L_\mathcal D (h)| \leq \epsilon$
- Lemma 4.2 a training set is $\frac \epsilon 2 - representative$, then it satisfies agonotic learnable $L_\mathcal D(h_S)\leq \min_{h\in \mathcal H} L_\mathcal D (h) + \epsilon$
- definition 4.3 Uniform Convergence: We say a hypothesis class $\mathcal H$ has the uniform convergence property if ..., then with the probability of at least $1-\delta$, S is $\epsilon$-representive. 

# Unit 4 Learning via Uniform Convergence
## 4.1 Uniform Convergence Is sufficient for Learnability
- For that($min L_S(h)$ also $min L_\mathcal D(h)$), it suffices to ensure that the empirical risks of all members of $\mathcal H$ are good approximations of their true risk (which is quivalent to $\mathcal H$ has uniform convergence property).
  1. suffice [səˈfīs]
   - be enough or adequate. 
   - a quick look should suffice. this is ~ for that.
   - synonyms: be enough, be sufficient, be adequate,
## 4.2 Finite Classes Are Agnostic PAC Learnable
- However, since the law of large numbers is only an asymptotic result, it provide no information about the gap between the empirically estimated error and its true value for any given, finite, sample size.
  1. asymptotic(,Oo O-tic) means approaching a value or curve arbitrarily closely (i.e., as some sort of limit is taken). 
## summary: 
Uniform convergence suffice for agnostic PAC learnability using the ERM rule. We have shown that finite hypothesis classes enjoy the uniform convergence property and are hence agnostic PAC learnable.

# Unit 3 A Formal Leaning Model
## 3.0 the PAC leaning model
- Therome: lemma -> ~ -> corollary
  1. theorem [ˈTHēərəm]
   - a general proposition not self-evident but proved by a chain of reasoning; a truth established by means of accepted truths.
   - Ideally the definitions would generate all the concepts from clear and distinct ideas, and the proofs would generate all the theorems from self-evident truths.
  2. lemma [ˈlemə]
   - a subsidiary or intermediate theorem in an argument or proof. 
   - It takes a long series of lemmas to show how powerful the primitive recursive functions are.
  3. corollary [ˈkôrəˌlerē]
   - a proposition that follows from (and is often appended to) one already proved.
   - For these angles, the contradiction used to prove the corollary does not arise.
  4. definition [ˌdefəˈniSHən]
   - a statement of the exact meaning of a word, especially in a dictionary.
   - The Judge said she had, in the absence of any statutory definition, consulted several dictionaries for a definition of the word record.
## 3.1 PAC Learning
- definition 3.1 PAC learnability
- corollary 3.2 finite hypothesis class is learnable with sample complexity $m_{\mathcal H(\epsilon, \delta)}\leq \left[\frac {\log(\mathcal H / \delta)} \epsilon \right]$
- later on we will show that what determines the PAC learnability of a hypothesis class is not its finiteness but rather a combinatorial measure called the VC dimension.
  1. combinatorial [ˌkäm bə nə ˈtȯr ē əl]
   - of or relating to the arrangement of, operation on, and selection of discrete mathematical elements belonging to finite sets or making up geometric configurations.
## 3.2 A More General Learning Model
- we will describe the agnostic PAC model in which this realizability assumption is waived.
  1. waive [wāv]
   - refrain from insisting on or using (a right or claim).
   - he will waive all rights to the money 
   - synonyms: relinquish, renounce, give up, 


# Unit 2 A Gentle Start
## 2.0 20101005 no new word, by I list the difficulty in this chapter:
- what is the meaning of the distribution function of training set.  $\mathcal D(A\cup B)\leq \mathcal D(A) + \mathcal D(B)$.  Can it be equivilent to the $P(A\cup B) \leq P(A)+P(B)$ ? 
- what is the meaning of $\mathcal D^m$. I know $m$ is the size of training set.  
    - ans: in page 38, i.i.d.(The examples in the training set are **independently and identically distributed** according to the distribution $\mathcal D$) assumption. $\mathcal D^m$ denotes the probability over $m$-tuples induced by applying $\mathcal D$ to pick each element of the tuple independently of the other members of the tuple.
## 2.1 A Formal Model - The Statistical Learning Framework (Links and corresponding meaning in 5.1)
## 2.2 Empirical Risk Minimization
- 2.2.1 Something May Go Wrong - Overfitting: Although the ERM rule seems very natural, without being careful, this approach may fail miserably. To demonstrate such a failure, let us go back to the problem of learning to predict the taste of a papaya on the basis of its softness and color. Consider sample as depicted in the following figure..
  1. miserable [ˈmiz(ə)rəbəl]
   - (of a person) wretchedly unhappy or uncomfortable.
   - their happiness made Anne feel even more miserable
   - synonyms: unhappy, sad, sorrowful, dejected, depressed, downcast, downhearted, 
  2. depicted [diˈpikt]
   - show or represent by a drawing, painting, or other art form.
   - The four-metre wide painting depicts a typical Lowry scene of Victorian life in a northern cotton town.
   - synonyms: portray, represent, picture, illustrate, delineate, reproduce,
- portray [pôrˈtrā], portrayal
  1. portrayal [pôrˈtrā(ə)l]
   - Kenny Ho has obtained a great level of fame in the Asian community for his portrayal as Zhan Zhao (展昭) in the 1993 Taiwanese television series Justice Bao.
   - a depiction of someone or something in a work of art or literature.
   - a realistic portrayal of war
   - synonyms: painting, picture, portrait, drawing, sketch, representation,

- we show a natural representation of it using polynomials.
  1. polynomial [ˌpäləˈnōmēəl]
   - an expression of more than two algebraic terms, especially the sum of several terms that contain different powers of the same variable(s).
   - The papers look at algebraic curves, the Riemann Roch theorem and algebraic polynomials.
   - nomial, polygon
- polygon, numerator (numerous, but numeric oOric), denominator, fraction
  1. polygon  [ˈpäliˌgän]
   - a plane figure with at least three straight sides and angles, and typically five or more.
   - For purposes of clarification: a hexagon is a polygon with six sides and six angles.
  1. numerator [ˈn(y)o͞oməˌrātər]
   - the number above the line in a common fraction showing how many of the parts indicated by the denominator are taken, for example, 2 in 2 / 3.
   - To convert a fraction to a percentage, divide the numerator by the denominator.
  1. denominator [diˈnäməˌnātər]
   - the number below the line in a common fraction; a divisor.
   - If you calculate the divergence for different species of plants, you find that both the numerator and the denominator are usually Fibonacci numbers.

## 2.3 Empirical Risk Minimization with Inductive Biasgt
$\mathcal D^m$ denotes the probability over $m$-tuples induced by applying $\mathcal D$ to pick each element of the tuple independently of the other members of the tuple.
  1. tuple:  set of (so many) elements —usually used of sets with ordered elements
  1. induce: [inˈd(y)o͞os]  促使, 感应, 引出
   - succeed in persuading or influencing (someone) to do something.
   - the pickets induced many workers to stay away
   - synonyms: persuade, convince, 
   - derive by inductive reasoning.
   - Moreover, Galileo approved Aristotle's position that explanatory principles must be induced from the data of sense experience.

# Unit 5 The Bias-Complexity Tradeoff
plan: new words, links, and the corresponding meaning of the notations. Then explain all the new work detials. Last figure out the proof
## 5.0 20181003
- papayas taste prblem .. tastiness
  1. papayas [pəˈpīə]
   - a tropical fruit shaped like an elongated melon, with edible orange flesh and small black seeds.
   - Lutein is found in spinach, leeks, peas, kiwi fruits, black grapes and romaine lettuce, while rich sources of zeaxanthin include sweetcorn, red peppers, nectarines, papaya and honeydew melon.
  2. taste [tāst]
   - the sensation of flavor perceived in the mouth and throat on contact with a substance. 
   - the wine had a fruity taste 
   - synonyms: flavor, savor, relish, tang, smack
  3. tastiness: pleasingness

- let us elaborate on this point
  1. elaborate
   - develop or present (a theory, policy, or system) in detail. 
   - the key idea of the book is expressed in the title and elaborated in the text

- this weaker assumption on distribution $\mathcal D$ is a prerequiste for using agnostic PAC model ...
  1. prerequisite [prēˈrekwəzət]
   - a thing that is required as a prior condition for something else to happen or exist.
   - sponsorship is not a prerequisite for any of our courses
   - synonyms: (necessary) condition, precondition
  2. agnostic [agˈnästik]
   - of or relating to agnostics or agnosticism.
   - So that wrestling is characteristic of my religious or agnostic poetry, but not necessarily everything else I do.
   - denoting or relating to hardware or software that is compatible with many types of platform or operating system. 
   - "many common file formats (JPEG, MP3, etc.) are platform-agnostic"

- ..pitfall of using a hypothesis as a mean of formalizing prior knowledge
  1. pitfalls [ˈpitˌfôl]
   - a hidden or unsuspected danger or difficulty. 
   - He bought some books on self-publishing and brushed up on the perils and pitfalls involved.
   - synonyms: hazard [ˈhazərd], danger, risk, peril, difficulty
  2. formalize
   - give (something) legal or formal status.
   - The civil union legislation exists because the Marriage Act as it was - the only basis to formalise the legal status of relationships - was vulnerable to human rights complaints.

## 5.1 The No-Free-Lunch Theorem
#### links and corresponding meanings: 
- $m \geq 8/log (7/|\mathcal H|/6)$: Corollary 2.3
- PAC model: 3.1
- ERM algorithm: empirical risk minimization 2.2
- approximation error: $\min_{h \in \mathcal D} L_{\mathcal D}(h)$
- $\mathcal D$ : distribution. So we know $\mathcal D$ over $\mathcal X \times \{0,1\}$ but?is it the training sample or task, or other? it is part of the task, or let say environment, eg. the papaya tastiness prediction in Australia. With the correct labeling function: $\mathcal {f:X \to Y}$. Now, $\mathcal {D,f}$ is a task.
- $h$: a hypothesis, let say the output of a learning algorithm, so $L_{\mathcal {D,f}}(h)$ is the loss of a hypothesis in the task $\mathcal {D,f}$. $h$ is the empirical output of learning algorithm $A$
- $S \sim \mathcal{D}^m$ : training set? yes!, each pair in the training data $S$ is generated by first sampling a point $x_i$ according to $\mathcal D$ and then labeling it by $\mathcal f$. So S is the empirical version of $\mathcal {D,f}$.   *In 3.1*: $S$ is a window through which the learner gets partial information about the distribution $\mathcal D$ over the world and the labeling function, $f$.
- $\mathcal X$: domain, or space, a vector of attribution. there exist a distribution  $\mathcal D$ over $\mathcal X \times \{0,1\}$, eg. in Austrilia, most tasty papaya gather in the distribution of this shape, and some overlapping with untasty papaya is on this corner.
- $C$: a subset of domain of 2m.  ?? task?, a empirical verstion of $\mathcal X$
- $T=2^{2m}$: the number of possible functions from C to $\{0,1\}$
- $A$: algorithm; return a predictive function $A(S):C \to \{0,1\}$
- $\delta$: sample & probability; the probability of getting **a nonrepresentative sample**. We call $1-\delta$ the *confidence parameter* of our prediction. (in 3.1)
- $\epsilon$: error, accuracy parameter, loss function, the threshold of success/failure of the learner. In 3.1, if $L_{(\mathcal{D,f})} \leq \epsilon$ we view the output of the algorithm as an **approximately correct predictor**.

- Theroem, Corollary, Proof ..
  1. theroem
  2. corollary
  3. proof

- indeed, a trivial successful learner
  1. indeed,
  2. trivial

- ... contradict the labels the $A(S)$ predicts on the unobserved instances in $C$.


## 5.2 Error Decompostion
- the minimum risk achievable by a predictor in the hypotheis.
  1. achievable

- under the realizability assumption, ..
  1. realizability

## summmary
### link:
- alternative way to express prior knowledge: chatper 7
- proof: related to lower bounds in VC theory

## exercise 2: complete it before prove

# Unit 1 Introduction
## 1.1 What is Learning 20181003
- If past experience with the food was negatively labeled, the animal predicts that it (the novel food producing an ill effect) will also have a negative effect when encountered in the future. 
  1. encounter, encountered
    - unexpectedly experience or be faced with (something difficult or hostile).
    - we have encountered one small problem
    - synonyms: experience, hit, run into,  
    - I encountered a challenge from another Pokemon trainer.   from?
- refer, referred
    - mention or allude to.
    - the reports of the commission are often referred to in the media
- when it is encountered in the future.

- (scan, extract  a set of words whose appearance in an e-mail message is indicative of spam) Then, when a new e-mail arrives, the machine can check whether one of the suspicious words appears in it, and predict its label accordingly.
  1. suspicious:  səˈspiSHəs
   - having or showing a cautious distrust(謹慎的不信任感) of someone or something.
   - he was suspicious of her motives
   - synonyms: doubtful, unsure,

- An Psychologist placed a bunch of hungry pigeons in a cage.
  1. a bunch of   [bənCH]
    - a number of things, typically of the same kind, growing or fastened together.
    - a bunch of grapes
    - synonyms: bouquet, posy, nosegay, 
    - I have a bunch of flutes/flowers
    - bundle [ˈbəndl]
        - a collection of things, or a quantity of material, tied or wrapped up together.
        - a thick bundle of envelopes
        - synonyms: bunch, roll, clump,
  2. psycholgist [sīˈkäləjist]  =  psychology  [sīˈkäləjē]
    - an expert or specialist in psychology.
    - Many cognitive psychologists also examine the effects of selective attention.
    - the scientific study of the human mind and its functions, especially those affecting behavior in a given context.
    - He studied Jungian and transpersonal psychology and took a special interest in allergic diseases.
    - synonyms: study of the mind, science of the mind

  
- An automatic mechanism had been attached to the cage, delivering food to the pigeons at regular intervals with no reference whatsoever to the birds' behavior. 
  1. whatsoever
   - at all (used for emphasis).
   - I have no doubt whatsoever
- (they have performed actions when the food was first delivered.) They subsequently continue to perform these same actions diligently.
  1. subsequently
   - after a particular thing has happened; afterward.
    - Mel's offhand remark subsequently became their rallying cry
    - synonyms: later (on), at a later date, afterward, in due course, following this/that
  1. diligently  : ˈdiləjənt
   - having or showing care and conscientiousness in one's work or duties.
   - many caves are located only after a diligent search
   - synonyms: industrious, hard-working, assiduous, conscientious, particular, punctilious
- long sentence: (The arrival of food reinforced each bird's specific action, and consequently, each bird tended to spend some more time doing the very same action.)  That, in turn, increased the chance that the next random food delivery would find each bird engaged in that activity again.  What results is a chain of events that reinforces the pigeons' associaton of the delivery of the food with whatever chance actions they had been performing when it was first delivered. -- 
    - in turn: conversely(ˈkänˌvərslē)  or   one by one
    - ? That, in turn, increased the chance that xx would?  
    - ?action would find phenomenon?  can an action be the subject of the word find. 
    - ?association of xx with xx?  
    - actions --> whatever chance actions they had been performing when it was first delivered.

- once we export a learning task to a machine, we must provide well defined crisp principles that will protect the program from reaching senseless or useless conclusion.
  1. export: Oo
   - send (goods or services) to another country for sale.
   - we exported 16 million worth of mussels to Japan
  1. whlie ..human.., once .. to a machine, we must ...
  1. crisp:  [krisp] air, food, or principle,  a postive word
   - (of a substance) firm, dry, and brittle, especially in a way considered pleasing or attractive.
   - crisp bacon
   - synonyms: crunchy, crispy, brittle,

- bait shyness revisited - rats fail to acquire conditioning between food and electric shock or between sound and nausea. ... if the unpleasant stimulus that follows food sonsumption is replaced by, say, electrical shock (rather than nausea), then no conditional occurs. ... The rats seems to have some "built in" prior knowledge telling them that, while temporal correlation between food and nausea can be casual, it is unlikely that there would be a causal relationship between food consumption and electrical shocks or between sounds and nausea.
  1. nausea [ˈnôzēə]   pinyin's o
   - a feeling of sickness with an inclination to vomit.
   - Only a few patients experienced postoperative nausea , so any statistical evaluation would be meaningless.
   - synonyms: sickness, biliousness,   
  1. temporal [ˈtemp(ə)rəl]
   - of or relating to time.
   - This issue explores some of the temporal and political dimensions of art. 
   - synonyms: secular, nonspiritual, worldly, profane, material, 
  1. causal [ˈkôzəl]
   - of, relating to, or acting as a cause.
   - the causal factors associated with illness
   - casual [ˈkaZHo͞oəl]   orange [ˈôrənj]
  1. stimulus [ˈstimyələs]
   - a thing or event that evokes a specific functional reaction in an organ or tissue.
   - areas of the brain which respond to auditory stimuli/stimulus
- between A and B or between C and D.  (A & B) || (C & D)
- casual, auditory
  1. casual: [ˈkaZHo͞oəl] 
   - relaxed and unconcerned.
   - she regarded his affairs with a casual indulgence
   - synonyms: relaxed, friendly, informal,
  1. auditory: [ˈôdiˌtôrē]
   - of or relating to the sense of hearing.
   - the auditory nerves

- We conclude that one distinguishing feature between the bait shyness learning and the pigeon superstition is the incorporation of prior knowledge that biases the learning mechanism.
  1. superstition [ˌso͞opərˈstiSHən]
   - excessively credulous belief in and reverence for supernatural beings.
   - he dismissed the ghost stories as mere superstition
   - synonyms: unfounded belief, credulity
  1. incorporation (掺入): internalisation, internalization
- We conclude that one doing xx is incorporation of xx that xx

- the rats "knows" that the co-occurrence of noise with some food is not likely to affect the nutritional value of that food.
  1. occurrence [əˈkərəns]
   - an incident or event.
   - vandalism used to be a rare occurrence
   - synonyms: event, incident, happening,
  1. nutrition [n(y)o͞oˈtriSHən]
   - the process of providing or obtaining the food necessary for health and growth.
   - a guide to good nutrition

## 1.2 When Do We Need Machine Learning
- Two aspects of a given problem may call for the use of programs that learn and improve on the basis of their "experience": the problem's complexity and the need for adaptivity. 
  1. call for:
   - synonyms: bespeak, quest, request
   - synonyms: require, take, demand

- There are numerous tasks that we human beings perform routinely, yet our introspection concerning how we do them is not sufficiently elaborate to extract a well defined program.
  1. routine: [ro͞oˈtēn]
   - performed as part of a regular procedure rather than for a special reason.
   - the principal insisted that this was just a routine annual drill
   - synonyms: standard, regular,
   - route, routing
  2. introspection [ˌintrəˈspekSHən]
   - the examination or observation of one's own mental and emotional processes.
   - quiet introspection can be extremely valuable
   - synonyms: self-analysis, self-examination, soul-searching, introversion, self-observation
  3. elaborate
   - involving many carefully arranged parts or details; detailed and complicated in design and planning.
   - elaborate security precautions
   - synonyms: complicated, complex, intricate, 
   - elaborate as a verb
        - develop or present (a theory, policy, or system) in detail.
        - the key idea of the book is expressed in the title and elaborated in the text
- route, routing
  1. route [ro͞ot]
   - a way or course taken in getting from a starting point to a destination.
   - the most direct route is via Los Angeles
   - synonyms: way, course,
  2. routing: 
   - send or direct along a specified course.
   - all lines of communication were routed through Atlanta
   - synonyms: direct, send, convey, dispatch, forward

-  (a set of tasks.) In all of these tasks, state of the art machine learning programs, programs that "learn from their experience," achieve quite satisfactory results, once exposed to sufficiently many traning examples.
  1. expose: ikˈspōz
   - make (something) visible, typically by uncovering it.
   - at low tide the sands are exposed
   - synonyms: reveal, uncover,
   - exposes as a adjective

- the analysis of very large and complex data sets: astronomical data, turning medical archives into medical knowledge, analysis of genomic data, and electronic commerce.
  1. archive  [ˈärˌkīv]
   - a collection of historical documents or records providing information about a place, institution, or group of people.
   - source materials in local archives
   - synonyms: records, annals, chronicles,
  1. analysis [əˈnaləsis]
   - detailed examination of the elements or structure of something, typically as a basis for discussion or interpretation.
   - statistical analysis
  1. gern [jēn]
   - (in informal use) a unit of heredity that is transferred from a parent to offspring and is held to determine some characteristic of the offspring.
   - proteins coded directly by genes
  1. genomic [ji-ˈnō-mik]
   - of or relating to a genome or to genomics
  1. commerce [ˈkämərs]
   - the activity of buying and selling, especially on a large scale.
   - the possible increase of commerce by a great railroad
   - synonyms: trade, trading, buying and selling,

- Learning to detect meaningful information in large and complex data sets is a promising domain in which the combination of programs that learn with the almost unlimited memory capacity and ever increasing processing speed of computers opens up new horizons.
  1. promising [ˈpräməsiNG]
   - showing signs of future success.
   - a promising actor
   - synonyms: good, encouraging, favorable, hopeful,
- ? combianation of A that xxx and dong B opens up new horizons

- one limiting feature of programmed tools is their rigidity - once the program has been written down and installed, it stays unchanged.
  1. rigid ˈrijid
   - unable to bend or be forced out of shape; not flexible.
   - a seat of rigid orange plastic
   - synonyms: stiff, hard, firm, inflexible,
  1. rəˈjidədē
   - inablity to be bent or be forced out of shape
   - adapt (oO) adaptive (oOtive) adativity(,Oo'tivity)


