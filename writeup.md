# **Finding Lane Lines on the Road WRITEUP** 
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)


## REFLECTION

This document is the reflection of the development of the pipeline to find lane lines in a real road, in this case, in the Highway 280 of California.


This document is divided in 3 sections: the first one, is the **pipeline** whit its corresponding experiments. The second one, is the **limitations** of the pipeline. And the last one is the possible **improvements** of the pipeline.

## Pipeline
This approach consist in a sequence of steps to obtain the lane lines of a roadway driving image. As examples, in this work I show the pipeline with two different images, the first one with white mark lanes, and the other with a yellow lane mark. 

### Step 1: GrayScale, darken, color space and color threshold
One of the most important steps is how detect properly the lane marks, and this is crucial in the challenge video overall. The different day conditions affect the detection, so I have tried to do my best in this step. 

Gray scale is basic in this problem, it allows to get the canny edges. But to make more robust the pipeline I have change the gamma of the gray image darken it, thus, I get better detection the white colors.

Using HLS space with a color threshold allows the algorithm to detect better yellow and white. The difficulty lies in find the correct thresholds.
Finally I have merge both methods to get the best of them.

 **1. Gray Scale, Darken and Color space**
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

 **2. HLS Colour threshold and final mask**
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

### Step 2: Gaussian Blur and Edge Detection
To detect the edges I have used Canny algorithm. There are other edge detectors like Sobel or Prewitt, but, for this problem, canny work good.
Internally, Canny applies a gaussian blur with 5x5 kernel.

I have found that the best thresholds for Canny are between 50 to 150, but it can be reduced to 70 and 140 and works even better.
<p align="center">
  <img src="experiments/8_canny_solidWhiteCurve.jpg" width="200" alt="canny1" />
  <img src="experiments/9_combined_solidWhiteCurve.jpg" width="200" alt="combined1" />
</p>
<p align="center">  
  <img src="experiments/8_canny_solidYellowCurve.jpg" width="200" alt="canny2" />
   <img src="experiments/9_combined_solidYellowCurve.jpg" width="200" alt="combined2" />
</p>

### Step 3: Define region of interest
The image have so much more information that is needed, and it can confound the algorithm, so to simplify the problem I have focused the vision in the front area of the car. 

To don't have problems with the image resolution I have defined this points: `(0,imshape[0]),(0.47*imshape[1], 0.6*imshape[0]), (0.54*imshape[1], 0.6*imshape[0]), (imshape[1],imshape[0])`

As you can see on the images, one the are inside the region of interest  keeps the edges.
<p align="center">
  <img src="experiments/10_roi_solidWhiteCurve.jpg" width="200" alt="roi" />
  <img src="experiments/9_combined_solidYellowCurve.jpg" width="200" alt="roi" />
</p>
 
 
### Step 4: Hough Transform
The last step is the Hough Transform. As a highway is almost a straight line, with the edges and the hough algorithm you can detect shapes, as lines. The left images show the detection of the lines.

But, to get the left and right lines (right images) there are other steps to consider. First, you need to get the slope and intercept of each line.  Second, group the lines in clusters, in this case, 2 clusters (left and right) erasing the horizontal and too vertical lines. Third, filter the lines that have a slope and intercept too different to the mean value of all the lines (it prevent outliers, but in most of cases is not necessary), and use a low-pass filter to obtain more stability in the lines using previously information, because the lines should not have a very quick change in slope. Fourth, draw the line with the new slope and intercept.

<p align="center">
  <img src="test_images_output/raw_lines_solidYellowCurve.jpg" width="200" alt="raw" />
  <img src="test_images_output/lines_solidYellowCurve.jpg" width="200" alt="filtered" />
</p>

<p align="center">
  <img src="test_images_output/raw_lines_solidYellowCurve.jpg" width="200" alt="raw" />
  <img src="test_images_output/lines_solidYellowCurve.jpg" width="200" alt="filtered" />
</p>

## Limitations

## Possible Improvements 
 
 
 
 
 
 
 
 
 
 
 

