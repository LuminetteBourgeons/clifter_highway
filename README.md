# clifter_highway
environmetnt decision making in autonomous driving


## environment

in this task, the ego vehicle is driving in multilane highway populated with other vehicle. the agent's objective is to reach high speed whole avoiding collision with neighbouring vehicles. driving on the right side of the road is also rewarded
```python
environ = gym.make("highway-v0")
```

![ebv1](output/highway.gif)