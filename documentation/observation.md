# Observation

for all environments, several types of a observation can be used. they are defined in the ``observation`` module. each environment comse with a __default__ observation, which can be changed or customised using environment configuration for instance

```python
import gym
import clifter_highway

env = gym.make("highway-0")
env.configure({
    "observation":{
        "type": "OccupancyGrid",
        "vehicles_count": 15.
         "features": ["presence",  "x", "y", "vx", "vy", "cos_h", "sin_h"],
         "features_range":{
            "x": [-100, 100],
            "y": [-100, 100],
            "vx": [-20, 20],
            "vy": [-20, 20]
         }
        "grid_size": [[-27.5, 27.5], [-27.5, 27.5]],
        "grid_step": [5, 5],
        "absolute": False
    }
})
env.reset()
```
the ``type`` field in the observation configuration takes values defined in ``observation_factory()``

## kinematics

the ``kinematicsObservation`` is a V x F array that describes a list of V nearby vehicles by a set of features of size F, listed in the "features" configuration field.

**example configuration**
```python
import gym
import clifter_highway

config = {
    "observation": {
        "type": "Kinematics",
        "vehicles_count": 15,
        "features": ["presence", "x", "y", "vx", "vy", "cos_h", "sin_h"],
        "features_range": {
            "x": [-100, 100],
            "y": [-100, 100],
            "vx": [-20, 20],
            "vy": [-20, 20]
        },
        "absolute": False,
        "order": "sorted"
    }
}
env = gym.make("highway-v0")
env.configure(config)
obs = env.reset()
print(obs)
```

