# **Finding Lane Lines on the Road** 

## Writeup

---

**Finding Lane Lines on the Road**

[image1]: ./test_images/solidWhiteRight.jpg "Lane Example"
[image2]: ./test_images/img_gray.jpg "Image on gray scale"
[image3]: ./test_images/blur_image.jpg "Image after Gaussian Blur"
[image4]: ./test_images/canny_image.jpg "Image after canny Operator"
[image5]: ./test_images/masked_image_result.jpg "ROI image"
[image6]: ./test_images/line_image.jpg "Lane Image"

![alt text][image1]

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---
## Overview:

The main goal of this project consist to open a video file, manipulate frames and find lanes. 
Then the result will be stored in mp4 file.

We can divide the project in steps:
* Open video files
* Convert it to gray scale
* Apply Gaussian Blur
* Apply Canny edge detection
* Define a Region of interest (ROI) in Image
* Apply a Hough Transform
* Draw Lines on original frame
* Assemble output video
 
  This Project was made in pycharm IDE, not in jupyter notebook.
---

### Reflection

### 1. Describe your pipeline. 

My pipeline consisted of 7 steps. 

The first step consist to open files using Opencv functions to do that. In this functions 
you need to specify which codec you will use.

Then, for each frame I apply the steps below. 

The first one is to convert frame to gray scale. 
The conversion was made using Opencv function cvtColor. 

![alt text][image2]

Next step consist to apply a Gaussian blur to frame.
The chosen kernel size was 5. Bigger kernel size implies more power of processing and the result was so much better.
 
![alt text][image3]
 
In Canny detector operator I consider 50 and 150 for lower and upper threshold values.

![alt text][image4]

Another important step was consider a region of interest. As camera pose will be always the same in this project, 
the region where to find lanes will be always the same. Then, we define a polygon region and make a bitwise and operation.

![alt text][image5]

The resulting frame is now ready to find lanes using Hough Transform, and applied do original frame to assemble output video.

![alt text][image6]

### 2. Identify potential shortcomings with your current pipeline

The main potential shortcoming is the region in the lower part of image. Sometimes Hough transform didn't find lines in that region.
The algorithm didn't have a good performance in challenge video.


### 3. Suggest possible improvements to your pipeline

The are a lot of improvements that can be done.
** Improve reliability of lines in the lower part of image.
*Improve performance in challenge video.
*Make some visual improvements to show the result.
