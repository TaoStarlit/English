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


# Unit 5 The Bias-Complexity Tradeoff
plan: new words, links, and the corresponding meaning of the notations. Then explain all the new work detials. Last figure out the proof
## 5.0 20181003
- papayas taste prblem .. tastiness
  1. papayas, tastiness

- let us elaborate on this point
  1. elaboarat

- this weaker assumption on distribution $\mathcal D$ is a prerequiste for using agnostic PAC model ...
  1. prerequiste
  2. agnostic

- ..pitfall of using a hypothesis as a mean of formalizing prior knowledge
  1. pitfalls
  1. formalize

## 5.1 The No-Free-Lunch Theorem
#### links and corresponding meanings: 
- $m \geq 8/log (7/|\mathcal H|/6)$: Corollary 2.3
- PAC model: 3.1
- ERM algorithm: empirical risk minimization 2.2
- approximation error: $\min_{h \in \mathcal D} L_{\mathcal D}(h)$
- $\mathcal D$ : distribution. So we know $\mathcal D$ over $\mathcal X \times \{0,1\}$ but?is it the training sample or task, or other?
- $S \sim \mathcal{D}^m$ : training set?
- $\mathcal X$: domain. there exist a distribution  $\mathcal D$ over $\mathcal X \times \{0,1\}$
- $C$: a subset of domain of 2m.  ?? task?
- $T=2^{2m}$: the number of possible functions from C to $\{0,1\}$
- $A$: algorithm; return a predictive function$A(S):C \to \{0,1\}$
- $\delta$ : probability; $\epsilon$ : error

- Theroem, Corollary, Proof ..
  1. theroem
  2. corollary
  3. proof

- indeed, a trivial successful learner
  1. indeed,
  2. trivial

- .. contradict the labels the $A(S)$ predicts on the unobserved instances in $C$.


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

