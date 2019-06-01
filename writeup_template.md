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

My pipeline consisted of 5 steps. 
  - First, I converted the images to grayscale.
  - Then I blurred this image using a Gaussian Blur.
  - After blurring the image it was run thorugh a Canny transform function to determin the edges of what could possibly be the lines in the image.
  - After applying the Canny transform I specified a region of interest by masking the resulting image to limit my selection to the rough area where I expect to find the lane lines.
  - I then fed the output of the mask to a hough lines function produced a set of solid colored lines on the image where I had specified a region of interest which should indicate the location of the lane lines.
  - The final step was to use a weighted image function to output the combination of my lane line drawings overlayed onto the original image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
