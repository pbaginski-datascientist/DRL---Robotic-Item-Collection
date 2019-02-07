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

- For detailed Python environment setup (PyTorch, the ML-Agents toolkit, and a few more Python packages) please follow these steps: [link](https://github.com/udacity/deep-reinforcement-learning#dependencies)

- Download pre-built Unity Environment:
  - [Linux](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux.zip)
  - [Mac](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana.app.zip)
  - [Win x32](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86.zip)
  - [Win x64](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86_64.zip)

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
