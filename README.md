## **Finding Lane Lines on the Road** 

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[gray]: ./grayscale_imgs/solidWhiteCurve.jpg "Grayscale"
[blurred]: ./blurred_imgs/solidWhiteCurve.jpg "Blurred"
[canny]: ./canny_imgs/solidWhiteCurve.jpg "Canny"
[masked]: ./masked_imgs/solidWhiteCurve.jpg "Masked"
[hough]: ./hough_imgs/solidWhiteCurve.jpg "Hough"
[weighted]: ./weighted_imgs/solidWhiteCurve.jpg "Weighted"

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

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by creating two lists, one for left line data and one for right. Using the slope of each line in the data I seperated the points into the lists for left and right lane data. 

To draw the interpolated lines on the image, I used numpy's polyfit function to gather the slope and intercept for each set of points in the data from my two lists. I set a maximum y value based upon the size of the image for each line and then plugged all of the extracted data into the formula 
```code x = y - b / m```.

Using this formula I was able to extract the corresponding x for each y coordinate and thus extrapolate points that allowed me to draw lines the full length of each lane.

Below is the output of the pipeline at each step:

## Grayscale
![alt text][gray]
## Blurring
![alt text][blurred]
## Canny Transform
![alt text][canny]
## Masking Region of Interest
![alt text][masked]
## Hough Lines
![alt text][hough]
## Weighted Image Combination
![alt text][weighted]


### 2. Identify potential shortcomings with your current pipeline


- One potential shortcoming is when the road has a curve in it or has a very scenic and noisy landscape. The functions used to gather data points and extract line data might be to rigid and linear to account for the curvature.

- Another shortcoming could be if the road were are night or the camera were to shift our area of interest would be incorrect and we would inaccurately detect lane lines.


### 3. Suggest possible improvements to your pipeline
- A possible improvement would be to add functionality to allow a memory of previous lane lines as the lane finder fails miserably on curved roads currently

- Another potential improvement could be to account for changing light conditoins and more traffic/noisier landscapes