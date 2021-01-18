# Deep Q-Network (DQN) - Acrobot

This is a test implementation of Deel RL Agent to solve OpenAI Gym's Acrobot-v1 environment.

# Getting started

This notebook uses Open AI gym's environmet, which you can install by [following this guide.](https://github.com/openai/gym)

This Agent was trained on local system using Windows 10. 
If you use Ubuntu or other OS and want to watch Agent's performance, 
you will need to modify some lines in this notebook (uncomment where marked).

# About Acrobot-v1
Acrobot is a 2-link pendulum with only the second joint actuated.
Initially, both links point downwards. The goal is to swing the
end-effector at a height at least the length of one link above the base.
Both links can swing freely and can pass by each other, i.e., they don't
collide when they have the same angle.

## States:

The state consists of the sin() and cos() of the two rotational joint
angles and the joint angular velocities :

`[cos(theta1) sin(theta1) cos(theta2) sin(theta2) thetaDot1 thetaDot2].`

For the first link, an angle of 0 corresponds to the link pointing downwards.
The angle of the second link is relative to the angle of the first link.
An angle of 0 corresponds to having the same angle between the two links.

A state of [1, 0, 1, 0, ..., ...] means that both links point downwards.

## Actions:

The action is either applying **+1, 0 or -1** torque on the joint between
the two pendulum links.

# Initial parameters

The Agent can be trained to achieve moderate performance fast with simple QNetwork:
 - single layer with 16 hidden nodes
 - with ReLU activation

And hyperparameters:
```buildoutcfg
BUFFER_SIZE = int(1e5)  # replay buffer size
BATCH_SIZE = 24         # minibatch size
GAMMA = 0.99            # discount factor
TAU = 1e-3              # for soft update of target parameters
LR = 0.01               # learning rate for Adam optimizer
UPDATE_EVERY = 4        # how often to update the network
```

# Further modifications

I managed to train the Agent to achieve >-90 performance in less than 1000 Epochs
by just modifying QNetwork size and it's hyperparamers. Try it yourself!