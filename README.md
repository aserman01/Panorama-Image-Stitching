# Image Stitching OpenCV
A project for creating a panorama image from two images using SIFT, kNN, RANSAC, Homography and weighted filters.

I implemented a feature matching automatic image stitching algorithm. User inputs two images which have overlapped fields and program creates a wide panorama of both images.

## Algorithm
* Firstly, we turn both images into gray scale and use SIFT (Scale-invariant Feature Transform) Method to detect their keypoints. 
* Using kNN and brute force, we find the most similar keypoints and match them. 
* We compute the homography matrix needed for matched points' transformation.
* Then we use RANSAC (Random Sample Consensus) we find the subset with most inliers and by doing so eliminate outliers.
* With homography matrix, we warp the images.
* Lastly, we use a weighted filter to make transition between both images seamless.

## Optimization
For a better optimization, I tried two different methods.

### Rectangle Masking with Percentage
As we know which image is left and which image is right, we can only scan the right and left part of images by scaning %75 part of an image, program can work in a more optimized manner.

My test results showed that scanning only %75 of the images helps us save 2-3 seconds for each stitching and this value still can increase as we reduce the scan area without losing any details in panorama.

<img width="1085" alt="Screen Shot 2022-08-18 at 11 00 38" src="https://user-images.githubusercontent.com/29065812/185342549-9692d38f-49fd-4a01-a5de-919c9d971dbf.png">


### Bucketing
We can seperate our image into little rectangles and can only take some of those rectangles to save computing time. As these rectangles are homogenously disturbed through our image, precision of the stitching doesn't change.

My test results showed that using 50x50 mask of the images helps us save 4-5 seconds (which is very drastic) for each stitching and this value still can increase as we reduce the scan area without losing any details in panorama.


<img width="1440" alt="Screen Shot 2022-08-18 at 11 34 24" src="https://user-images.githubusercontent.com/29065812/185352395-299a6a63-05bb-438c-9e2a-d67a39a430d5.png">


## Sample

### Input Images

![imageLeft](https://user-images.githubusercontent.com/29065812/184124543-b386111d-9801-4121-8195-89f2008e88c9.jpg)
![imageRight](https://user-images.githubusercontent.com/29065812/184124562-12dcfbab-b328-44c7-ae9a-d9c7d2d0332b.jpg)

### SIFT and kNN Matches
<img width="1440" alt="Screen Shot 2022-08-11 at 14 50 16" src="https://user-images.githubusercontent.com/29065812/184138121-c3f30fe9-509e-4854-aa77-33e905dd98a4.png">

### Weighted Filter

<img width="1440" alt="Screen Shot 2022-08-11 at 11 20 57" src="https://user-images.githubusercontent.com/29065812/184124898-95159c98-6af9-4efb-8f7a-41d9220b4a61.png">

### Output

![Panorama_Final](https://user-images.githubusercontent.com/29065812/184125137-977e2810-aa7a-460f-94fa-8d51473fdacb.png)

