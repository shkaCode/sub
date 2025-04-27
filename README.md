[1].Perform the following operations on digital image:

1. Read color image and convert to gray scale
2. Display size, shape, class, datatype of color and gray scale image
3. Resize (reduce ) the size of image to half
4. Rotate the original image left-right, top-bottom
5. Extract image pixels (few rows and columns) and display it as image
6. Modify some image pixels (as white or black) and display modified
imag

code-

import cv2
import numpy as np
import matplotlib.pyplot as plt

# 1. Read color image and convert to gray scale
color_image = cv2.imread('lena.jpeg')  # give your image name here
gray_image = cv2.cvtColor(color_image, cv2.COLOR_BGR2GRAY)

# 2. Display size, shape, class, datatype of color and gray scale image
print("Color Image Shape:", color_image.shape)
print("Color Image Size:", color_image.size)
print("Color Image Class:", type(color_image))
print("Color Image Datatype:", color_image.dtype)

print("Gray Image Shape:", gray_image.shape)
print("Gray Image Size:", gray_image.size)
print("Gray Image Class:", type(gray_image))
print("Gray Image Datatype:", gray_image.dtype)

# 3. Resize (reduce) the size of image to half
height = color_image.shape[0]
width = color_image.shape[1]
resized_image = cv2.resize(color_image, (width//2, height//2))

# 4. Rotate the original image left-right, top-bottom
flip_lr = cv2.flip(color_image, 1)  # Left-Right flip
flip_tb = cv2.flip(color_image, 0)  # Top-Bottom flip

# 5. Extract image pixels (few rows and columns) and display it as image
cropped_image = color_image[50:200, 100:300]

# 6. Modify some image pixels (as white or black) and display modified image
modified_image = color_image.copy()
modified_image[100:150, 100:150] = [255, 255, 255]  # white block
modified_image[200:250, 200:250] = [0, 0, 0]        # black block

# Display all images one by one

# Show original color image
plt.imshow(cv2.cvtColor(color_image, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')
plt.show()

# Show gray scale image
plt.imshow(gray_image, cmap='gray')
plt.title('Gray Scale Image')
plt.axis('off')
plt.show()

# Show resized image
plt.imshow(cv2.cvtColor(resized_image, cv2.COLOR_BGR2RGB))
plt.title('Resized Image (Half Size)')
plt.axis('off')
plt.show()

# Show left-right flipped image
plt.imshow(cv2.cvtColor(flip_lr, cv2.COLOR_BGR2RGB))
plt.title('Left-Right Flipped Image')
plt.axis('off')
plt.show()

# Show top-bottom flipped image
plt.imshow(cv2.cvtColor(flip_tb, cv2.COLOR_BGR2RGB))
plt.title('Top-Bottom Flipped Image')
plt.axis('off')
plt.show()

# Show cropped image
plt.imshow(cv2.cvtColor(cropped_image, cv2.COLOR_BGR2RGB))
plt.title('Cropped Image')
plt.axis('off')
plt.show()

# Show modified image
plt.imshow(cv2.cvtColor(modified_image, cv2.COLOR_BGR2RGB))
plt.title('Modified Image')
plt.axis('off')
plt.show()

