### what is bayesian stats? 
it is an approach to statistics and inference, different than frequentist.


### how does bayes differ from frequentist?


### what is a heuristic? and how is ts a heuristic?
A heuristic is an practical approach to problem solving that does not necessarily always lead to the most optimal solution. 
 But can approximate that leads to a good enough solution.

### If we already have optimal thereotical solutions, then why use heuristic?
It is often used when the problem does not meet the preconditions, too computational or resource intensive, have to rerun the algorithm in a dynamic environment, real-time decision making.

### what does "heuristic" mean for ts?
It means that it can 

### what is the relationship between rl and mab?
it is a simplier version of rl.

## what is MAB?

### what is the goal of MAB?
balancing exploit and explore, and minimize regret?

### what is regret?
after the whole deployment is run
the different between the (highest arm mean reward x number of trials) - (the actual reward)

### What is the difference between rl and mab?
The difference is in mab, we try to find the best option, in rl we create the option from the interaction.
Balancing the need to explore all options to find the best one and exploiting the best option once it is known

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
each arm has a reward distribution, each time sample happens, it will randomly sample a sample reward for each arm (does this approach handle the explore and exploit? since the random sampling ensures that not )
- then it will play the arm with highest sample reward 
- 


## what are the potential problem with TS?
- high type 2 error (false positive)