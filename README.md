# Multi Agent Deep Deterministic Policy Gradient

Multi Agent Deep Deterministic Policy Gradient Actor-Critic method for solving the multi agent tennis problem.

## Project Details

The multi agent tennis environment is a Unity environment that consists of a two paddle agents that can move back and forth and hop to hit a ball. The goal is to keep the ball in the air without hitting the ground.

- State space: 8 dimensions corresponding to position and velocity of the ball and racket. 
- Action space: 2 dimensions corresponding to horizontal racket movement and jumping.
- Rewards: +0.1 is provided if the agent hits the ball over the net, -0.01 if the ball hits the ground or goes out of bounds. The goal is to keep the ball in play. 
  
The environment is considered solved when the agents achieve an average score of +0.5 (over 100 consecutive episodes, after taking the maximum over both agents).

The code in this project is based heavily off the code from the Udacity Deep Reinforcement Learning Collaboration and Competition [code](https://github.com/udacity/deep-reinforcement-learning/tree/master/p3_collab-compet) and my previous work in [DDPG](https://github.com/ajkeith/control-ddpg).

## Getting Started

Follow the instructions at the Udacity [Deep Reinforcement Learning](https://github.com/udacity/deep-reinforcement-learning) repository for general instructions on setting up the environment. Specific instructions for installing and downloading required files for this project are at located in [Project 3](https://github.com/udacity/deep-reinforcement-learning/tree/master/p3_collab-compet). 

## Instructions

Run `Tennis.ipynb` to train the agents and visualize the scores over time. The logic for the agent and neural network are in `ddpg_agent.py` and `ddpg_model.py`, respectively. The model weights for the successful agent are saved in `checkpoint_actor.pth` and `checkpoint_critic.pth`. Note that there is an alternative approach in the files `agent.py` and `model.py`.


