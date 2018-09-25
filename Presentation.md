- new words:
1. presenter, process, 
2. corridor, balcony, 
3. coriander, celery, chrysanthemum 
4. parallel, coorelation
5. interpret, interpretation
6. arithmetic 

my part to xingrui:
1. task relationship: 
2. interpret task relationship
3. 




How to share the hidden layers across tasks to model the task relationship?


motivation:
1. Task differences harm model precidtion in multi-task learning.
  
2. Avoiding the need of adding many new parameter per task, as recent works did when modeling the task relationships.

3. Leveraging Shared Bottom Network to capture the task-shared information and MoE model to capture the task-specific information, which means combination of this two models to model the task relationships.



lilsubs.com -- realy impressive

### short presentation
short presentation overview and sample --- greet, reason,
    structure: introduction: greeting, self id, topic, purpose(why I choose this topic), what the main point be?
      
greeting: well come? 
self: as you may already know
purpose: today, I would like to talk to you a little bit about
reason: because I think it is important for students to know something about more deep learning frameworks 
indication time + deal with question: since I've only got about 7 or 8 minutes I won't be able to go into great depth so if you
have any questions I'd be happy to answer at the end of presentation

scope or outline:
so given these time limits I've chosen just two things to
talk about. firstly I'll briefly introduce this topic
secondly I'd like to talk about the backgroud of the paper

XX dealing with difficult terms XX
I don't think I'll be using any difficult terms ... leave your question to the end of presentation

transition:
okay well
let's get started the first thing, the introduction. 
The key word of the title, multi-task learning is a subfield of machen learning ...

expanding the point:
this seems quite important to students and I guess there are two possible reasons for this.
firstly it's because they're curious to know about their teachers and lecturers 
and secondly they probably just want to feel confident that they're in the hands of an experienced professional 

(real things) well I don't know about that but I've certainly been around a long time I started
... primary school
as you probably know: primary school teachers are generalists
in other words they teach nearly everything
so: for the first couple of years after graduating from Teachers College I taught in primary schools
(another) after that I went back to university

this xx and brings me to: 1995, when I started xxx  
so that means: I've been here for 18 years 

restaing main point: so hopefully that satisfy your curiousity

transition to 2nd point:
 but of course I don't spend all
my time in teaching and learning believe it or not teachers are human too and need a break from work just like everybody else.
so this brings us to the second thing I'd like to share with you about myself. 
and that is to tell you about how I spend my spirit or my free time well in a strange sort of way I can't stay away from teaching and learning because I love foreign languages


This seems quite important, there are 3 points for this.
Firstly, it the simplest method for multi-task learning, whose goal is to improve the generation performance.
Secondly, 
Third, for the structure, xxx, which enables the shared bottom model to xx

But, as mention before the task differences will harm the performance, as you know this model does not consider the task differences.




### expression start/close/transition:
 how important a presentation can be?  part 1, part 2, part 3
    - what and why it important
        1. I will xx
        2. why it is important? well, if you do this correctly, your audience you followwhat  you pay attentionto what you say
        3. this means you have much greater chance of selling them your products or services,
        4. getting a job or promotion
        5. or just impress you boss and co-workers with how organized and efficient your presentation. it is pretty good thing, hub
    - part 1 when you begin your topic: OK, so as mentioned(outline) the first thing I'm going to tale about is __.
    - part 2 end your 1st topic: So I think you've now got a good understanding of __ right?
    - part 3 transition to your next part: OK, so let me now move onto the second/next thing/item, which is ___


### transistion:
transistion: on the slides, it must have separate points:
    1. don't too smooth, eg. next, next. you need to separate main points
    2. signpost: first, second, third (don't use finally unless in the conclusion)
    3. classic transition: now that we've discussed tents, let's talk about sleeping bags
    4. summary transition (also highlight the postions of the points and the relationships among the points): And that's why tents are the first key component of your camping gear. (pause) Now let's discuss another key piece of gear.  recap A, pause, forecap B
    5. racap previous two points and forecap next topic: tents are the first key component of your camping gear. (pause) A good sleeping bag is the second (pause). let's now discuss how you're going to carry it all.





## Real draft
greeting: hello everyone, welcome to our presentation.

self: as you may already know my name is Tao Zheng, and the other two presenters are xingrui and Yan Zhang.

purpose: today, we would like to talk to you a little bit about the paper: Modeling Task Relationships in Multi-task Learning with Multi-gate Mixture-of-Experts
\\

reason: because I think it is helpful for you to know this new deep learning frameworks on the classic topic multi-task learning. 

time question: since we've only got about half an hour for presentation, we won't be able to go into great depth. so if you have any questions, we'd be happy to answer at the end of presentation

### outline
For the outline, given these time limits. For my part in this outline, there are just two things to talk about.  
firstly I'll briefly introduce this topic.
secondly I'd like to talk about the backgroud of the paper.


#### multi-tasks learning:
The topic is multi-tasks learning, a machine learning subfield in which multiple tasks are solved at the time, that means they are trained simoutonus, and exploiting commonalities and differences across tasks.

##### RecSys: 
why it is important? Well, take recommander system as an example. If you predict what movies users want to watch and recommand them, then users will purchase, which is task one users engagement. At the sametime, you also need to model what movies users like and rate, that means afterward you will let they go back for more movies, which is task 2 users satification. If you do these 2 tasks simultaneously and correctly, you will have a much greater chance to sell your movies again and again, earn profits and obtain rewards continuously.
It is a pretty good thing, hub.

##### Challenge:
But in practice, multi-task learning models do not always outperform the corresponding single-task models on all tasks. Why? because the task differences harm the preditions. To tackle the this problem, researchers need to model the task relationships as the title said.

#### task relationship.
What are task relationships? Well, It consists of two types: shared and specific. 
##### breed predictions of dogs and cats
An interesting example about task relationships is the breed prediction of cats and dogs. cats and dogs have shared information ..., they also have their own specific information. By the way, this diagram is the shared-bottom model using the shared layers to capture the task shared information, this model will discussed in related works section.

###### ---> question
the two important concepts are the multi-task learning and the task relationships, let's have a look that what question this paper try to answer.  
#### the question of the paper
How to share the hidden layers across tasks to model the task relationship?
Keep this question in mind, let's discuss about the background, related works


#### shared bottom
this is the the shared bottom, as we mention before before.

.....


###### shared bottom ---> recent works

This shared-bottom model is a basic model for multi-task learning problem, since this problem was researed in 1997. Now let's have a look of the recent works of multi-task learning problem.


#### recent works --- Mixture of Experts
xx, xx, xx and outperform the basic shared bottom model, but all of they need adding ...
And this paper tries to avoid adding more parameter.
The paper propose a model that is inpired by a classic model, that is Mixture of Experts model.

As you can see in this diagram:

.....

### motivation:
1. goal, 
2. approch, 
3. implementation

And how to combine these 2 model to to model the tasks relationship.
I will leave this part to our buddy, xingrui: 















### end end problem
? the idea of shared bottom / MoE.  ? learn the way to illustrate following points with proper transitional statements.
1. goal, 
2. approch, 
3. implementation

? a statement: multi-class learning model < single task. + reason??

Ying hua,  she investigates website the group of the the authors.

graph problem: iteration

update and learning: different part different phrase

one hop  two hop

SSE, graph representation

check the supplementary materials of SSE

it is another way:  different from the graph xx embedding algorithm

怎么找近邻呀！！ 不同的V.  one-hop neighbors; T-hop neighbors



our teams:

pearson correlations:  to control the task correlation, difference


gate and expert is the neural.  attaition ??

methods:  end-to-end nerual network

pearson:
to quantify indicator task relationships


MMoE/OMoE: parameter


performance:   loss-number of correlation
correlation 0.1, 0.5, 1:  make sense: MMoE is always good, shared and MMoE the same, when correlation = 1.  

- jiangchao
VAE mixture model

- boss
mixture model?  I can use EM first.    EM have few parameters, to mixture regression model.

EM replace the Gate A.  the constant matrix

GMM


- me:
interpration, the distribution of gate

- yinghua:
different input: image + attribution. 
Data pre-processing