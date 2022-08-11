# Image_Stitching
A project for creating a panorama image from two images using SIFT, kNN, RANSAC, Homography and weighted filters

I implemented a feature matching automatic image stitching algorithm. User inputs two images which have overlapped fields and program creates a wide panorama of both images.

##Algorithm
*Firstly, we turn both images into gray scale and use SIFT (Scale-invariant Feature Transform) Method to detect their keypoints. 
*Using kNN and brute force, we find the most similar keypoints and match them. 
*We compute the homography matrix needed for matched points' transformation.
*Then we use RANSAC (Random Sample Consensus) we find the subset with most inliers and by doing so eliminate outliers.
*With homography matrix, we warp the images.
*Lastly, we use a weighted filter to make transition between both images seamless.
