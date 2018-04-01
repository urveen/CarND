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

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I 
Second Use a gaussian kernel to filter the image.This helps in getting rid of noisy parts of the image which makes the next steps more reliable
Third Perform canny edge detection.This step basically detects the edges in the image with the help of the image gradient and hysteris 
Fourth Mask the region of interest 
Fifth Use hough transformation to find lines from the edges.Transforms each point to a line in hough space where the intersection of these lines shows the presence of a line in image space.
Finally Draw straight white lines on the lanes in the image 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

1. Get the slope of each line and thresh all lines smaller than 0.5
2. Calculate the size of each line and take the average slope of the biggest x lines.
	I used x=5
3.Get b with b = y - m * x and again get average b of the x biggest lines.
4. With this line equation we can extrapolate to the bottom and the top of the lines.


If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...
- Might not work effectively in different kinds of lighting conditions i.e. real life road conditions
- Won't be that effective on turns

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
1. perfectly tweaked parameters for the hough transformation
2. a non-linear line fitting for detecting curves more reliable
3. my smoothing window was set to 10, which is around 0.4s. This can eventually lead to problems in fast transitions.
4. a deep learning model
