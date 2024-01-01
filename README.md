# Snake-Game-AI
# Reinforcement Learning
Reinforcement learning is an area of Machine Learning. It is about taking suitable action to maximize reward in a particular situation. In this type of learning, we have an agent, which is allowed to interact with the environment. After any action taken by the agent in the environment, the environment will return a reward to the agent, and a new state of the environment.
The agent will explore the whole environment using random moves in the beginning, and will gain some knowledge of the environment. After training, the agent will only make moves that will return high rewards.
# Example:
Consider an environment of size 3x3, and the agent is a dog whose goal is to get to the bone and avoid the fire.
First, we need to define actions that can be taken by our agent, states in the environment, and rewards.
Our agent, the dog can move up, right, down, or left. There are 9 states, two of them are end states (Fire and Bone). The dog wll get a reward of 10 points if he successfully gets to the bone, and a reward of -10 if he falls in the fire.
### Q Values, and Q Learning
Q value or Quality value is used to determine the quality of an action at a state. Q value depends on the state and action. A high Q value for an action means that the end reward will be high if we take that action.      
**Q(State, Action) = Q Value**
We need to learn these Q values for all the state-action pairs. The algorithm which is used to learn these values is called Q Learning. The skeleton learning equation in Q Learning is as follows:

**New Q Value Q(State, Action) = Old Q Value Q(State, Action) + Reward for that action + Max Q Value Q(State, Action)**

To get the new Q value for a state-action pair, we add the old value with the reward of that action, and the max Q value of the next state.
We also use discounting reward which means that our agent wants to reward as soon as possible. Thus our end reward value of +10 will decrease with every step away from the end state.
After using Q Learning, and applying a discount of reward we will get Q values as showing in the picture below. Now the dog will always take the shortest route to the bone.
# Deep Q Network
For games with many states, we use a neural network to get Q Value for a state-action pair. This network is known as Deep Q Network or DQN. We can either of the following architecture of DQN, but the second one is preferred.

If we use first architecture, then for at a given state, we have to iterate through DQN n times, where n is the number of actions available for the agent.

If we use second architecture, then we have to iterate through DQN only one time, and we will get Q Values for all actions, among them we will choose the action with the highest Q value.

We want to iterate through DQN only one time because iterating through a Neural Network is a computationally expensive step, and it takes time to get output. Thus less iteration is preferred.
# Snake Game
We have to create a bot for the Snake game. In the game of snake, the snake has to eat food to grow, and avoid hitting walls and eating itself. First, we have to define the actions, state, and rewards.
#### Actions
Snake can only move left, forward, or right. Snake can't move backward.
#### State
We can get the state of the game by just answering the following things:
- Is there a wall or snake body on the left?
- Is there a wall or snake body in front?
- Is there a wall or snake body on the right?
- Was snake moving up?
- Was snake moving right?
- Was snake moving down?
- Was snake moving left?
- Is the food left or right?
- Is the food up or down?
  
Assume the following state when snake is moving up.

- Is there a wall or snake body on the left? **NO**
- Is there a wall or snake body in front? **NO**
- Is there a wall or snake body on the right? **YES**
- Was snake moving up? **YES**
- Was snake moving right? **NO**
- Was snake moving down? **NO**
- Was snake moving left? **NO**
- Is the food left or right? **Left**
- Is the food up or down? **Down**
#### Reward
The agent will get +10 reward when the snake eats food, and -10 when the snake eats itself or hits the wall.

