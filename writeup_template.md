# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"
[image2]: ./test_images_output/solidWhiteCurve.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps:

- converted the test input images to grayscale.

- applied the Gaussian smoothing blur in order to quit off the noise and possible image mistakes. 

- found the edges on the image by using the Canny detector algorithm.

- Made a mask over the image of edges which encloses the area of interest

- Transformed the space on the image using the Hough transform to get the lines in the image. I mean, link the bordes found with algorithm of Canny

- In order to draw a single line on the left and right lanes, I modified the draw_lines() function by getting the slope and intercept of each line found by Canny algorithm. By using polifyt function, I averaged the data to obtain a unique slope and intercept. Therefore, i applied this parameters in the lower point in the image where the street lines are located. 

- overlap the drawed lines on the orgin image to visualize the image with the lines found.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]

![alt text][image2]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the image/video have more than one parallel lines to street lines, the code does not work very good like the canny edge detector as well. Since that, the hough space finds other lines with the same shape of the street lines so, the draw lines functions includes this data in the average of the slope and intercept. Therefore, the lines drawn are incorrects or has a little gap from the corrects. 

Another deficiency could be when the lines on the street are different from the white color, the algorithm does not work very well too. Finally, based on the theory, the code will not work exactly when the light changes in the environment. It means that, in the dark environment, the lines of the street will not be found.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to change the gray space for another that had included the parameter of the ligth intensity, for example, HSV or LAB space. 

Another potential improvement could be to use more complex algorithm in order to find the lines parameters. For example, by using CNN to get the parameters slope and intercept values.