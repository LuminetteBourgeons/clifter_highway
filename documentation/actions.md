## Actions

similarly to observations, several types of actions can be use in every environment. they are defined in the ``action`` module. each environment comes with a __defeault__ action type, which can be changed or customised using environment configurations. for instance,

```python
import gym
import clifter_highway

environ = gym.make("highway-v0")
env.configure({
    "action": {
        "type": "ContinuousAction"
    }
})
env.reset()
```

**continuous actions**

the ``continuousAction`` type allows the agnet to directly set the ``low-level`` control of the vehicle kinematic, namely the throttle alpha and stering angle

note:
_the control of throttle and tring can be enabled or disable trough the ``longitudinal`` and ``lateral`` configuration, respectively, the action space can be either 1D or 2D_

**discrete actions**

the ``DiscreteAction`` is a uniform quantization of the ``ContinuousAction`` above.

the ``actions_per_axis`` paramter allows to set the quantization step. similarly to continuous actions, the longitudinal and lateral axis can be enabled or disabled separately

**discrete meta actions**

The ``DiscreteMetaAction`` type adds a layer of speed and steering controllers on top of the continuous low-level control, so that the ego-vehicle can automatically follow the road at a desired velocity. Then, the available meta-actions consist in changing the target lane and speed that are used as setpoints for the low-level controllers.

the full corresponding action space is defined in ``ACTIONS_ALL``

```python
ACTIONS_ALL = {
        0: 'LANE_LEFT',
        1: 'IDLE',
        2: 'LANE_RIGHT',
        3: 'FASTER',
        4: 'SLOWER'
    }
```
Some of these actions might not be always available (lane changes at the edges of the roads, or accelerating/decelrating beyond the maximum/minimum velocity), and the list of available actions can be accessed with get_available_actions() method. Taking an unavailable action is equivalent to taking the ``IDLE`` action.

Similarly to continuous actions, the longitudinal (speed changes) and lateral (lane changes) actions can be disabled separately through the ``longitudinal`` and ``lateral`` parameters. For instance, in the default configuration of the intersection environment, only the speed is controlled by the agent, while the lateral control of the vehicle is automatically performed by a steering controller to track a desired lane.

**manual control**

the environments can be used as simulator

```python
env = gym.make("highway-v0")
env.configure({
    "manual_control": True
})
env.reset()
done = False
while not done:
    env.step(env.action_space.sample())
```