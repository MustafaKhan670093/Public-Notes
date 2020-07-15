# Self Driving Car Concepts

### Introduction

This file includes different self driving car concepts that I am in the process of learning and my notes on those topics. 

### CPU vs GPU.   (and FPGAs ?)

What is the difference between the two and what are the use cases, advantages and disadvantages of using one over the other in self driving cars?

The main difference between CPU and GPU architecture is that a CPU is designed to handle a wide-range of tasks quickly (as measured by CPU clock speed), but are limited in the concurrency of tasks that can be running. A GPU is designed to quickly render high-resolution images and video concurrently.

Because GPUs can perform parallel operations on multiple sets of data, they are also commonly used for non-graphical tasks such as machine learning and scientific computation. Designed with thousands of processor cores running simultaneously, GPUs enable massive parallelism where each core is focused on making efficient calculations.(Source: https://www.omnisci.com/technical-glossary/cpu-vs-gpu)

### Autoware and Apollo

### Sensors

Self driving cars have a range of sensors (cameras, lidar, radar, etc.) used in order to assist with performance. What are the main ones that are used, their specifications, what they look like and their advantages and disadvantages?

The sensors consist of a Velodyne HDL-64 3D LiDAR, a PointGrey Grasshopper monocular camera, a PointGrey Bumblebee stereo camera, and a NovAtel PwrPak7
GPS/IMU

### Writing in C++ using Robot Operating System (ROS)

Robot Operating System is robotics middleware. Although ROS is not an operating system, it provides services designed for a heterogeneous computer cluster such as hardware abstraction, low-level device control, implementation of commonly used functionality, message-passing between processes, and package management.

### Lane Detection

Different methods. One example is: First, we convert incoming images into a Bird’s Eye View perspective. Second, we filter the images to obtain lane marking pixels using three independent methods, two based on vision and one based on LiDAR. We then fit a centerline to each of the resulting pixel masks. This results in independent measurements of the centerline which are combined in a single Kalman filter. We model the centerline of the vehicle’s ego-lane as a quadratic. 

What are steerable filters? What are the alternatives? What is the Lateral Challenge?

LiDAR-Based Lane Detection: This method takes advantage of the difference in infrared reflectivity between lane marking paint and road
asphalt. Each laser scan is searched for regions with highintensity gradients. The resulting set of points are then accumulated over several laser scans in order to get a denser result. Scans are accumulated over a sliding window and aligned using Iterative Closest Point. The resulting set of points are then projected into a Bird’s Eye View image

Does camera-lidar fusion improve performance?

This paper: https://arxiv.org/pdf/1809.07941v1.pdf and this github repo: https://github.com/Shuijing725/ece498sm_project say it does improve performance.

### Semantic Segmentation

https://www.cs.toronto.edu/~tingwuwang/semantic_segmentation.pdf

### Using RANSAC to reject outliers

### Kalman Filter

Understanding the technical math and several programming examples + use cases of a kalman filter (also evaluate different types of kalman filters)

Kalman filtering is an algorithm that provides estimates of some unknown variables given the measurements observed over time.

### Stop Sign Detection

Our Stop Sign Detector consists of a Haar Cascade classifier. Compared to an alternative deep learning object detector such as YOLO, Haar Cascades run very fast on CPUs. They are also very simple to train and tune. We trained our classifier using OpenCV’s Haar Cascade trainer on a custom hand-labeled dataset. We obtained the best results when images were first pre-processed using adaptive histogram equalization. Once a Stop Sign is localized in a camera frame, we determine its relative depth using LiDAR.

### What is a ProportionalIntegral (PI) controller, a lateral controller and a feedback-linearized controller (FBL)?

### What is Model Predictive Control (MPC) ?

### Using the Grid Map and Elevation Mapping libraries to create a 2.5D gravity-aligned elevation map around the vehicle

### Experiments to test the effectiveness of an improvement in the design and structure of a self driving car

### What are  Universal Transverse Mercator (UTM) coordinates?

### SAE levels of autonomy

### What is redundancy?

In engineering, redundancy is the duplication of critical components or functions of a system with the intention of increasing reliability of the system, usually in the form of a backup or fail-safe, or to improve actual system performance.

### What is Optical Flow?

