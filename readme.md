<!-- [![continuous integration](https://raw.githubusercontent.com/MPI-IS-BambooAgent/sw_badges/master/badges/plans/corerobotics/tag.svg?sanitize=true)](url) -->

mim_msgs
--------

ROS messages and services for all the Machines-In-Motion organization.

### Installation:

#### Standard dependencies:

This package is based on [ROS2](https://docs.ros.org/).
Currently based on ROS2 dashing release.

#### Download the pacakge:

Use the `git clone` or [treep](https://gitlab.is.tue.mpg.de/amd-clmc/treep)
using the [treep_machines_in_motion](https://github.com/machines-in-motion/treep_machines_in_motion) configuration.

In both case do not forget to **register your ssh public key in your settings**:

In short you can either:
  - use git directly:
  ```
  mkdir -p ~/devel/workspace/src
  cd ~/devel/workspace/src
  git clone git@github.com:machines-in-motion/mim_msgs.git
  ```
  - or use treep:
  ```
  mkdir -p ~/devel
  pip install treep
  cd ~/devel
  git clone git@github.com:machines-in-motion/treep_machines_in_motion.git
  treep --clone mim_msgs
  ```

#### Build the package

We use [colcon](https://github.com/machines-in-motion/machines-in-motion.github.io/wiki/use_colcon)
to build this package:
```
cd mkdir -p ~/devel/workspace
colcon build
```

### Usage:

#### Demos/Examples

See the [ROS2 tutorials](https://docs.ros.org/en/dashing/Tutorials.html)
for some examples on how to use ROS2 messages and services.

### License and Copyrights

License BSD-3-Clause
Copyright (c) 2021, New York University and Max Planck Gesellschaft.
