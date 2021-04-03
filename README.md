# 3D Object Tracking

In this project, we are tracking an object in environment with the help of combination of feature detection in consecutives images and lidar point cloud. So, we can calculate TTC with vehicle in front of autonomous system. 

<img src="https://github.com/Kush-Sh/3D-Model-Tracking/blob/main/Images/1st.jpg?raw=true" width="1170" height="496" />


#1. Step 1 - Findig the same object in multiple images
With the help of key point matching in previous and current image with can be able to detect the 3D object in array of images. As we know vector of DMatch data structure hold the all-matched key points in both images, we the help of looping through all the matched key points we can find all the objects with bounding box associated with it.
If the key point associate with query index present in previous image boxes and point associate with train index present in current image boxes, then that match represents the same box in both the images, hence pertain to same object in both the images.
A key point present in box or not and which box ID, can be calculated with the help of loop of the all boxes present in particular frame. 
Now if the match present in both the frames so the BOX ID of the particular frame (both frames) can be saved as the map of box IDs (paired together) and saved in a vector of matched bounding boxes.






In this final project, you will implement the missing parts in the schematic. To do this, you will complete four major tasks: 
1. First, you will develop a way to match 3D objects over time by using keypoint correspondences. 
2. Second, you will compute the TTC based on Lidar measurements. 
3. You will then proceed to do the same using the camera, which requires to first associate keypoint matches to regions of interest and then to compute the TTC based on those matches. 
4. And lastly, you will conduct various tests with the framework. Your goal is to identify the most suitable detector/descriptor combination for TTC estimation and also to search for problems that can lead to faulty measurements by the camera or Lidar sensor. In the last course of this Nanodegree, you will learn about the Kalman filter, which is a great way to combine the two independent TTC measurements into an improved version which is much more reliable than a single sensor alone can be. But before we think about such things, let us focus on your final project in the camera course. 

## Dependencies for Running Locally
* cmake >= 2.8
  * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1 (Linux, Mac), 3.81 (Windows)
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* OpenCV >= 4.1
  * This must be compiled from source using the `-D OPENCV_ENABLE_NONFREE=ON` cmake flag for testing the SIFT and SURF detectors.
  * The OpenCV 4.1.0 source code can be found [here](https://github.com/opencv/opencv/tree/4.1.0)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools](https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory in the top level project directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./3D_object_tracking`.
