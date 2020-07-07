# Self Driving Car Concepts

### Introduction

This file includes different self driving car concepts that I am in the process of learning and my notes on them. 

### CPU vs GPU

What is the difference between the two and what are the use cases, advantages and disadvantages of using one over the other in self driving cars?

### Autoware and Apollo

### Sensors

Self driving cars have a range of sensors (cameras, lidar, radar, etc.) used in order to assist with performance. What are the main ones that are used, their specifications, what they look like and their advantages and disadvantages?

The sensors consist of a Velodyne HDL-64 3D LiDAR, a PointGrey Grasshopper monocular camera, a PointGrey Bumblebee stereo camera, and a NovAtel PwrPak7
GPS/IMU

### Writing in C++ using Robot Operating System (ROS)

### Lane Detection

Different methods. One example is: First, we convert incoming images into a Bird’s Eye View perspective. Second, we filter the images to obtain lane marking pixels using three independent methods, two based on vision and one based on LiDAR. We then fit a centerline to each of the resulting pixel masks. This results in independent measurements of the centerline which are combined in a single Kalman filter. We model the centerline of the vehicle’s ego-lane as a quadratic. 

What are steerable filters? What are the alternatives? What is the Lateral Challenge?

LiDAR-Based Lane Detection: This method takes advantage of the difference in infrared reflectivity between lane marking paint and road
asphalt. Each laser scan is searched for regions with highintensity gradients. The resulting set of points are then accumulated over several laser scans in order to get a denser result. Scans are accumulated over a sliding window and aligned using Iterative Closest Point. The resulting set of points are then projected into a Bird’s Eye View image

### Semantic Segmentation

https://www.cs.toronto.edu/~tingwuwang/semantic_segmentation.pdf

### 
