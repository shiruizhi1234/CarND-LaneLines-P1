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

My pipeline consisted of 5 steps. First, I converted the images to HSL from RGB color space, then I use color selection to get both yellow and white color from the image. Then I convert the image to a grayscale and use a region selection to select only part of the image that we interest. Next I use Gaussian Blur to smooth the image and then use Canny Edge Detection to find edges. After that I transform the image to Hough space to find lines and connect those lines.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by first separating lines by their slope. Lines with negative slope are on the left side, while lines with positive slope are on the right side. Then I use a linear regression to approximate the slope and intercept for the left lane and right lane. Finally I draw the two lanes from the bottom to the middle of the image. 

### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when there is both an old lanes and new lanes, especially when the track of old lanes are still visible.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to record current lane position. Find lanes that could continue this trajectory.
