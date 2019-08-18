# **Finding Lane Lines on the Road WRITEUP** 
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)


## REFLECTION

This document is the reflection of the development of the pipeline to find lane lines in a real road, in this case, in the Highway 280 of California.


This document is divided in 3 sections: the first one, is the **pipeline** whit its corresponding experiments. The second one, is the **limitations** of the pipeline. And the last one is the possible **improvements** of the pipeline.

### Pipeline
This approach consist in a sequence of steps to obtain the lane lines of a roadway driving image:

 **Step 1: GrayScale, darken, colour space and color threshold**
 1. Gray Scale, Darken and Color space

<p align="center">
  <img src="test_images/solidWhiteCurve.jpg" width="200" alt="original" />
  <img src="experiments/1_gray_solidWhiteCurve.jpg" width="200" alt="grey" />
  <img src="experiments/2_dark_solidWhiteCurve.jpg" width="200" alt="dark" />
  <img src="experiments/3_hls_solidWhiteCurve.jpg" width="200" alt="hls" />
</p>
<p align="center">
  <img src="test_images/solidYellowCurve.jpg" width="200" alt="original" />
  <img src="experiments/1_gray_solidYellowCurve.jpg" width="200" alt="grey" />
  <img src="experiments/2_dark_solidYellowCurve.jpg" width="200" alt="dark" />
  <img src="experiments/3_hls_solidYellowCurve.jpg" width="200" alt="hls" />
</p>

 2. HLS Colour threshold and final mask
<p align="center">
  <img src="experiments/4_white_solidWhiteCurve.jpg" width="200" alt="white" />
  <img src="experiments/5_yellow_solidWhiteCurve.jpg" width="200" alt="yellow" />
  <img src="experiments/6_mask_solidWhiteCurve.jpg" width="200" alt="mask" />
</p>
<p align="center">
  <img src="experiments/4_white_solidYellowCurve.jpg" width="200" alt="white" />
  <img src="experiments/5_yellow_solidYellowCurve.jpg" width="200" alt="yellow" />
  <img src="experiments/6_mask_solidYellowCurve.jpg" width="200" alt="mask" />
</p>

 **Step 2: Gaussian Blur and Edge Detection**
<p align="center">
  <img src="experiments/8_canny_solidWhiteCurve.jpg" width="200" alt="canny1" />
  <img src="experiments/9_combined_solidWhiteCurve.jpg" width="200" alt="combined1" />
</p>
<p align="center">  
  <img src="experiments/8_canny_solidYellowCurve.jpg" width="200" alt="canny2" />
   <img src="experiments/9_combined_solidYellowCurve.jpg" width="200" alt="combined2" />
</p>

 **Step 3: Define region of interest**
<p align="center">
  <img src="experiments/10_roi_solidWhiteCurve.jpg" width="200" alt="roi" />
  <img src="experiments/9_combined_solidYellowCurve.jpg" width="200" alt="roi" />
</p>
 
 
 **Step 4: Hough Transform**
<p align="center">
  <img src="test_images_output/raw_lines_solidYellowCurve.jpg" width="200" alt="roi" />
  <img src="test_images_output/lines_solidYellowCurve.jpg" width="200" alt="roi" />
</p>

<p align="center">
  <img src="test_images_output/raw_lines_solidYellowCurve.jpg" width="200" alt="roi" />
  <img src="test_images_output/lines_solidYellowCurve.jpg" width="200" alt="roi" />
</p>
 
 
 
 
 
 
 
 
 
 
 
 
 
