# clifter_highway
environmetnt decision making in autonomous driving


## environment

**highway**


in this task, the ego vehicle is driving in multilane highway populated with other vehicle. the agent's objective is to reach high speed whole avoiding collision with neighbouring vehicles. driving on the right side of the road is also rewarded
```python
environ = gym.make("highway-v0")
```

![ebv1](output/highway.gif)


**merge**


in this task, the ego vehicle starts on a main highway but soon approaches a road junction with incoming vehicles on the access ramp. the agent's objectiove is now to maintain a higha speed while making room for the vehicles so that the can safety merge in the traffic.

```python
environ = gym.make("merge-v0)
```

![mergeenv1](output/merge-env.gif)
