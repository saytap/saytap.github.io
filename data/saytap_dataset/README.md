# SayTap Dataset

This dataset contains robot trajectories collected from a Unitree Go1 robot when
the robot followed simple instructions from the [SayTap](https://saytap.github.io) paper.

## Dataset
The dataset contains trajectories from 20 experiments, where the Go1 robot 
followed the following commands:

| #     | Command                                          |
|-------|--------------------------------------------------|
| 1     | Stand still                                      |
| 2-5   | Raise your front/rear left/right leg.            |
| 6     | Trot in place                                    |
| 7-10  | Trot forward/backward slowly/fast                |
| 11    | Pace in place                                    |
| 12-15 | Move forward/backward slowly/fast in pacing gait |
| 16    | Bound in place                                   |
| 17-20 | Bound forward/backward slowly/fast               |

In each experiment, Go1 started from a standing still pose and is ready for a
user command. Receiving the instruction, Go1 reacted accordingly for 5 seconds
and then resume to the standing still pose. Including the response time from a
LLM, each trajectory's length is about 1000 steps.

## Features

The features in each trajectory are:
1. `image` - Type: `np.uint8`, shape: `(64, 64, 3)`. This is a dummy
feature because SayTap does not take visual information as its input.
2. `wrist_image` - Type: `np.uint8`, shape: `(64, 64, 3)`. This is a dummy
feature because SayTap does not take visual information as its input.
3. `state` - Type: `np.float32`, shape: `(30,)`. This contains Go1's base and
joint states. `state[:3]` are the base's linear velocities, `state[3:6]`
contains the base's angular velocities, `state[6:18]` and `state[18:30]` are
the 12 joints' positions (offset from the default positions) and velocities.
4. `proj_grav_vec` - Type: `np.float32`, shape: `(3,)`. This is the gravity
vector `[0, 0, -1]` in Go1's base frame.
5. `desired_vel` - Type: `np.float32`, shape: `(3,)`. This contains the desired
velocities, where the first 2 entries are the linear velocities along and
perpendicular to the robot's heading direction and the last entry is the angular
yaw velocity.
6. `prev_act` - Type: `np.float32`, shape: `(12,)`. This contains the actions
applied to the robot in the previous step.
7. `desired_pattern` - Type: `np.bool`, shape: `(4, 5)`. This contains the
desired foot contact patterns for the front right, front left, rear right and
rear left legs. `True` indicates foot on the ground and `False` stands for foot
in the air. The length of the pattern is 5.

The default joint positions are: `hip=0`, `upper_leg=0.8` and `lower_leg=-1.7`.

## License
CC-BY-4.0
