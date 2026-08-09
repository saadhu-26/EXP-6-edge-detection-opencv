# EXP-6-edge-detection-opencv
## Aim
To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

## Software Required
- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (cv2)
- NumPy
- Matplotlib
## Algorithm
### Step 1:
Import all the necessary modules for the program.

### Step 2:
Load an image using cv2.imread().

### Step 3:
Convert the image to grayscale.

### Step 4:
Apply Sobel operator using OpenCV to detect edges.

### Step 5:
Apply Prewitt operator using custom kernels.

### Step 6:
Apply Roberts operator using custom kernels.

### Step 7:
Apply Laplacian operator using OpenCV.

### Step 8:
Apply Canny edge detector using OpenCV.

### Step 9:
Display all edge-detected images for comparison.

## Developed By
- #### Name: SAADHANA A
- #### Register No: 212225240126

## Program
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
image = cv2.imread('download (1).jpg') 
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')
```
```
sobel_x = cv2.Sobel(gray_image, cv2.CV_64F, 1, 0, ksize=5) 
sobel_y = cv2.Sobel(gray_image, cv2.CV_64F, 0, 1, ksize=5)  
sobel_combined = cv2.magnitude(sobel_x, sobel_y)  
plt.imshow(sobel_combined, cmap='gray')
plt.title('Sobel Edge Detection')
plt.axis('off')
```
```
prewitt_x = cv2.Sobel(gray_image, cv2.CV_64F, 1, 0, ksize=3)
prewitt_y = cv2.Sobel(gray_image, cv2.CV_64F, 0, 1, ksize=3)
prewitt = abs(prewitt_x) + abs(prewitt_y)
plt.imshow(prewitt, cmap='gray')
plt.title('Prewitt Edge Detector')
plt.axis('off')
plt.show()
```
```
roberts_x = cv2.filter2D(gray_image, cv2.CV_64F, np.array([[1, 0], [0, -1]]))
roberts_y = cv2.filter2D(gray_image, cv2.CV_64F, np.array([[0, 1], [-1, 0]]))
roberts = abs(roberts_x) + abs(roberts_y)
plt.imshow(roberts, cmap='gray')
plt.title('Roberts Edge Detector')
plt.axis('off')
plt.show()
```
```
laplacian = cv2.Laplacian(gray_image, cv2.CV_64F)
limit = np.percentile(np.abs(laplacian), 95)
plt.imshow(laplacian, cmap='gray', vmin=-limit, vmax=limit)
plt.title('Laplacian Edge Detection')
plt.axis('off')
plt.show()
```
```
canny_edges = cv2.Canny(gray_image, 50, 150)
plt.imshow(canny_edges, cmap='gray')
plt.title('Canny Edge Detection')
plt.axis('off')
```

## Output

   <img width="222" height="338" alt="Screenshot 2026-08-09 122744" src="https://github.com/user-attachments/assets/a13144ab-78bf-48d5-917c-cc01b95e64b9" />

### Sobel Edge Detector
- Detects edges in horizontal and vertical directions
- Produces gradient-based edge map

  <img width="228" height="332" alt="Screenshot 2026-08-09 122756" src="https://github.com/user-attachments/assets/e08f522b-18cb-48ef-a56e-cf8a8ecafcc8" />

### Prewitt Edge Detector
- Similar to Sobel but simpler kernel
- Detects directional edges

  <img width="220" height="339" alt="Screenshot 2026-08-09 124051" src="https://github.com/user-attachments/assets/ab47c8e5-69e8-4f08-96c0-b3e44e862368" />

### Roberts Edge Detector
- Detects edges using diagonal gradients
- Sensitive to noise

  <img width="216" height="344" alt="Screenshot 2026-08-09 124100" src="https://github.com/user-attachments/assets/55c2af4f-0b87-47d6-b09c-620407ca4b07" />

### Laplacian Edge Detector
- Detects edges using second-order derivatives
- Highlights rapid intensity changes

  <img width="235" height="337" alt="Screenshot 2026-08-09 122805" src="https://github.com/user-attachments/assets/d8b613ba-1f53-4785-af76-7c25932af4bb" />

### Canny Edge Detector
- Multi-stage edge detection
- Produces clean and thin edges

  <img width="245" height="339" alt="Screenshot 2026-08-09 122820" src="https://github.com/user-attachments/assets/d00dbd52-dbe6-44ad-ae4e-0d33c04e4354" />

## Result
Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. 

Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.
