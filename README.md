# edge-detection-opencv

## Aim

To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

---

## Software Required

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

## ⚙️ Algorithm

### Step 1:
Import all the necessary modules for the program.

### Step 2:
Load an image using `cv2.imread()`.

### Step 3:
Convert the image to grayscale.

### Step 4:
Apply **Sobel operator** using OpenCV to detect edges.

### Step 5:
Apply **Prewitt operator** using custom kernels.

### Step 6:
Apply **Roberts operator** using custom kernels.

### Step 7:
Apply **Laplacian operator** using OpenCV.

### Step 8:
Apply **Canny edge detector** using OpenCV.

### Step 9:
Display all edge-detected images for comparison.

---
## Program

### Developed By

- **Name:** Rishikesh S
- **Register No:** 212225240118

---

### i) Original Image
```
import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread("C:\\Users\\manas\\OneDrive\\Desktop\\Manasa\\image.jpg") 
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')
```

### ii)Sobel Edge Detector
- Detects edges in horizontal and vertical directions  
- Produces gradient-based edge map
```
sobel_x = cv2.Sobel(gray_image, cv2.CV_64F, 1, 0, ksize=5)  
sobel_y = cv2.Sobel(gray_image, cv2.CV_64F, 0, 1, ksize=5)  
sobel_combined = cv2.magnitude(sobel_x, sobel_y)  
plt.imshow(sobel_combined, cmap='gray')
plt.title('Sobel Edge Detection')
plt.axis('off')
```
###  iii)Canny Edge Detector
- Multi-stage edge detection  
- Produces clean and thin edges  
```
canny_edges = cv2.Canny(gray_image, 50, 150)
plt.imshow(canny_edges, cmap='gray')
plt.title('Canny Edge Detection')
plt.axis('off')
```
###  iv)Prewitt Edge Detector
- Similar to Sobel but simpler kernel  
- Detects directional edges
```
image = cv2.imread("Ferrari.jpg")

gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
prewitt_x = np.array([[1, 0, -1],
                      [1, 0, -1],
                      [1, 0, -1]])

prewitt_y = np.array([[1, 1, 1],
                      [0, 0, 0],
                      [-1, -1, -1]])

prewitt_x_edge = cv2.filter2D(gray, -1, prewitt_x)
prewitt_y_edge = cv2.filter2D(gray, -1, prewitt_y)
prewitt = cv2.magnitude(prewitt_x_edge.astype(np.float32),
                        prewitt_y_edge.astype(np.float32))

plt.imshow(canny_edges, cmap='gray')
plt.title('Prewitt Edge Detection')
plt.axis('off')

```

###  v)Roberts Edge Detector
- Detects edges using diagonal gradients  
- Sensitive to noise  
```
gray_image = cv2.imread('Ferrari.jpg', 0)

# Roberts kernels
kernel_x = np.array([[1, 0],
                     [0, -1]], dtype=np.float32)

kernel_y = np.array([[0, 1],
                     [-1, 0]], dtype=np.float32)

# Apply Roberts operator
roberts_x = cv2.filter2D(gray_image, cv2.CV_64F, kernel_x)
roberts_y = cv2.filter2D(gray_image, cv2.CV_64F, kernel_y)

# Calculate magnitude
roberts = cv2.sqrt(roberts_x*2 + roberts_y*2)
roberts = cv2.convertScaleAbs(roberts)

# Display result
plt.imshow(roberts, cmap='gray')
plt.title('Roberts Edge Detection')
plt.axis('off')
plt.show()
```

### vi)Laplacian Edge Detector
- Detects edges using second-order derivatives  
- Highlights rapid intensity changes
```
laplacian = cv2.Laplacian(gray_image, cv2.CV_64F)
plt.imshow(laplacian, cmap='gray')
plt.title('Laplacian Edge Detection')
plt.axis('off')
```


## Output

### Original Image



###  Sobel Edge Detector


###  Canny Edge Detector


###  Prewitt Edge Detector


###  Roberts Edge Detector


###  Laplacian Edge Detector




---

## Result

Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.
