
**The current pipeline[Solution](P1.ipynb):**
* Convert the image to the gray scale
* Remove the noise with Gaussion kernel
* Apply the Canny edge detection
* Mask the region of interest
* Apply the Hough transform
* Draw the lane lines from the Hough lines

Example:
![pipeline]
(example/example.jpg)

Video results:
![white]
(white.gif)

![yellow]
(yellow.gif)

Comments: The current pipeline works reasonably well on the 'White' and 'Yellow' videos. However a few things could be improved in the future.
* The region of interest is masked hard-codedly. A flexible method is needed to handle various cases, such as different videos, curves etc.
* Hough transform is applied to left or right Canny edges. The sign of slope is used to distinguish left or right. An assertion function is needed to handle the ill-defined slope and intercept.
* The lane lines are drawn by taking the median of the slope and the median of intercept for left and right cases, respectively. Using the median is better than using the mean to remove the outliers. One may further improve the lane drawing by using the slopes and intercepts from a few dominant Hough lines.
* Alternative way to draw the lane lines would be to fit the Hough points on each side respectively. However it is important to remove the outlier points to have an unbiased fit. Therefore machine learning techniques can be applied here. In the video, the lane lines are a little bit 'shaking'. This can be improved by running a time(frame) average to smooth out.

**Regarding the challenge video**
* The tree shadow affects strongly the Canny edge detection, i.e the gradient.
* One possible solution is to use cv2.inRange() to map out the yellow.
* The large curves could be fitted with polynomial models instead of linear
models."
