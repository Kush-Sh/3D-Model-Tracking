# 3D Object Tracking

In this project, we are tracking an object in environment with the help of combination of feature detection in consecutives images and lidar point cloud. So, we can calculate TTC with vehicle in front of autonomous system. 

<img src="https://github.com/Kush-Sh/3D-Model-Tracking/blob/main/Images/1st.jpg?raw=true" width="1170" height="496" />


# 1. Findig the same object in multiple images
With the help of key point matching in previous and current image with can be able to detect the 3D object in array of images. As we know vector of DMatch data structure hold the all-matched key points in both images, we the help of looping through all the matched key points we can find all the objects with bounding box associated with it.
If the key point associate with query index present in previous image boxes and point associate with train index present in current image boxes, then that match represents the same box in both the images, hence pertain to same object in both the images.
A key point present in box or not and which box ID, can be calculated with the help of loop of the all boxes present in particular frame. 
Now if the match present in both the frames so the BOX ID of the particular frame (both frames) can be saved as the map of box IDs (paired together) and saved in a vector of matched bounding boxes.

# 2. Compute collision Time with the help of lidar points
Computing the time-to-collision in seconds for all matched 3D objects using only Lidar measurements from the matched bounding boxes between current and previous frame with the of distance, velocity and time relation. For dealing with outliers – average of all points has been taken. So, the error in calculation reduces.

# 3. Finding the keypoints within the bounding box (bounding boxex finds by YOLO detection)
In this task all the matches associate with particular bounding box in both previous frame and current frame saved in bounding box key points matches. A loop has been performed through all the matches points in both frames, if the point key point present in both the frame, that particular match should be save as match key point associated with that box. The problem with these all matches it that, it contains some outliers. So, to remove the outliers, standard deviation is used. 95% percent within two standard deviations is used to remove the far matches in the vector of matches.

# 4. Compute collision time with the help of Camera computation bases
Two successive images collected from MONO camera setup is used to calculated TTC with the common points of interests. MedianDistRation is used to deal with the outliers, below code shows the implementation.



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
