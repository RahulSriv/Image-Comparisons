# Image Comparisons
Measures the extent of similarity between two images using OpenCV-Python.

Finding if two images are equal with Opencv, is a quite simple operation.

There are 2 fundamental elements to consider:

The images have both the same size and channels
Each pixel has the same value

The quality of a match is define by the distance. The distance is a number, and the lower this number is, the more similar the features are.
By applying the ratio test we can decide to take only the matches with lower distance, so higher quality.

If we decrease the ratio value, for example to 0.1 we will get really high quality matches, but the downside is that we will get only few matches.
If we increase it we will get more matches but sometimes many false ones.

Considering that high quality images (high quality in this case it means high number of pixels) might have thousands of features, so thousands of 
keypoints while low quality images might have only a few hundreds, we need to find a proportion between the matches found and the keypoints.
We check the number of keypoints of both images using len(kp_1) and len(kp_2) and we take the number of the images that has less keypoints.
Finally we divide the good matches by the number of keypoints. We will get a number between 0 (if there were no matches at all) 
and 1 (if all keypoints were a match) and then we multiply them by 100 to have a percentage score.
