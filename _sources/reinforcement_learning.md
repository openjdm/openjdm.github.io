# Reinforcement learning

Theo Culhane & Jessica Zhang

Reinforcement learning, or learning through trial and error, is a
central part of our understanding of how humans make judgements and
decisions. It has recently gained public interest due to advances in
artificial intelligence based on the principles behind learning by trial
and error. In this chapter, we will start out with a brief look at the
history of thinking on reinforcement learning in Psychology, including
the work of Rescorla and Wagner in 1972 on how reinforcement affects
Pavlovian conditioning, followed by a look at the history of
reinforcement learning becoming an important part of research on
artificial intelligence, looking at Sutton and Barto’s *Reinforcement
Learning* from 1998. Then, we will examine computational methods of
reinforcement learning and how they have evolved since the first edition
of Sutton and Barto’s book. We will then consider how our understanding
of reinforcement learning has evolved with advances in knowledge about
the dopamine system, looking both at the history of dopamine studies and
modern thinking about the dopamine system as it relates to reinforcement
learning, and finally explore the ways in which dopamine studies and
computational research have influenced one another.

# Overview of reinforcement learning history

Much of the current understanding of how reinforcement learning works
stems from the ideas first formalized in Rescorla and Wagner’s 1972
paper *A theory of Pavlovian conditioning: Variations in the
effectiveness of reinforcement and nonreinforcement*. Though Rescorla
and Wagner were studying classical conditioning and not decision making,
their theory of how conditioning affects how an animal (or human) judges
the value of a particular situation has become the basis for the more
complex formulations of how a human judges a situation and decides the
optimal action. Their formula, called the Rescorla Wagner Model, has
several complex parameters, but simplified for brevity posits the
equation that:

$$v\_X^{t+1} = v\_X^t + alpha(v\_X^{observed\_t} - v\_X^t)$$

where $v\_X^{t}$ is the estimation of value of situation X at time t,
$\\alpha$ is some constant between 0 and 1 that determines the tradeoff
between speed and stability of an estimate, and $v\_X^{observed\_t}$ is
an observation of how valuable situation X is in a particular instance t
(Rescorla and Wagner 1972). This basic premise has then been
incorporated into algorithms such as temporal difference learning, which
incorporates an aspect of future actions and past actions into an
estimate of the value of a particular circumstance, which is used in
reinforcement learning to decide what action should be taken in order to
maximize expected value (Sutton and Barto 2018). This idea of looking
into the past and future was then taken to another level in the Q
Learning algorithm, in which the specific action taken from a particular
state is also taken into account in the evaluation of the expected
reward, instead of just trying to estimate the particular value that a
state has independent of what is then done in that state.<span
class="Apple-converted-space"> </span>

  

In Q Learning, we build up a table of the expected value of taking every
particular state-action pair in a given system, systematically
downweighting expected values further in the future to represent our
uncertainty about the future. We then decide what actions we should take
using this table, generally using some kind of system that takes the
action with the highest expected value most of the time, and tests out
other actions to make sure our estimates for them are correct a small
amount of the time (Sutton and Barto 2018). 


![Q-learning matrix](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e0/Q-Learning_Matrix_Initialized_and_After_Training.png/590px-Q-Learning_Matrix_Initialized_and_After_Training.png)

(A example of the Q-learning matrix across training. Originally published at [<span
class="s2">https://en.wikipedia.org/wiki/File:Q-Learning\_Matrix\_Initialized\_and\_After\_Training.png</span>](https://en.wikipedia.org/wiki/File:Q-Learning_Matrix_Initialized_and_After_Training.png)
by LearnDataSci, 2018. Licensed under a Creative Commons Attribution 4.0 License; No changes made.)


More recently, as Q learning is used in more complex environments,
building a table that contains all possible state-action pairs is
infeasible, since the complexity leads to too many state-action pairs
for a computer to realistically store. Therefore, more recent Q learning
models, such as that used by Google in Alpha Go, which beat human
grandmasters in the board game Go, have used more complex systems, such
as deep neural networks, to estimate the expected value of actions. This
allows a model that generalizes to states or state-action pairs that it
has never seen before, and is able to generalize state-action pairs it
has seen before so it never needs to explicitly store each one. This
greatly increases the efficiency of the model, at the possible cost of
accuracy. However, because the efficiency is so much greater, modern
thinking is that this possible decrease in accuracy is worth it.

  

## Computational methods overview


One of the simplest types of computational reinforcement learning is
called the Multi Armed Bandit. In this problem, let us imagine that we
have a machine with k possible levers, each of which, when pulled, will
give a random reward with a specific mean. Before pulling any levers, we
have no knowledge of what reward this might be, but we know we want to
maximize the long term reward we get. Therefore, we must determine which
levers to pull, and decide our tradeoff between exploiting the best
lever we have found and trying to find out whether another lever might
be better in the long term. For a more concrete example, imagine a
machine with two levers, one of which gives a random reward uniformly
between 1 and 10 when pulled, and one of which gives a reward of 3 90%
of the time and 200 the other 10% of the time. If we started out pulling
each lever 4 times, we might expect to see perhaps a reward of 2, 6, 8,
and 4 from the first lever, and 4 rewards of 3 from the second lever.
Therefore, we might conclude that, to maximize our reward, we should
pull the first lever and get our mean of 5 reward, leaving on the table
the actual expected reward from lever 2 of 22.7 had we bothered to just
keep exploring. However, if instead lever 2 had just always given a
reward of 3, our first 4 trials would have been the same, and our choice
of always choosing lever 1 would be the correct one. This illustrates
the basic premise of the MAB, which then prescribes complex mathematical
formulas to optimize this exploration/exploitation tradeoff (Sutton and
Barto 2018).<span class="Apple-converted-space"> </span>

  

This then brings us to another important concept in computational
reinforcement learning, which is the distinction between online and
offline learning. In offline learning, we are given a pre-existing
dataset, and attempt to decide on the best actions to take at any
particular time using only that dataset. By contrast, in online
learning, we see new examples to learn about one at a time, and try to
learn as they come in, and then apply this new learning to inform our
exploration of what actions we should test out. This is more akin to
what humans do, but has several drawbacks. For one, because learning
starts when the first example is seen, there is the possibility that
learning will start off in the wrong direction, and then since future
learning is informed by the earlier learning, the entire learning
process may go down an improper path, and only end up back the right
path with a certain amount of luck, but no guarantee. Secondly, because
the entire dataset isn’t seen before learning occurs, the results can be
a lot less stable. In other words, since the basic makeup of the dataset
is likely to change over time, the results of learning can become
outdated, or random anomalies in the data can take the learning down an
unexpected path, similar to the first drawback. However, because it is
more alike with how humans learn, online learning is more informative
for studying human reinforcement learning and decision making than
offline learning is.



## Influence of Computational Research on Dopamine Studies

Reinforcement learning has its roots in animal learning in psychology,
which examines the relationship between events and animal responses to
them. The concept of reinforcement learning can be thought of as the
strengthening of relationships between events that result in animal
satisfaction and those animal responses, and the weakening of
relationships between events that cause animal discomfort and those
responses.<span class="Apple-converted-space"> </span>

  

Reinforcement learning research is valuable because it is a parallel to
animal decision-making and can help us understand our decision-making
processes in the face of reward and punishment. Instrumental
conditioning in animal behavior, or conditioning that involves
increasing the probability of reward and decreasing the probability of
punishment, is the essence of how reinforcement learning works
(Dickinson 2010). Pavlovian conditioning, or classical conditioning, is
considered a prototype for prediction learning within reinforcement
learning (Niv 2009). The behavioral processes behind conditioning are
computationally complex, and reinforcement learning provides a framework
for understanding them. This means that reinforcement learning models
both provide an explanation for animal behavior, help generate
predictions based on optimal behavior, and suggest actions to achieve
optimization.

  

Reinforcement learning models also help build an understanding of
dopamine, a neurotransmitter involved in many neurological disorders
including Parkinson’s disease, schizophrenia, and depression (Bhandari
2019). This understanding has implications for potentially treating
these conditions, which could ameliorate the lives of hundreds of
thousands of people worldwide. Specifically, studies of animal brains
via electrophysiological recordings, lesion studies, and pharmacological
manipulations have linked reinforcement learning to particular neural
substrates including dopamine while revealing that reward prediction
errors exist (Niv 2009).<span class="Apple-converted-space"> </span>

  

The process in which reward prediction errors are generated is a key
aspect of temporal difference learning, a reinforcement learning process
that extends the Rescorla-Wagner model to also account for the timing of
different events. In this process, a learning system aims to estimate
the values of different states based on predicted rewards or punishments
(Niv 2009). Temporal difference prediction errors occur when unpredicted
significant events happen and are similar to dopamine reward prediction
errors (Niv 2009). Dopamine neurons fire early in training in response
to an unexpected reward, known as an unconditioned stimulus, but not
once that stimulus becomes expected, or conditioned, over time (Niv
2009). When a reward is expected and not fulfilled, dopamine neuron
firings dip below the baseline, and this is known as a negative reward
prediction error (Niv 2009). It is notable that dopaminergic responses
and temporal difference learning are both able to account for delayed
rewards and discounted future rewards. Thus, examining the nuances in
temporal difference prediction errors is useful because it allows us to
better understand dopamine reward prediction errors, which helps
pinpoint dopaminergic targets in a medical context.<span
class="Apple-converted-space"> </span>

  

Reinforcement learning has been powerful in bringing together
computation, algorithm, and implementation, and the ways in which it has
facilitated our understanding of neurological investigations has been
invaluable (Niv 2009). As reinforcement learning and neurological
research continue to inform one another, we may consider how the synergy
of the two can accelerate breakthroughs in other fields.

  

  

*Caption*: A depiction of the Q-learning matrix across training.  Reproduced [<span
class="s1">https://en.wikipedia.org/wiki/Reinforcement\_learning\#/media/File:Reinforcement\_learning\_diagram.svg</span>](https://en.wikipedia.org/wiki/Reinforcement_learning#/media/File:Reinforcement_learning_diagram.svg)
by Megajuice, 2017 under a Creative Commons Attribution 4.0 License. No changes made)</span>

  

  

  

  

https://techvidvan.com/tutorials/reinforcement-learning/

  

  

<span
class="s1"><https://www.sciencedirect.com/science/article/pii/S0022249608001181></span><span
class="s3"> (1)</span>

<span
class="s1"><https://www.sciencedirect.com/science/article/pii/B9780125264303500039></span><span
class="s3"> (2)</span>

<span
class="s1"><https://link.springer.com/referenceworkentry/10.1007%2F978-3-540-68706-1_343></span><span
class="s3"> (3)</span>

<span
class="s1"><https://www.webmd.com/mental-health/what-is-dopamine></span><span
class="s3"> (4)</span>

  

<span
class="s1"><https://www.researchgate.net/figure/Reward-prediction-error-responses-at-the-time-of-reward-right-and-reward-predicting_fig2_302578615></span>

  

<span class="s3">Good overview of reinforcement learning: [<span
class="s1">https://www.sciencedirect.com/science/article/pii/B9780125264303500039</span>](https://www.sciencedirect.com/science/article/pii/B9780125264303500039)</span>

  

Neural correlates of RL:

<span
class="s1"><https://www.sciencedirect.com/science/article/pii/S0022249608001181></span>

  

Rescorla and Wagner’s original paper. The basis for a lot of modern
thinking about RL:

<span
class="s1"><https://www.researchgate.net/publication/233820243_A_theory_of_Pavlovian_conditioning_Variations_in_the_effectiveness_of_reinforcement_and_nonreinforcement></span>

  

  
