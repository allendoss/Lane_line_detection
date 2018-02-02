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

The pipeline used in the code consisted of the following steps.

1. First, the individual frames in the videos were extracted using the functions in the moviepy library

2. The image was then passed to the function 'imageProcessing'

3. Here the image was converted to a grayscale image for canny edge detection followed by a Hough line detection

4. The drawLines function performs the following:
  a. Divided the hough lines in two groups-on the right side of the center of the image and the other group on the left using the slopes to differentiate between them
  b. The coordinates of all the right lane lines are put in an array. A polynomial of degree one is used to interpolate these points. The process is repeated for left lane lines
5. The lines from the previous step is weighted using the weightedImg function and is overlapped over the original image

### 2. Identify potential shortcomings with your current pipeline

The current pipeline has the following shortcomings:
1. In case of images with shadow over the lane lines the line detection fails
2. The lane lines are straight, this implies in situations with curved lane lines the code fails to produce curved lines


### 3. Suggest possible improvements to your pipeline

The following could be improved:
1. use linear regression to better fit the lines
2. use HSV and HSL color space to better identify the appropriate lane lines in the challenge video
