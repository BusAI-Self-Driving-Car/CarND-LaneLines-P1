# **Finding Lane Lines on the Road WRITEUP** 
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)


## REFLECTION

This document is the reflection of the development of the pipeline to find lane lines in a real road, in this case, in the Highway 280 of California.


This document is divided in 3 sections: the first one, is the **pipeline** whit its corresponding experiments. The second one, is the **limitations** of the pipeline. And the last one is the possible **improvements** of the pipeline.

### Pipeline
This approach consist in a sequence of steps to obtain the lane lines of a roadway driving image:

 **Step 1: GrayScale, darken, colour space and color threshold**
 1. Gray Scale, Darken and Color space

![alt-text-1](experiments/1_gray_solidWhiteCurve.jpg "title-1") ![alt-text-2](experiments/2_dark_solidWhiteCurve.jpg "title-2")



2. 



3. Gaussian smoothing and Edge detection (Canny method was used in this case)
<img src="test_images_output/canny_edges.jpg" width="380" alt="canny" />
4. Define the region of interest 
<img src="test_images_output/roi_edges.jpg" width="380" alt="ROI" />
5. Apply the Hough Transform
<img src="test_images_output/hough.jpg" width="380" alt="Hough Transform" />

6. Refine the lines to obtain two lines, one for each lane side
<img src="test_images_output/lines_solidWhiteCurve.jpg" width="380" alt="Hough Transform" />


