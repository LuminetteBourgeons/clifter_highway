# clifter_highway
![license](https://img.shields.io/github/license/slowy07/clifter_highway?logo=github&style=for-the-badge)
![build_badge](https://img.shields.io/github/workflow/status/slowy07/clifter_highway/build?logo=github&style=for-the-badge)
![python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![pytorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=PyTorch&logoColor=white)
[![sponsor_button](https://img.shields.io/badge/sponsor-30363D?style=for-the-badge&logo=GitHub-Sponsors&logoColor=#white)](https://saweria.co/slowy07)

Autonomous driving decision making tasks and environments

</br>

## Try it online!

[![google_colab](https://img.shields.io/badge/Colab-F9AB00?style=for-the-badge&logo=googlecolab&color=525252)](https://colab.research.google.com/drive/1owsJCTwjg92_2J0WDE-f-s_8jNvN9lgb?usp=sharing)

![multiagent_intersection](documentation/output_dat/intersection_multi_agent.gif)

</br>

## Environments

**Highway**


In this task, the ego vehicle is driving in multilane highway populated with other vehicles. The agent's objective is to drive in high speed on the right side on the road while avoiding collision with other vehicles.
```python
environ = gym.make("highway-v0")
```

![ebv1](output/highway.gif)


**Merge**


In this task, the ego vehicle approaches a junction with incoming vehicles on the access ramp. The agent's objective is now to maintain a high speed while leaving some space for other vehicles so that the ego vehicle can safely merge in the traffic.

```python
environ = gym.make("merge-v0)
```

![mergeenv1](output/merge-env.gif)

**Roundabout**


In this task, the ego vehicle if approaching a rounadbout with flowing traffic. ot follow its planned route automatically, but hash to handle lane changes and longitudinal control to pass the roundabout as fast as possible while avoiding collisions.


```python
environ = gym.make("roundabout-v0")
```
![roundaboutenv1](output/roundabout-env.gif)


**parking**

a goal conditioned continuous control task in which the ego vehicle must pak in a given space with the appropriate heading.

```python
environ = gym.make("parking-v0")
```

![parkingenv1](output/parking-env.gif)


**intersection**

intersection negotation task with dense traffic

![intersectionenv1](output/intersection-env.gif)


**racetrack**

a continuous control task involving lane-keeping and obstacle avoidance

![racetrackenv1](output/racetrack-env.gif)


## example agents

**deep q network**

![dqnenv1](output/dqn.gif)

this model-free value-based reinforcement learning agent performs Q-learning with function approximation, using a neural network to represent the state-action value function Q.

**deep deteministic policy gradient**

![ddpgenv1](output/ddpg.gif)
this model-free policy-base reinforcemetn learning agent is optimized directly by gradient ascent. it uses hindsight experience replay to efficiently learn how to solve a goal-conditional taks.

![deepfastdqnenv2](documentation/output_dat/highway_fast_dqn.gif)

**value iteration**

![ttcvi](output/ttcvi.gif)
the value iteration is only compatible with finite discrete MDPs, this simplified state representation describe the nearby traffic in terms of predicted time-to-collision on each lane of the road.the transition model is simplistic and assumes that each behicle will keep driving at a constan speed without changing the lines. this model bias can be source of mistakes.

the agent then performs a value iteration to computer the corresponding optimal state-value function.

**monte carlo tree search**

the agents leverages a transition and reward models to perform a stochastic tree seach of the optimal trajectory. no particular assumption is required on state representation or transition model.

![montelcarolenv](output/mcts.gif)


more information:
- [observation](documentation/observation.md)
- [actions](documentation/actions.md)
- [rewards](documentation/rewards.md)
- [multi agent setting](documentation/multi_agent_setting.md)
