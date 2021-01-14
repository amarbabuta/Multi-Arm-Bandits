### Multi-Arm-Bandits


### 1. What is the task? 
1. A system for deeper understanding of Multi Arm Bandits and common Multi Arm Bandits approaches and how they are applied.
2. Better understanding of how the Bayesian paradigm support ML.




In this project, the task is to have deeper understanding of Muti Arm Bandits approaches, and how they can be used in real world scenarios. Our works include implementing Python classes for Multi Arm Bandits and contextual bandits algorithms. For more details, please check the [project specifications](https://github.com/amarbabuta/Multi-Arm-Bandits/blob/master/project2%20.pdf) and [project code](https://github.com/amarbabuta/Multi-Arm-Bandits/blob/master/ABABUTA.ipynb).

### 2. Code
#### 2.1. Epsilon greeedy and UCB
`ABABUTA.ipynb`
###### Intialize
first initializing the constructor with list of Qs with Q0, a list for storying rewards and making a list of list for arm rewards.


##### 2.1.1 Epsilon greedy
##### Play the arm
1. choosing a random number between 0.0 and 1.0.
2. if the random number is less than epsilon then explore otherwise exploit.
3. Then tie breaking and returning the random arm among the value-maximising the arms.
##### Update the arm
Update function is storying the rewards in rewards list and incrementing reward arm by updating it.

##### 2.1.2 UCB
##### Play the arm
1. estimating value of each arm j as average reward observed.
2. then finding maximum Qt.
3. Then tie breaking and returning the random arm among the value-maximising the arms.
##### Update the arm
Update function is storing the rewards in rewards list and incrementing reward arm by updating it.

#### 2.2. Beta Thompson Bandit
###### Intialize
first initializing the constructor with alpha(i) and beta(i) to alpha0 and beta0 respectively and a list for storying rewards.
[beta thompson algorithm](http://proceedings.mlr.press/v23/agrawal12/agrawal12.pdf)

##### Play the arm
1. finding beta distribution for each arm j.
2. then storing maximum of beta.
3. Then tie breaking and returning the random arm among the value-maximising the arms.
##### Update the arm
Update function is storing the rewards in the rewards list and updating alpha and beta according to algorithm.


#### 2.3 Off-Policy Evaluator
1. checking whether the arm value is equal to context value if it is not equal then arm index is incremented and it checks next value.
2. if arm value is equal to context value then it updates the value of arm, rewards and context and increments the arm index
3. if arm index is greater than length of arms then it breaks and return the rewards

This function returns the average reward after applying above approaches.

[policy evaluator](https://arxiv.org/pdf/1003.0146.pdf)
[policy evaluator](https://arxiv.org/pdf/1003.5956.pdf)

#### 2.4 Contextual Bandits- LinUCB
###### Intialize
initializing A and b with ndims identity matrix and ndims zero vector respectively and a list for storying rewards.

##### Play the arm
1. dividing context for each arm.
2. calculating theta(a) by applying the formula in algorithm.
3. calculating p(t,a) by applying the formula given.
4. storying maximum of p(t,a).
5. Then tie breaking and returning the random arm among the value-maximising the arms.
##### Update the arm
Update function is storing the rewards in rewards list and updating A and b according to algorithm.

Then calculating off-policy average reward on this approach.


#### 2.5 Contextual Bandits- LinThompson
###### Intialize
initializing B, parameter mu and f with identity, zero matrix and zero matrix respectively according to algorithm and a list for storing rewards.

##### Play the arm
1. first evaluating mu(t) which is Gaussian distribution according to algorithm.
2. finding maximum of arm a(t) by multiplying transpose of context and mu(t).
3. Then tie breaking and returning the random arm among the value-maximising the arms.
##### Update the arm
Update function is storing the rewards in rewards list and updating B and f according to algorithm.

Then calculating off-policy average reward on this approach.



[Contextual Bandits-Lin Thompson](http://proceedings.mlr.press/v28/agrawal13.pdf)

#### 2.6 Evaluation

##### 2.6.1 Plot cumulative reward for each class
finding the cumulative reward per round and then plotting the curve for each algorithm.

##### 2.6.2 Hyperparameter optimization of LinUCB and LinThompson
function returning best reward for alpha value and v value for Lin UCB and LinThompson respectively.
and plotting the average reward vs alpha/v value.




