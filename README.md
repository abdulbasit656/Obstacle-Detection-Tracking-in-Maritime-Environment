# Obstacle-Detection-Tracking-in-Maritime-Environment
A robust obstacle detection and tracking system for USV in marine environments using CNN algorithm YOLO for detection and Extended Kalman Filter for tracking using ROS platform developed in C++ language.

# Installation
## Prerequisites
Ubuntu 20.04. NVIDIA CUDA support. * npm

## Install ROS Noetic

Install ROS Noetic following the instructions at the official installation page.

Be sure to source the ROS installation folder, sh $ echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc

## Create the catkin workspace

Following the flow described in the official ROS website, sh $ mkdir -p ~/Documents/catkin_obstacle/src $ cd ~/Documents/catkin_obstacle/ $ catkin_make
## Install Darknet
1. Import the package. This will take a while as it will also install the YOLO weights. sh $ cd ~/Documents/catkin_obstacle/src/ $ git clone --recursive https://github.com/leggedrobotics/darknet_ros

2. Rename the cloned repo folder as darknet_ros.

3. CUDA properties configuration. In darknet_ros/darknet/Makefile and in darknet_ros/darknet_ros/CMakeLists.txt, replace -gencode arch=compute_30,code=sm_30 -gencode arch=compute_35,code=sm_35... with your CUDA 

4. architecture and gencode, which you should be able to find here. For example, in the case of RTX 3050, it's -gencode arch=compute_86,code=sm_86.

(Optional) Try a check compilation by running the following commands. The parameter -DCMAKE_BUILD_TYPE=Release is necessary to compile with optimizations. sh $ cd ~/Documents/catkin_obstacle/ $ catkin_make -DCMAKE_BUILD_TYPE=Release After running this, no Darknet-related error message should appear. If it does, solve it before proceeding. Some CUDA or PCL related error should popup, which you solve by following the next steps.

## Install PCL

Read https://pcl.readthedocs.io/projects/tutorials/en/pcl-1.11.0/gpu_install.html. The CUDA enabling part is important since the point cloud clustering works with pcl CUDA functions.
Now install PCL version 1.10 from Github according to these instructions.

**The code repository is not for the public**
