# **Finding Lane Lines on the Road** 

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[SolidWhiteCurve]: ./test_images_output/solidWhiteCurve.jpg "Solid White Curve"
[SolidWhiteRight]: ./test_images_output/solidWhiteRight.jpg "Solid White Right"
[SolidYellowCurve]: ./test_images_output/solidYellowCurve.jpg "Solid Yellow Curve"
[SolidYellowCurve2]: ./test_images_output/solidYellowCurve2.jpg "Solid Yellow Curve"
[SolidYellowLeft]: ./test_images_output/solidYellowLeft.jpg "Solid Yellow Left"
[WhiteCarLaneSwitch]: ./test_images_output/whiteCarLaneSwitch.jpg "White Car Lane Switch"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps:
  1. Convert image to grayscale
  2. Apply Gaussian blur with a kernel size of 5 pixels
  3. Apply a Canny transform with a low threshold of 40 pixels and a high threshold of 140 pixels
  4. Get Hough lines from resulting image
  5. Only keep the region of interest (the bottom portion of the image where the lanes reside)
  6. Apply lines onto the original image

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by separating all lines based on their slopes (positive slopes referred to left line, while negative slopes referred to right line). Additionally, I only kept the line with the greatest length for each side.

### 2. Identify potential shortcomings with your current pipeline

The current pipeline is a bit jittery and sometimes does not pick up the lane correctly.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to consider incorporating previously viewed frames when drawing the lines for the current frame's lanes. Realistically, the lanes shoud not change drastically among a close set of frames.
