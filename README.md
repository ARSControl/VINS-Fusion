# VINS-Fusion (Fork)

### *Code adapted for OpenCV 4, Ceres 2.1, and ROS Noetic!*

This repository is a fork of [VINS-Fusion](https://github.com/HKUST-Aerial-Robotics/VINS-Fusion), adapted and tested for **NVIDIA Jetson Nano** running **Ubuntu 20.04** with **ROS Noetic**.  
The main modifications include support for modern dependencies and integration with Intel RealSense cameras via a custom fork of the `realsense-ros` wrapper.

---

## VINS-Fusion Overview
<img src="https://github.com/HKUST-Aerial-Robotics/VINS-Fusion/blob/master/support_files/image/vins_logo.png" width = 55% height = 55% div align=left />
<img src="https://github.com/HKUST-Aerial-Robotics/VINS-Fusion/blob/master/support_files/image/kitti.png" width = 34% height = 34% div align=center />

VINS-Fusion is an optimization-based multi-sensor state estimator for accurate self-localization in autonomous systems (drones, cars, AR/VR).  
It extends [VINS-Mono](https://github.com/HKUST-Aerial-Robotics/VINS-Mono) and supports multiple visual-inertial configurations:
- **Stereo cameras**  
- **Mono camera + IMU**  
- **Stereo cameras + IMU**  
- Experimental GPS fusion  

**Features:**
- Multiple sensor setups (stereo/mono+IMU)  
- Online spatial calibration (camera–IMU extrinsics)  
- Online temporal calibration (camera–IMU time offset)  
- Visual loop closure  



## Requirements

This fork has been tested on:

- **NVIDIA Jetson Nano**  
- **Ubuntu 20.04**  
- **ROS Noetic**  
- **OpenCV 4**  
- **Ceres Solver 2.1** ([Download & Build Instructions](http://ceres-solver.org/installation.html))
- **realsense-ros (custom fork)**: [Forked wrapper](https://github.com/ARSControl/realsense-ros.git)
- **cv_bridge**: [link](https://github.com/ros-perception/vision_opencv.git)  

Other dependencies follow the original [VINS-Fusion requirements](https://github.com/HKUST-Aerial-Robotics/VINS-Fusion).



## Installation

1. Clone this repository:
```bash
cd ~/catkin_ws/src
git clone https://github.com/ARSControl/VINS-Fusion.git
```

2. Install [Ceres 2.1](https://ceres-solver.googlesource.com/ceres-solver/+/refs/tags/2.1.0)

3. Install the realsense-ros custom wrapper
```bash
cd ~/catkin_ws/src
git https://github.com/ARSControl/realsense-ros.git
```

4. Install cv_bridge
```bash
cd ~/catkin_ws/src
git https://github.com/ros-perception/vision_opencv.git
```

5. Build
```bash
cd ~/catkin_ws/src
catkin build
```
   

## Usage

The system is typically split between the **companion computer (Jetson Nano)**, which handles the sensor processing and VINS estimator, and the **host PC**, which visualizes the results in RViz.  

### On the Jetson Nano (companion computer)
Launch the VINS estimator with a RealSense camera:
```bash
roslaunch vins_estimator vins.launch
```

### On the Host PC
```bash
roslaunch vins_estimator rs_vins.launch
```

You can also play back datasets on the Jetson Nano (see the original VINS-Fusion datasets page) while monitoring results on the host PC with RViz.


## Notes
- Optimized for Jetson Nano (4GB RAM). For better performance, adjust the number of feature points in config/*.yaml.

- Works best with the forked RealSense wrapper due to compatibility fixes.

- Tested with Intel RealSense D435i camera.


### Acknowledgment

- Original work: [VINS-Fusion by HKUST](https://github.com/HKUST-Aerial-Robotics/VINS-Fusion)

- [Ceres solver](http://ceres-solver.org/index.html)

- [Intel RealSense ROS Wrapper](https://github.com/IntelRealSense/realsense-ros)

## Contacts

For questions, issues, or collaboration related to this fork:  

- **Maintainer:** Mattia Catellani
- **Email:** mattia.catellani@unimore.com  
- **GitHub:** [@MatCat960](https://github.com/MatCat960)  

Feel free to open an issue or pull request in this repository.