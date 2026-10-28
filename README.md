# Exp-4--Record-Image-Transformations-Completion-requirements

## Geometric Transformations Using OpenCV

---

## Aim

To write a Python program using OpenCV to perform various geometric transformations on an image.

The program performs the following operations:

- Image Translation  
- Image Scaling (Resizing)  
- Image Shearing  
- Image Reflection (Flipping)  
- Image Rotation  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image in color mode.

### Step 3: Image Translation
- Create a translation matrix to shift the image  
- Move the image 50 pixels to the right and 80 pixels down  
- Apply transformation using `cv2.warpAffine()`  
- Display original and translated images  

### Step 4: Image Scaling
- Resize the image to 0.5× (downscale)  
- Resize the image to 2× (upscale)  
- Use `cv2.resize()`  
- Display original, downscaled, and upscaled images  

### Step 5: Image Shearing
- Create transformation matrices for:
  - Horizontal shearing  
  - Vertical shearing  
- Apply transformations using `cv2.warpAffine()`  
- Display original and sheared images  

### Step 6: Image Reflection
- Perform flipping using `cv2.flip()`:
  - Horizontal reflection  
  - Vertical reflection  
  - Both axes  
- Display all reflected images  

### Step 7: Image Rotation
- Create rotation matrices for:
  - 45° rotation  
  - 90° rotation  
- Use `cv2.getRotationMatrix2D()` and `cv2.warpAffine()`  
- Display original and rotated images  

---

##  Program

### Developed By:
**Name:** Aman Nair

### Register No:
212225240008

~~~python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read image
img = cv2.imread("img.jpg")
img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
h, w = img.shape[:2]

# 1. Image Translation
M = np.float32([[1, 0, 50], [0, 1, 80]])
translated = cv2.warpAffine(img, M, (w, h))

# 2. Image Scaling
small = cv2.resize(img, None, fx=0.5, fy=0.5)
large = cv2.resize(img, None, fx=2, fy=2)

# 3. Image Shearing
M1 = np.float32([[1, 0.5, 0], [0, 1, 0]])
horizontal = cv2.warpAffine(img, M1, (w, h))

M2 = np.float32([[1, 0, 0], [0.5, 1, 0]])
vertical = cv2.warpAffine(img, M2, (w, h))

# 4. Image Reflection
flip_h = cv2.flip(img, 1)
flip_v = cv2.flip(img, 0)
flip_both = cv2.flip(img, -1)

# 5. Image Rotation
M45 = cv2.getRotationMatrix2D((w//2, h//2), 45, 1)
rot45 = cv2.warpAffine(img, M45, (w, h))

M90 = cv2.getRotationMatrix2D((w//2, h//2), 90, 1)
rot90 = cv2.warpAffine(img, M90, (w, h))

# Display results
images = [
    img, translated, small, large,
    horizontal, vertical, flip_h,
    flip_v, flip_both, rot45, rot90
]

titles = [
    "Original", "Translation", "Downscaled", "Upscaled",
    "Horizontal Shear", "Vertical Shear", "Horizontal Flip",
    "Vertical Flip", "Both Axes Flip", "Rotation 45", "Rotation 90"
]

plt.figure(figsize=(15, 12))

for i in range(len(images)):
    plt.subplot(3, 4, i + 1)
    plt.imshow(images[i])
    plt.title(titles[i])
    plt.axis("off")

plt.tight_layout()
plt.show()
~~~

---

##  Output

### Image Translation
- Original image is displayed  
- Translated image (shifted right and down) is displayed  

### Image Scaling
- Original image is displayed  
- Downscaled image (0.5×) is displayed  
- Upscaled image (2×) is displayed  

### Image Shearing
- Original image is displayed  
- Horizontally sheared image is displayed  
- Vertically sheared image is displayed  

### Image Reflection
- Original image is displayed  
- Horizontally flipped image is displayed  
- Vertically flipped image is displayed  
- Both-axis flipped image is displayed  

### Image Rotation
- Original image is displayed  
- 45° rotated image is displayed  
- 90° rotated image is displayed  

<img width="1643" height="293" alt="image" src="https://github.com/user-attachments/assets/151d2366-5d59-477b-a4a7-14a7388ce390" />
<img width="1285" height="296" alt="image" src="https://github.com/user-attachments/assets/f8534576-43a9-44e4-ac6f-83428e2fccef" />
<img width="1681" height="344" alt="image" src="https://github.com/user-attachments/assets/0499f314-7c73-45d7-9692-849ced89d8ec" />


---

##  Result

Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.
