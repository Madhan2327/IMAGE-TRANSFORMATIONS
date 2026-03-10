# IMAGE-TRANSFORMATIONS

## Aim
To perform image transformation such as Translation, Scaling, Shearing, Reflection, Rotation and Cropping using OpenCV and Python.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
### Step 1:
Import necessary libraries (cv2, numpy, matplotlib) and load the source image.


### Step 2:
Create transformation matrices for translation, rotation, scaling, and shearing using functions like cv2.getRotationMatrix2D().


### Step 3:
Apply the geometric transformations using cv2.warpAffine() for affine transformations and cv2.flip() for reflection.


### Step 4:
Crop the image by selecting a specific rectangular region using NumPy array slicing.


### Step 5:
Display the original and all transformed images with appropriate titles using matplotlib.pyplot.


## Program:

## Developed By: Madhan C
## Register Number: 212224240081
PYTHON
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
# Step 1: Load the image
image = cv2.imread('9dcce48f-499e-4cc4-b8ae-c7d856718778.jpg')  # Load the image from file
# Display the original image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))  # Convert BGR to RGB for correct display
plt.title("Original Image")  
plt.axis('off') 
(np.float64(-0.5), np.float64(1279.5), np.float64(812.5), np.float64(-0.5))
```

i)Image Translation
```

tx, ty = 100, 50  # Translation factors (shift by 100 pixels horizontally and 50 vertically)
M_translation = np.float32([[1, 0, tx], [0, 1, ty]])  # Translation matrix: 
# [1, 0, tx] - Horizontal shift by tx
# [0, 1, ty] - Vertical shift by ty
translated_image = cv2.warpAffine(image, M_translation, (image.shape[1], image.shape[0]))  
plt.imshow(cv2.cvtColor(translated_image, cv2.COLOR_BGR2RGB))  # Display the translated image
plt.title("Translated Image")  
plt.axis('off')
(np.float64(-0.5), np.float64(1279.5), np.float64(812.5), np.float64(-0.5))
```

ii) Image Scaling
```

fx, fy = 5.0, 2.0  # Scaling factors (1.5x scaling for both width and height)
scaled_image = cv2.resize(image, None, fx=fx, fy=fy, interpolation=cv2.INTER_LINEAR)
# resize: Resize the image by scaling factors fx, fy
# INTER_LINEAR: Uses bilinear interpolation for resizing
plt.imshow(cv2.cvtColor(scaled_image, cv2.COLOR_BGR2RGB))  # Display the scaled image
plt.title("Scaled Image")  # Set title
plt.axis('off')
(np.float64(-0.5), np.float64(6399.5), np.float64(1625.5), np.float64(-0.5))
```

iii)Image shearing
```
shear_matrix = np.float32([[1, 0.5, 0], [0.5, 1, 0]])  # Shearing matrix
# The matrix shears the image by a factor of 0.5 in both x and y directions
# [1, 0.5, 0] - Shear along the x-axis (horizontal)
# [0.5, 1, 0] - Shear along the y-axis (vertical)
sheared_image = cv2.warpAffine(image, shear_matrix, (image.shape[1], image.shape[0]))
plt.imshow(cv2.cvtColor(sheared_image, cv2.COLOR_BGR2RGB))  # Display the sheared image
plt.title("Sheared Image")  # Set title
plt.axis('off')
(np.float64(-0.5), np.float64(1279.5), np.float64(812.5), np.float64(-0.5))
```

iv)Image Reflection
```

reflected_image = cv2.flip(image, 2)  # Flip the image horizontally (1 means horizontal flip)
# flip: 1 means horizontal flip, 0 would be vertical flip, -1 would flip both axes
plt.imshow(cv2.cvtColor(reflected_image, cv2.COLOR_BGR2RGB))  # Display the reflected image
plt.title("Reflected Image")  # Set title
plt.axis('off')
(np.float64(-0.5), np.float64(1279.5), np.float64(812.5), np.float64(-0.5))
```


v)Image Rotation
```

(height, width) = image.shape[:2]  # Get the image height and width
angle = 45  # Rotation angle in degrees (rotate by 45 degrees)
center = (width // 2, height // 2)  # Set the center of rotation to the image center
M_rotation = cv2.getRotationMatrix2D(center, angle, 1)  # Get the rotation matrix
# getRotationMatrix2D: Takes the center of rotation, angle, and scale factor (1 means no scaling)
rotated_image = cv2.warpAffine(image, M_rotation, (width, height))  # Apply rotation
plt.imshow(cv2.cvtColor(rotated_image, cv2.COLOR_BGR2RGB))  # Display the rotated image
plt.title("Rotated Image")  # Set title
plt.axis('off')
(np.float64(-0.5), np.float64(1279.5), np.float64(812.5), np.float64(-0.5))
```


vi)Image Cropping
```
x, y, w, h = 100, 100, 200, 150  # Define the top-left corner (x, y) and the width (w) and height (h) of the crop
# Cropping the image from coordinates (x, y) to (x+w, y+h)
cropped_image = image[y:y+h, x:x+w]
# The crop is performed by slicing the image array in the y and x directions
plt.imshow(cv2.cvtColor(cropped_image, cv2.COLOR_BGR2RGB))  # Display the cropped image
plt.title("Cropped Image")  # Set title
plt.axis('off')
(np.float64(-0.5), np.float64(199.5), np.float64(149.5), np.float64(-0.5))
```



## Output:
## ORIGINAL IMAGE


<img width="373" height="503" alt="image" src="https://github.com/user-attachments/assets/57822adc-634d-48c6-b1cc-b58e8ce3f859" />


### i)Image Translation


<img width="369" height="466" alt="image" src="https://github.com/user-attachments/assets/856c95e6-692e-4ff5-93e7-046c5196f96f" />


### ii) Image Scaling


<img width="616" height="345" alt="image" src="https://github.com/user-attachments/assets/32d55a0e-eec4-4277-804e-304764781121" />

### iii)Image shearing



<img width="359" height="454" alt="image" src="https://github.com/user-attachments/assets/0b88f157-3294-4594-9e61-5127a429c678" />

### iv)Image Reflection


<img width="363" height="462" alt="image" src="https://github.com/user-attachments/assets/9d40fa41-2998-4f07-8d93-faaaee117ea9" />

### v)Image Rotation




<img width="354" height="460" alt="image" src="https://github.com/user-attachments/assets/ae9022f2-37d1-4806-ac8a-aefad54be7f4" />

### vi)Image Cropping
<img width="581" height="463" alt="image" src="https://github.com/user-attachments/assets/0edb8259-7a2e-48ec-b44e-90caabc0bfd5" />



## Result: 

Thus the different image transformations such as Translation, Scaling, Shearing, Reflection, Rotation and Cropping are done using OpenCV and python programming.
