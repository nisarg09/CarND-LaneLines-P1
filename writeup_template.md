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

My pipeline consisted of 5 steps. First, I converted the images to grayscale and hsv. HSV conversion is to detect yellow lines and white lines by applying masks on it. The upper and lower limit of the masks are chosen such that white and yellow lines become clearly visible in the frame. Smoothing image is the next step after the masking applied, the blurred image is then passed for the canny edge detection to detect lane lines in the image using canny edge function. To select the region of the interest from the image vertices are created and calculated by applying values for the four bounds of the trapezoid and applying roi on the image removes false detections. 
The next step is to pass the image for the Houghlines function, which detects the lines, the tuning parameters are selected by testing on test images and fine tuned. 


In order to draw a single line on the left and right lanes, I modified the draw_lines() function by first find the slope of the lines detected and also some lines are partially recognized so we exptrapolate them to draw full length lines. We have two lines one for the left and one for the right, after calculating the slope, the negative sloped lines are left lines and positive sloped lines are right lines. We are collecting them all and deriving the average of them. Once done we'll draw the lines.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the pipeline applied on the challange video it's stumbblng a bit and detection is getting affected. 



### 3. Suggest possible improvements to your pipeline

A possible improvement would be to apply HSL color space instead of HSV color space for better detection in all kinds of surroundings.

Another potential improvement could be to detect region of interest dynamically.
