
# Panda Simulation Environment (Gazebo + MoveIt!)

This repository contains the simulation setup for a Franka Emika Panda Robot placed on a table in Gazebo. An object is positioned in front of the robot, which is equipped with a Realsense RS200 Camera attached to its wrist and a Panda Parallel Jaw Gripper. The robot is controlled by MoveIt, providing a comprehensive environment for research and development in robotics.

## Installation

Follow these steps to set up your simulation environment:

```bash
mkdir -p catkin_ws/src
cd catkin_ws/src
git clone https://github.com/Oyefusi-Samuel/PANDA_ROBOT_TEST.git
# Clone additional necessary repositories
cd ..
sudo apt-get install libboost-filesystem-dev
rosdep install --from-paths src --ignore-src -y --skip-keys libfranka
cd ..
```

Ensure you build the libfranka library from source and pass its directory to `catkin_make` when building this ROS package as described in [this tutorial](^1^).

## Building the Workspace

Build the catkin workspace with the following command:

```bash
catkin_make -j4 -DCMAKE_BUILD_TYPE=Release -DFranka_DIR:PATH=/path/to/libfranka/build
source devel/setup.bash
```

## Running the Simulation

To launch the simulation, use the following command:

```bash
roslaunch panda_moveit_config test.launch
```

## Configuration

The ready state of the robot can be set in the 'Set Goal State' tab in Moveit! Rviz. Modify the `config/panda_arm.xacro` file in `panda_moveit_config` to change the ready state or add new states.

## Spawning Objects

To spawn objects in the workspace, use the following command:

```bash
rosrun moveit_test pick_place

```


## Acknowledgements

This project is a modified and extended version of the work done by Erdal Pekel. Special thanks to all contributors and maintainers.

---


