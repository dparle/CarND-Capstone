# Udacity Self Driving Car ND Capstone Project

This is the project repo for the final project of the Udacity Self-Driving Car Nanodegree: Programming a Real Self-Driving Car.


### System / Code Structure

![System Overview](imgs/final-project-ros-graph-v2.png "System Overview")


Please use **one** of the two installation options, either native **or** docker installation.

### Native Installation

* Be sure that your workstation is running Ubuntu 16.04 Xenial Xerus or Ubuntu 14.04 Trusty Tahir. [Ubuntu downloads can be found here](https://www.ubuntu.com/download/desktop).
* If using a Virtual Machine to install Ubuntu, use the following configuration as minimum:
  * 2 CPU
  * 2 GB system memory
  * 25 GB of free hard drive space

  The Udacity provided virtual machine has ROS and Dataspeed DBW already installed, so you can skip the next two steps if you are using this.

* Follow these instructions to install ROS
  * [ROS Kinetic](http://wiki.ros.org/kinetic/Installation/Ubuntu) if you have Ubuntu 16.04.
  * [ROS Indigo](http://wiki.ros.org/indigo/Installation/Ubuntu) if you have Ubuntu 14.04.
* [Dataspeed DBW](https://bitbucket.org/DataspeedInc/dbw_mkz_ros)
  * Use this option to install the SDK on a workstation that already has ROS installed: [One Line SDK Install (binary)](https://bitbucket.org/DataspeedInc/dbw_mkz_ros/src/81e63fcc335d7b64139d7482017d6a97b405e250/ROS_SETUP.md?fileviewer=file-view-default)
* Download the [Udacity Simulator](https://github.com/udacity/CarND-Capstone/releases).

### Docker Installation
[Install Docker](https://docs.docker.com/engine/installation/)

Build the docker container
```bash
docker build . -t capstone
```

Run the docker file
```bash
docker run -p 4567:4567 -v $PWD:/capstone -v /tmp/log:/root/.ros/ --rm -it capstone
```

### Port Forwarding
To set up port forwarding, please refer to the "uWebSocketIO Starter Guide" found in the classroom (see Extended Kalman Filter Project lesson), if you access to this nanodegree on Udacity. Else you need to manually [enable port 4567](https://www.howtogeek.com/122641/how-to-forward-ports-to-a-virtual-machine-and-use-it-as-a-server/).

### Usage

1. Clone the project repository
```bash
git clone https://github.com/udacity/CarND-Capstone.git
```

2. Install python dependencies
```bash
cd CarND-Capstone
pip install -r requirements.txt
```
3. Make and run styx
```bash
cd ros
catkin_make
source devel/setup.sh
roslaunch launch/styx.launch
```
4. Run the simulator

### Real world testing
1. Download [training bag](https://s3-us-west-1.amazonaws.com/udacity-selfdrivingcar/traffic_light_bag_file.zip) that was recorded on the Udacity self-driving car.
2. Unzip the file
```bash
unzip traffic_light_bag_file.zip
```
3. Play the bag file
```bash
rosbag play -l traffic_light_bag_file/traffic_light_training.bag
```
4. Launch your project in site mode
```bash
cd CarND-Capstone/ros
roslaunch launch/site.launch
```
5. Confirm that traffic light detection works on real life images

### Other library/driver information
Outside of `requirements.txt`, here is information on other driver/library versions used in the simulator and Carla:

Specific to these libraries, the simulator grader and Carla use the following:

|        | Simulator | Carla  |
| :-----------: |:-------------:| :-----:|
| Nvidia driver | 384.130 | 384.130 |
| CUDA | 8.0.61 | 8.0.61 |
| cuDNN | 6.0.21 | 6.0.21 |
| TensorRT | N/A | N/A |
| OpenCV | 3.2.0-dev | 2.4.8 |
| OpenMP | N/A | N/A |

We are working on a fix to line up the OpenCV versions between the two.

### Compiling on Udacity workspace

If you get following error message:
```
CMake Warning at /opt/ros/kinetic/share/catkin/cmake/catkinConfig.cmake:76 (find_package):
  Could not find a package configuration file provided by "dbw_mkz_msgs" with
  any of the following names:

    dbw_mkz_msgsConfig.cmake
    dbw_mkz_msgs-config.cmake

  Add the installation prefix of "dbw_mkz_msgs" to CMAKE_PREFIX_PATH or set
  "dbw_mkz_msgs_DIR" to a directory containing one of the above files.  If
  "dbw_mkz_msgs" provides a separate development package or SDK, be sure it
  has been installed.
Call Stack (most recent call first):
  styx/CMakeLists.txt:10 (find_package)


-- Could not find the required component 'dbw_mkz_msgs'. The following CMake error indicates that you either need to install the package with the same name or change your environment so that it can be found.
CMake Error at /opt/ros/kinetic/share/catkin/cmake/catkinConfig.cmake:83 (find_package):
  Could not find a package configuration file provided by "dbw_mkz_msgs" with
  any of the following names:

    dbw_mkz_msgsConfig.cmake
    dbw_mkz_msgs-config.cmake

  Add the installation prefix of "dbw_mkz_msgs" to CMAKE_PREFIX_PATH or set
  "dbw_mkz_msgs_DIR" to a directory containing one of the above files.  If
  "dbw_mkz_msgs" provides a separate development package or SDK, be sure it
  has been installed.
Call Stack (most recent call first):
  styx/CMakeLists.txt:10 (find_package)


-- Configuring incomplete, errors occurred!
See also "/home/workspace/CarND-Capstone/ros/build/CMakeFiles/CMakeOutput.log".
See also "/home/workspace/CarND-Capstone/ros/build/CMakeFiles/CMakeError.log".
Invoking "cmake" failed
```

Run the following commands:
```
sudo apt-get update
sudo apt-get install -y ros-kinetic-dbw-mkz-msgs
cd /home/workspace/CarND-Capstone/ros
rosdep install --from-paths src --ignore-src --rosdistro=kinetic -y
```
