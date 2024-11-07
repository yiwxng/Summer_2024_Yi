### what is bayesian stats? 
it is an approach to statistics and inference, different than frequentist.


### how does bayes differ from frequentist?

___

### what is a heuristic? and how is ts a heuristic?
A heuristic is an practical approach to problem solving that does not necessarily always lead to the most optimal solution. 
 But can approximate that leads to a good enough solution.

### If we already have optimal thereotical solutions, then why use heuristic?
It is often used when the problem does not meet the preconditions, too computational or resource intensive, have to rerun the algorithm in a dynamic environment, real-time decision making.

## what is rl 
where an agent 


### what is the relationship between rl and mab?
it is a simplier version of rl.

## what is MAB?
It is a problem that seeks to balance between explore and exploit, when faced with many unfamilar options, with the end goal of maximizing your reward. 

This is an example slide that I created for CSSC 2024:
![My Image](/CTS/mab_slide.png)

note: this was a rough draft that did not get to fully explain what mab is due to short presentation time. 

### what is the goal of MAB?
balancing exploit and explore, and minimize regret?

### what is regret?
after the whole deployment is run
the different between the (highest arm mean reward x number of trials) - (the actual reward)

### What is the difference between rl and mab?
The difference is in mab, we try to find the best option, in rl we create the option from the interaction.
Balancing the need to explore all options to find the best one and exploiting the best option once it is known
- actions : rl creates, mab exist
- state : rl agent needs to be aware of the state, no state in mab
- long-term consequences : rl agent needs to be aware, mab only needs immediate rewards



  
Actions: rl choosing actions that not only affect immediate rewards, but also subsequent statesm and future rewards.
mab choosing actions 

| **Aspect**               | **Reinforcement Learning (RL)**                                                                                                                                                                | **Multi-Armed Bandit (MAB)**                                                                                                                   |
|--------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| **Objective**            | To learn a policy that maximizes cumulative rewards in a dynamic environment, taking into account the effects of actions on future states and rewards.             | To maximize cumulative rewards by choosing the best option based on reward probabilities, focusing on balancing exploration and exploitation.    |
| **State**                | The environment's state is crucial and changes based on the agent’s actions. Actions influence not just immediate rewards but future states and subsequent rewards. | Typically stateless; each decision is made independently of previous ones without considering changes in state.                                   |
| **Decision Impact**      | Actions have long-term consequences affecting future decisions through state transitions.                                                                           | Actions affect only the immediate reward; there is no impact on future actions beyond learning about reward probabilities.                       |
| **Learning Focus**       | Learning involves developing an understanding of how actions affect future states (model-based) or directly maximizing rewards through trial and error (model-free).| Learning focuses on estimating the reward probabilities of each option to inform the balance of exploration of new options and exploitation of known ones. |
| **Complexity**           | Generally higher complexity due to the need to manage state transitions, potentially large state and action spaces, and the temporal aspect of decision making.     | Simpler as it involves fewer variables (no states), and decisions are independent in terms of impact on future conditions.                      |
| **Algorithm Examples**   | Q-learning, Deep Q-Networks (DQN), Policy Gradient methods, Actor-Critic methods.                                                                                  | Epsilon-Greedy, Upper Confidence Bound (UCB), Thompson Sampling.                                                                               |
| **Exploration vs. Exploitation** | Balancing exploration (trying new actions to learn about their effects on states and rewards) and exploitation (using known information to maximize rewards) is nuanced by the impact on future states. | Directly focuses on exploring less-known arms to accurately estimate their rewards and exploiting the best-known arms for maximum reward.       |
| **Applications**         | Suitable for complex scenarios like robotics, autonomous vehicles, game playing, and any situation where decisions impact future conditions.                        | Commonly used in simpler decision-making scenarios like online advertising, clinical trials, or other fields where choices are relatively independent. |


## how does ts work? 
each arm has a reward distribution, each time sample happens, it will randomly sample a sample reward for each arm (does this approach handle the explore and exploit? since the random sampling ensures that exploration of non-optimal arms alsoo happens)
- then it will play the arm with highest sample reward 
- but there will be a chance where we don't get to explore all options due to randomness of samples. 


## Key Properties of TS & CTS: 
- convergence to optimal arm over time (under stationary bandits)(bc of  what theorem and why?)
- regret - as another way of measuring reward (why do wee have another way of measuring regret, what does this extra information tells us?)
- effect size : larger effect size, faster convergence (what is effect size? when do we learn it ?)
- empirically, ts outperforms UCB and e-greedy, especially under delayed rewards scenario
- risk: due to its randomness nature, there will be a chance that the optimal arm did not get play/ allocated more 
- too many contextual factor, increase in dimension, curse of dimensionality



## CTS background: 
CTS is from TS, a Bayesian probabllistic approach that treat the options’ reward like a multivariable distribution, and randomly sample from each distribution to balance exploit and explore. CTS is an extension to TS, where we incorporate context at the moment of given reward to optimize decision-making.

## definition
### key component 
- prior distribution
- likelihood
- posterior 
- posterior is proportional to prior * likelihood

### how does cts update ?
since distribution of reward depends on the type of rewards (binary, continous), and the added contextual variables are extra info to be accounted for. the expected reward will have a regression model, and be linked to a linking function to calculate expexted reward for each arm. then update. 

### questions:
- how does the mean vector and covariance matrix change?
- how does coefficients in regression change?
- why do we need a linking function 

### cons of TS:
- effectiveness of using TS depends on goodness of priors. (convergence rate??)
- bad priors may lead to suboptimal performance, especially in the early stages of learning.
- or no priors,

- complex for non-conjugate priors distributions

- although TS will eventually achieve optimal learning over time, the suboptimal learning may be dangerous in short term, high-stake situations.  

- correctly model the reward distributions/ reward regression

 
## Difference between TS and CTS 

| Element          | TS                                          | CTS                                             |
|------------------|---------------------------------------------|-------------------------------------------------|
| Model            | Probability distribution for rewards        | Regression model (e.g., linear model)            |
| Context          | No                                           | Yes                                              |
| Parameter        | theta                                 | beta                                  |
| Prior            | ex. theta ~beta(a,b) | beta ~ N(mean vector, and )   |
| Posterior        |  based on observed rewards           |  based on observed context-reward pairs   |
| Action Selection | sample sampled value for each distribution and select max     | , select max |
| Example          | Bernoulli rewards                           | Linear model with context                        |

