# Image_Stitching
A project for creating a panorama image from two images using SIFT, kNN, RANSAC, Homography and weighted filters

I implemented a feature matching automatic image stitching algorithm. User inputs two images which have overlapped fields and program creates a wide panorama of both images.

## Algorithm
* Firstly, we turn both images into gray scale and use SIFT (Scale-invariant Feature Transform) Method to detect their keypoints. 
* Using kNN and brute force, we find the most similar keypoints and match them. 
* We compute the homography matrix needed for matched points' transformation.
* Then we use RANSAC (Random Sample Consensus) we find the subset with most inliers and by doing so eliminate outliers.
* With homography matrix, we warp the images.
* Lastly, we use a weighted filter to make transition between both images seamless.

## Sample

### Input Images

![imageLeft](https://user-images.githubusercontent.com/29065812/184124543-b386111d-9801-4121-8195-89f2008e88c9.jpg)
![imageRight](https://user-images.githubusercontent.com/29065812/184124562-12dcfbab-b328-44c7-ae9a-d9c7d2d0332b.jpg)

### SIFT and kNN Matches
<img width="1440" alt="Screen Shot 2022-08-11 at 11 14 16" src="https://user-images.githubusercontent.com/29065812/184124799-22c4480b-747e-4bc7-b1e0-377e11b66044.png">

### Weighted Filter

<img width="1440" alt="Screen Shot 2022-08-11 at 11 20 57" src="https://user-images.githubusercontent.com/29065812/184124898-95159c98-6af9-4efb-8f7a-41d9220b4a61.png">

### Output

![Panorama_Final](https://user-images.githubusercontent.com/29065812/184125137-977e2810-aa7a-460f-94fa-8d51473fdacb.png)

