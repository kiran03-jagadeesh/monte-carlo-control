# MONTE CARLO CONTROL ALGORITHM

## AIM
To develop a Python program to find the optimal policy for the given MDP using the Monte carlo control algorithm.

## PROBLEM STATEMENT
The FrozenLake environment in OpenAI Gym is a gridworld problem that challenges reinforcement learning agents to navigate a slippery terrain to reach a goal state while avoiding hazards. Note that the environment is closed with a fence, so the agent cannot leave the gridworld.

### States
- **5 Terminal States**:
  - `G` (Goal): The state the agent aims to reach.
  - `H` (Hole): A hazardous state that the agent must avoid at all costs.
- **11 Non-terminal States**:
  - `S` (Starting state): The initial position of the agent.
  - Intermediate states: Grid cells forming a layout that the agent must traverse.

### Actions
The agent can take 4 actions in each state:
- `LEFT`
- `RIGHT`
- `UP` 
- `DOWN`

### Transition Probabilities
The environment is stochastic, meaning that the outcome of an action is not always certain.
- **33.33%** chance of moving in the intended direction.
- **66.66%** chance of moving in a orthogonal directions.

This uncertainty adds complexity to the agent's navigation.

### Rewards
- `+1` for reaching the goal state(G).
- 0 reward for all other states, including the starting state (S) and intermediate states.

### Episode Termination
The episode terminates when the agent reaches the goal state (G) or falls into a hole (H).

### GRAPHICAL REPERSENTATION
![rl_2](https://github.com/kiran03-jagadeesh/monte-carlo-control/assets/94174536/b0556bd7-2dc8-4066-8c34-6e4141cc25b1)


## MONTE CARLO CONTROL ALGORITHM
1. Initialize the state value function V(s) and the policy π(s) arbitrarily.
2. Generate an episode using π(s) and store the state, action, and reward sequence.
3. For each state s appearing in the episode:
    * G ← return following the first occurrence of s
    * Append G to Returns(s)
    * V(s) ← average(Returns(s))
4. For each state s in the episode:
    * π(s) ← argmax_a ∑_s' P(s'|s,a)V(s')
5. Repeat steps 2-4 until the policy converges.
6. Use the function `decay_schedule` to decay the value of epsilon and alpha.
7. Use the function `gen_traj` to generate a trajectory.
8. Use the function `tqdm` to display the progress bar.
9. After the policy converges, use the function `np.argmax` to find the optimal policy. The function takes the following arguments:
    * `Q`: The Q-table.
    * `axis`: The axis along which to find the maximum value.

## MONTE CARLO CONTROL FUNCTION
### STEP 1
Initialize the agent's knowledge of the environment, which includes the Q-values, state-value function, and policy.

### STEP 2
The agent explores the environment, taking actions and observing the rewards and next states. This process is repeated until an episode ends.

### STEP 3
For each step in the episode, the agent updates its Q-value estimate for the state-action pair it took. The update is based on the reward received and the value of the next state.

### STEP 4
The agent updates its policy to select the action with the highest Q-value for each state.

### STEP 5
The agent repeats steps 2-4 for a specified number of episodes or until it converges to a good policy.

### STEP 6
The agent returns the optimal Q-values, state-value function, and policy.

## OUTPUT:
![Rl_op](https://github.com/kiran03-jagadeesh/monte-carlo-control/assets/94174536/74d68540-209b-4fcb-91f6-63697839010d)

## RESULT:

Thus, Python program is developed to find the optimal policy for the given RL environment using the Monte Carlo algorithm.
