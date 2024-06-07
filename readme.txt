COMPUTER VISION
Homework 01
This Python script performs image stitching and blending using OpenCV and NumPy. The script uses SIFT (Scale-Invariant Feature Transform) to detect and match keypoints between images. It then estimates the homography matrix using RANSAC (Random Sample Consensus) and applies a perspective warp to stitch the images together. The stitched images are then blended to create a seamless panorama.


Requirements
Python 3
•	OpenCV (cv2)
•	NumPy
•	Matplotlib
•	PIL (Python Imaging Library)
Make sure to keep the give the file path correctly before running the code.
The output images will be saved in the same folder which contains your code.


Functions
1.	homogeneous_coordinate(coordinate): Calculates the homogeneous coordinates.
2.	warp(image, homography): Warps the image as per the homography matrix.
3.	getPerspectiveTransform(src, dst): Estimates the homography between source and destination points.
4.	perspective_transform(pts1, H): Applies the homography to the points.
5.	estimate_homography(pts1, pts2, ransac_threshold=4, ransac_iterations=100): Finds the homography matrix using RANSAC.
6.	find_keypts(img1, img2): Finds and matches SIFT keypoints between two images.
7.	match_keypts(good_matches, kp1, kp2): Matches keypoints in two images and estimates the homography using RANSAC.
8.	blend_images(left, middle, left_middle_offset_x, left_middle_offset_y, blend): Stitches images and blends them if required.


Usage
1.	Load the images.
2.	Find keypoints in the images using find_keypts(img1, img2).
3.	Match the keypoints and estimate the homography using match_keypts(good_matches, kp1, kp2).
4.	Warp the source image using warp(img1, H1).
5.	Blend the warped image and the destination image using blend_images(warped_image_source1, np.array(img2), source1_offset_x, source1_offset_y, blend).
6.	Display and save the result.


Note

The script assumes that the images are of the same size and taken from the same camera centre position. Ensure that your input images are properly aligned and have sufficient overlap for accurate stitching.
The blending function currently uses a simple averaging method, which may not produce the best results for images with different lighting conditions or parallax. 
Adjust the blending parameter (`blend`) to create mosaic with or without blending.
(blend = 0 for stitching without blending and 1 for stitching with blending)
ThankYou!

