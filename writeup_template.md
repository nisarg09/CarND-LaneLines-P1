# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I converted image to HSV color space to find white and yellow markers clearly. Third step is to combined mask on gray image and apply for smoothing. Once smoothing is done the canny detection is applied by configuring threshold values. The output image is applied for Houghlines detection by tuning rho, threshold, min_lines and max_gap etc. 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by first calculating the slope of the lines, the left line will have slope in negative and right line will have slope in positive, some lines are partially recognized and to fill them extrapolation is done and then lines are drawn on the image.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when line detection not smooth in challange video.

Another shortcoming could be tuning hough parameters properly for better line segment detections.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use HSL color space
Another potential improvement could be to detect roi dynamically.
