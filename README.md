# Gocartor-2130-
Gocartor2130 ROS package C++ for data collection
### Overview
This repository holds code of a [ROS](http://www.ros.org) package for point cloud acquisition with  [Gocator3100](http://lmi3d.com/products/gocator/snapshot-sensor) 3D cameras. It is basically a ROS wrapper of the low-level API provided by [LMI Technologies](http://lmi3d.com), the manufacturer of the camera. 

![Camera and cloud at rviz](https://github.com/beta-robots/gocator_3100/blob/master/media/gocator_3100_ros_pkg.png)

### Dependencies
The package has been tested with the following dependencies:
* Ubuntu 16.04
* CMake + gcc
* [ROS Kinetic](http://wiki.ros.org/indigo/Installation/Ubuntu)
* [Point Cloud Library v1.8](http://www.pointclouds.org/) (shipped with ROS Kinetic)
* GoSDK library (propietary library from manufacturer LMI Technologies)

To install GoSDK dependency, the following steps are required: 

1. With a Serial Number of a device, register as a customer at the [LMI website](http://downloads.lmi3d.com/)
2. Download the SDK from the [LMI website](http://downloads.lmi3d.com/) (file 14400-4.2.5.17_SOFTWARE_GO_SDK.zip)
3. Uncompress GoSDK
4. Build GoSDK
```shell 
$ cd GO_SDK/Gocator
$ make -f GoSdk-Gnu.mk 
```

### Download
```shell
$ git clone https://github.com/beta-robots/gocator_3100.git
```

### Build
1. Indicate, by editing the CMakeLists.txt of this package (line 58), where GoSDK library is placed (This point should be improved , see issue #7)
2. The build procedure is the ROS-catkin standard.From your ROS workspace: 
```shell
$ catkin_make --only-pkg-with-deps gocator_3100 
```

### Execute

1. Plug your camera correctly, in terms of power, signal and **grounding!**
2. Properly edit the config/gocator_3100_params.yaml according your configuration and needs. 
3. Call the launch file. From the package folder would be
```shell
$ roslaunch launch/gocator_3100.launch
```
### TODO yimin

GoSDK version: 14400-6.1.20.8_SOFTWARE_GO_SDK.zip

### How to compile GoSDK

How to compile GoSDK

1. Download the SDK from the LMI website (file 14400-6.1.20.8_SOFTWARE_GO_SDK.zip)
2. Uncompress "14400-6.1.20.8_SOFTWARE_GO_SDK.zip" to GoSDK 
3. Bulid GoSDK

   1)  copy folder GO_SDK, which is inside the extracted folder to path ~/
   2)  Switch from different build types.

       To switch Build Type between "Debug" and "Release", you need to adjust three files in total.

       ~/GO_SDK/Platform/kApi/kApi-Linux_X64.mk
       ~/GO_SDK/Gocator/GoSdk/GoSdk-Linux_X64.mk
       ~/GO_SDK/Gocator/GoSdk/GoSdkExample-Linux_X64.mk

       find following block in these three files, and change it to "Debug" or "Release", 
       then the generated libs with be generated and put to the corresponding folders.

       ifndef config
	        config := Release
       endif

    3) $ cd GO_SDK/Gocator
    4)  $ make -f GoSdk-Gnu.mk 

4. This package has been tested with the the following dependencies:

   . Ubuntu 16.04
   . Cmake-3.3.2
   . ROS kinetic
   . PCL libray: pcl-pcl-1.8.0
   . OpenCV 3.3

   . Firmware: Gocator 21xx Firmware - Version 6.1.20.8


     
