# AIKIDO Tutorial

## Install dependencies
## Install Aikido dependencies
Add a few custom PPAs necessary for Aikido
```
$ sudo add-apt-repository ppa:dartsim/ppa
$ sudo add-apt-repository ppa:personalrobotics/ppa
$ sudo apt-get update
```

Install build dependencies for Dart
```
$ apt install cmake build-essential libboost-filesystem-dev libmicrohttpd-dev libompl-dev libtinyxml2-dev libyaml-cpp-dev libccd-dev libfcl-dev liboctomap-dev libnlopt-dev liburdfdom-dev
```

Build and install Dart from source
```
$ mkdir ~/ros_dependencies && cd ~/ros_dependencies
$ git clone https://github.com/dartsim/dart.git
$ cd dart
$ git checkout tags/v6.7.3
$ mkdir build && cd build
$ cmake ..
$ make -j4
$ make install
```

Extend your shared library path to include libdart
```
$ echo 'export LD_LIBRARY_PATH="$LD_LIBRARY_PATH:/usr/local/lib"' >> ~/.bashrc
$ source ~/.bashrc
```

Install some miscellaneous dependencies
```
$ apt install ros-kinetic-controller-interface ros-kinetic-transmission-interface ros-kinetic-realtime-tools ros-kinetic-controller-manager ros-kinetic-control-toolbox ros-kinetic-octomap-ros ros-kinetic-srdfdom python-catkin-tools python-pybind11
```

## Setup Instructions
### Setting up the workspace
**Open a terminal and type in following commands**
```bash
# Store your favorite ros workspace path in a env variable ROS_WORKSPACE
# Feel free to replace ~/ros_ws with what you like
$ export ROS_WORKSPACE=~/ros_ws
$ mkdir -p $ROS_WORKSPACE/src && cd $ROS_WORKSPACE
$ wstool init src
$ catkin init
# Store your ros version in a env variable ROS_ROOT_PATH
# example: /opt/ros/kinetic or /opt/ros/melodic
$ export ROS_ROOT_PATH=/opt/ros/kinetic
$ catkin config --extend $ROS_ROOT_PATH
```
### Downloading the Tutorial stack from github
**In the same termial, type in following commands**
```bash
$ git clone https://github.com/hejia-zhang/AIKIDO-Tutorial.git ~/AIKIDO-Tutorial
$ cd $ROS_WORKSPACE/src
$ wstool merge ~/AIKIDO-Tutorial/tutorial.rosinstall
$ wstool up
```
### Building the workspace
**In the same terminal, type in following commands**
```bash
$ cd $ROS_WORKSPACE
$ catkin build
```

## Run demo
**Open a terminal and type in following commands**
```
$ roscore
```
**Open a terminal and type in following commands**
```
$ rviz
```
**Open a terminal and type in following commands**
```
$ source $ROS_WORKSPACE/devel/setup.bash
$ cd $ROS_WORKSPACE/src/libada/src/scripts
$ python simple_trajectories.py
```
