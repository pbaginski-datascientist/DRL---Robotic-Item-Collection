# DRL---Robotic-Item-Collection
Training an agent to collect items in a large square world using deep reinforcement learning

### Project description

For this project, the task is to train an agent to navigate in a large, square world, while collecting yellow bananas, and avoiding blue bananas. A reward of `+1` is provided for collecting a yellow banana, and a reward of `-1` is provided for collecting a blue banana. Thus, the goal is to collect as many yellow bananas as possible while avoiding blue bananas.

- **State space** is `37` dimensional and contains the agent's velocity, along with ray-based perception of objects around the agent's forward direction. 

- **Action space** is `4` dimentional. Four discrete actions correspond to:
  - `0` - move forward
  - `1` - move backward
  - `2` - move left
  - `3` - move right

- **Solution criteria**: the environment is considered as solved when the agent gets an average score of **+13 over 100 consecutive episodes**.

### Getting started

#### Configuration

PC configuration used for this project:
- OS: Mac OS 10.14.4 Mojave
- i7 Quadcore 3.5 Ghz, 32GB, GeForce GTX 780M

#### Environment setup

1. Check [this nanodegree's prerequisite](https://github.com/udacity/deep-reinforcement-learning/#dependencies), and follow the instructions.

2. Download the environment from one of the links below.  You need only select the environment that matches your operating system:
    - Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux.zip)
    - Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana.app.zip)
    - Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86.zip)
    - Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86_64.zip)

    (_For Windows users_) Check out [this link](https://support.microsoft.com/en-us/help/827218/how-to-determine-whether-a-computer-is-running-a-32-bit-version-or-64) if you need help with determining if your computer is running a 32-bit version or 64-bit version of the Windows operating system.

    (_For AWS_) If you'd like to train the agent on AWS (and have not [enabled a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md)), then please use [this link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux_NoVis.zip) to obtain the environment.

3. Place the file in `bin/` directory, and unzip (or decompress) the file.

# Instructions
To train the agent, start jupyter notebook, open `Navigation.ipynb`
and execute! For more information, please check instructions
inside the notebook.


#### DQN

**Idea**. Use deep neural network for Q-value function approximation as `state` -> `action` mapping. The following loss function is minimized as part of this:

![equation](http://latex.codecogs.com/gif.latex?MSE%28r_%7Bt&plus;1%7D&plus;%5Cgamma%20%5Cmax_%7Ba%7DQ%5Et%28s_%7Bt&plus;1%7D%2C%20a%29-Q%28s_%7Bt%7D%2C%20a_%7Bt%7D%29%29)

Neural network architecture:

| Layer   | (in, out)          | Activation|
|---------|--------------------|-----------|
| Layer 1 | (`state_size`, 64) | `relu`|
| Layer 2 | (64, 128) | `relu` |
| Layer 3 | (128, 128)| `relu` |
| Layer 4 | (128, 64) | `relu` |
| Layer 5 | (64, 32)  | `relu` |
| Layer 6 | (32, `action_size`)| - |

### Results
 - Best model weights are saved under the checkpoint file in the repo.

#### Possible improvements

Multiple potential improvements to this method are available and have been researched:
- Exchanging the epsilon greedy action selection for a more systematic method such as another neural network for best epsilon selection.
- Providing dynamic reward maps to the agent
- Using abbreviations of the above algorithm, namely Double DQN, Dueling DQN, Prioritized Experience Replay, Fixed-Q-Targets, or even the ultimate DQN version called Rainbow DQN.
