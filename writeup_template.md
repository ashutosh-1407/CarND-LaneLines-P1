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

The pipeline consists of below steps:
-> image is converted to gray scale
[//examples/gray.jpg]

-> smoothening of image is done using gaussian blur
[//examples/blur_gray.jpg]

-> canny function is used to find the gradients
[//examples/cany_img.jpg]

-> hough transform is done to detect specific lines
[//examples/hough_img.jpg]

-> region of interest is defined to allow lines only in the specific portion of the image
[//examples/roi_img.jpg]

-> images with region of interest and line image found by hough transform are overlapped
[//examples/weight.jpg]

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by:

-> separating left lines and right lines by using the slope value
-> calculated slope and intercept for left lane and right lane based on whether the slope is positive or negative
-> calculating the average slope and intercept value for left and right lanes and plotting them
-> if for some reason, there are no points in left or right lane, i have taken the previous line slope/intercept values and used them

### 2. Identify potential shortcomings with your current pipeline


As of now, the pipeline is able to detect lane lines almost perfectly. But i guess there are still few frames
in the video where the lane lines are not accurate. Also, the pipeline is performing poorly for the
challenge video.


### 3. Suggest possible improvements to your pipeline

One approach is to tune the parameters for the Canny edge detection and HoughLinesP function so that
lane lines can be detected perfectly. Other approach could be to use different color space available and
check to see if lane lines could be detected better using those color spaces.

### Rubric:

1. Have all project files been included with the submission?
I have included both the files

2. Does the pipeline for line identification take road images from a video as input and return an annotated video stream as output?
The pipeline returns an annotated video stream as output and is provided in the test_videos_output folder

3. Has a pipeline been implemented that uses the helper functions and / or other code to roughly identify the left and right lane lines with either line segments or solid lines? (example solution included in the repository output: raw-lines-example.mp4)
Yes, the pipeline has been implemented to identify the lane lines

4. Have detected line segments been filtered / averaged / extrapolated to map out the full extent of the left and right lane boundaries? (example solution included in the repository: P1_example.mp4)
The extrapolation has been done by modifying the draw_lines function and the working is explained above

5. Has a thoughtful reflection on the project been provided in the notebook?
yes, it has been provided.
