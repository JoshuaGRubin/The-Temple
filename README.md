# The Temple
A simple reinforcement learning experiment to train an agent to use manipulable bits as memory.

Famous archeologist and adventurer Ohio Smith seeks a legendary treasure and has tracked it down to an overgrown temple, deep in the jungle.  Upon entering, she sees two identical altars; one contains the reward, and the other, a somewhat painful trap (strangely enough, *exactly* as uncomfortable as the treasure is rewarding).  Fortunately, in the center of the room there is a plaque indicating which altar has the treasure - but the text is so small that she has to be standing at the plaque to read it.  Furthermore, each time she reenters the temple, the altars shuffle, with only the plaque to aid in consistently recovering the reward.  She caries with her only a small dial with three positions.  Can she learn to use it remember which altar to choose?

The Temple is a simple environment, inspired by [OpenAI's "Frozen Lake" gym](https://github.com/openai/gym). Our interface will loosely follow gym in that the environment object implements similar, `reset`, `step`, and `render` methods.  The Q-Learning approaches are inspired (if not taken directly from) [Arthur Juliani's helpful Q-Learning tutorial](https://medium.com/emergent-future/simple-reinforcement-learning-with-tensorflow-part-0-q-learning-with-tables-and-neural-networks-d195264329d0).

`reset` shuffles the reward and penalty altars, and sets the signal (plaque) accordingly.  Memory is set to `0`.

`step` takes one of the following actions; 0: move-left 1: move-right 2: move-down 3: move-up 4: set-memory-1 5: set-memory-2.  If memory-reset is available (`False`, by default), action 6: set-memory-0 (defauly state).

The state returned by `reset` and `step` is of the numpy array [x-coordinate, y-coordinate, memory-state, signal-state].  Each of these is by default a number from 0-2.  The signal component will always be zero unless the agent is positioned at the plaque, in which case it will be one or two, depending on which altar holds the reward.
