# reward

the reward function is defined in the ``_reward()`` method, overloaded in every environment

The choice of an appropriate reward function that yields realistic optimal driving behaviour is a challenging problem, that we do not address in this project. In particular, we do not wish to specify every single aspect of the expected driving behaviour inside the reward function, such as keeping a safe distance to the front vehicle. Instead, we would rather only specify a reward function as simple and straightforward as possible in order to see adequate behaviour emerge from learning. In this perspective, keeping a safe distance is optimal not for being directly rewarded but for robustness against the uncertain behaviour of the leading vehicle, which could brake at any time.

## most environment

We generally focus on two features: a vehicle should
progress quickly on the road;
avoid collisions.

