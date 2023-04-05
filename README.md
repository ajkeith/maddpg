# Multi Agent Deep Deterministic Policy Gradient

Multi Agent Deep Deterministic Policy Gradient Actor-Critic method for solving the multi agent tennis problem.

## Project Details

The multi agent tennis environment is a Unity environment that consists of a two paddle agents that can move back and forth and hop to hit a ball. The goal is to keep the ball in the air without hitting the ground.

![tennis](https://user-images.githubusercontent.com/10624937/42135623-e770e354-7d12-11e8-998d-29fc74429ca2.gif)

- State space: 8 dimensions corresponding to position and velocity of the ball and racket. 
- Action space: 2 dimensions corresponding to horizontal racket movement and jumping.
- Rewards: +0.1 is provided if the agent hits the ball over the net, -0.01 if the ball hits the ground or goes out of bounds. The goal is to keep the ball in play. 
  
The environment is considered solved when the agents achieve an average score of +0.5 (over 100 consecutive episodes, after taking the maximum over both agents).

The code in this project is based heavily off the code from the Udacity Deep Reinforcement Learning Collaboration and Competition [code](https://github.com/udacity/deep-reinforcement-learning/tree/master/p3_collab-compet) and my previous work in [DDPG](https://github.com/ajkeith/control-ddpg).

## Getting Started

Follow the instructions at the Udacity [Deep Reinforcement Learning](https://github.com/udacity/deep-reinforcement-learning) repository for general instructions on setting up the environment. Specific instructions for installing and downloading required files for this project are at located in [Project 3](https://github.com/udacity/deep-reinforcement-learning/tree/master/p3_collab-compet). 

## Instructions

Run `Tennis.ipynb` to train the agents and visualize the scores over time. The logic for the agent and neural network are in `ddpg_agent.py` and `ddpg_model.py`, respectively. The model weights for the successful agent are saved in `checkpoint_actor.pth` and `checkpoint_critic.pth`. Note that there is an alternative approach in the files `agent.py` and `model.py`.

## Learning Algorithm

This problem is solved using a multi agent deep deterministic policy gradient approach. This is an actor critic method that uses an actor neural network and a critic network to approximate the optimal value function and policy for two agents. 

Following the architecure and hyperparameter settings from my previous [DDPG solution](https://github.com/ajkeith/control-ddpg), the actor neural network architecture consists of two 256-node linear hidden layers with batch normalization in between and with ReLU (rectified linear unit) and tanh activation functions. 

The critic neural network architecure consists of two 256-node linear hidden layers (plus action nodes on the second), followed by batch normalization, followed by a 256-node linear hidden layer, followed by a 128-node hidden layer. This network uses leaky ReLU activation functions to prevent plateaus in learning. 

The overall hyperparameters are:
- Replay buffer size: 1e6
- Minibatch size: 128
- Discount factor: 0.99
- Soft update factor: 1e-3
- Initial noise epsilon: 1.0
- Noise decay: 0.9995
- Minimum noise: 0.01
- Network update frequency: 2

The training hyperparameters are:
- Max training episodes: 1500
- Max timesteps per episode: 1000

These parameters were chosen based on my previous [DDPG solution](https://github.com/ajkeith/control-ddpg).

## Results

This implementation solved the problem by achieving an average reward of at least +0.5 over 100 episodes in less than 1500 total episodes. The full results are shown below. The saved weights are available for the [actor](./checkpoint_actor.pth) and the [critic](./checkpoint_critic.pth). 

![Results](./score.png)

## Future Work

The agent's performance could be improved by implementing various alternative algorithms like multi agent PPO or with more sophisticated network architectures. It would also be interesting to consider a more competitive reward structure in which the agent gets a reward for making the ball hit the opponent's floor. 


