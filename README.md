# Panaroma_image_stitching
Create your own panaroma from scratch
The code provided is designed to perform image stitching, specifically for panorama creation. 
Here are the key operations:
1. Modular Approach: The code is divided into several functions, each performing a 
specific task. This modular approach enhances readability and maintainability.
2. Homography Estimation: The estimate_homography function uses the RANSAC 
algorithm for robust homography estimation. This method is resistant to outliers, 
which are common in keypoint matching.
3. Keypoint Matching: The find_keypts function uses SIFT (Scale-Invariant Feature 
Transform) for keypoint detection and description. It then uses FLANN (Fast Library 
for Approximate Nearest Neighbors) for efficient matching of keypoints.
4. Image Warping: The warp function applies the estimated homography to the source 
image to align it with the destination image. It uses homogeneous coordinates for this 
transformation.
5. Image Blending: The blend_images function stitches the warped source image and 
the destination image together. It offers an option to blend overlapping regions for a 
smoother transition.
6. Normalization: The homography matrix and the transformed points are normalized to 
ensure consistent results.
7. Error Handling: The code includes assertions and error handling to ensure that the 
inputs meet the necessary requirements (e.g., at least four point pairs for homography 
estimation).
8. Use of Libraries: The code leverages several Python libraries such as NumPy for 
numerical operations, OpenCV and PIL only for reading images, saving images 
and finding keypoint matches using cv2.FlannBasedMatcher(), and Matplotlib for 
displaying the result. These libraries provide efficient and reliable pre-implemented 
methods.
These design choices collectively ensure that the code is robust, efficient, and capable of 
generating high-quality panoramas from a set of images.
Design Choices:
• RANSAC is used for Homography calculation
• Blending operation: compares the mean pixel values of corresponding regions in the 
two images and selects pixels from one image over the other based on this 
comparison.
• Inverse warping technique is used
• Nearest-neighbor interpolation is used in Inverse warping

Output
Outputs with blend for given set of images:

Mosaic of img1 and img2:				
![image](https://github.com/niveditaapr21/Panaroma_image_stitching/assets/42715946/4c900920-4ea5-424e-94e2-2a76f1bc5605)

Mosaic of img1, img2 and img3:
![image](https://github.com/niveditaapr21/Panaroma_image_stitching/assets/42715946/0e7769ba-56a0-43cf-a933-901b23d6f7ab)

Mosaic of img1, img2, img3 and img4:
![image](https://github.com/niveditaapr21/Panaroma_image_stitching/assets/42715946/7a6dcfff-6355-4ed8-a3b3-27890c0068b1)

Mosaic of img1, img2, img3, img4 and img5:
![image](https://github.com/niveditaapr21/Panaroma_image_stitching/assets/42715946/a4f0e831-5c5a-43c4-aeb7-a9252b433157)

Mosaic of img1, img2, img3, img4 and img5(without blend):
![image](https://github.com/niveditaapr21/Panaroma_image_stitching/assets/42715946/e77bc577-5eaf-4cd6-995e-ee1ac3dcb757)

Important Observations:
•	Blending operation needs to be improved.
•	Reference is taken as the rightmost image at each subsequent step, to improve the structure of mosaic (i.e. make it less skewed on one side) centre image can be taken as the reference while warping and stitching. I have tried to build the mosaic taking centre image as the reference and have obtained the following result:
![image](https://github.com/niveditaapr21/Panaroma_image_stitching/assets/42715946/66ea6112-1602-4e3e-a637-bcacd0eec710)
