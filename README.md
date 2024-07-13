# OpenCV Image Processing Task

## Objectives

This project demonstrates fundamental image processing and computer vision tasks using the OpenCV library in Python. The tasks include:
- Loading and displaying images
- Converting images to grayscale
- Extracting and manipulating color channels
- Image indexing and slicing
- Plotting images using Matplotlib

## Libraries Used

- OpenCV
- Matplotlib
- Pillow
- wget

## Getting Started

### Prerequisites

Ensure you have the following libraries installed:

```bash
pip install opencv-python matplotlib pillow wget

Running the Script
The main script image_processing.py includes all the tasks outlined in this project. Here's a breakdown of the script:
1. Import Libraries and Download Images
import os
import cv2
import matplotlib.pyplot as plt
from PIL import Image

# Download images using wget
!wget https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-CV0101EN-SkillsNetwork/images%20/images_part_1/lenna.png -O lenna.png
!wget https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-CV0101EN-SkillsNetwork/images%20/images_part_1/baboon.png -O baboon.png
!wget https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-CV0101EN-SkillsNetwork/images%20/images_part_1/barbara.png -O barbara.png

2. Define Helper Function
def get_concat_h(im1, im2):
    dst = Image.new('RGB', (im1.width + im2.width, im1.height))
    dst.paste(im1, (0, 0))
    dst.paste(im2, (im1.width, 0))
    return dst

3. Load and Display an Image
my_image = "lenna.png"
image = cv2.imread(my_image)
new_image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
plt.figure(figsize=(10, 10))
plt.imshow(new_image)
plt.show()

4. Convert Image to Grayscale
image_gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
plt.figure(figsize=(10, 10))
plt.imshow(image_gray, cmap='gray')
plt.show()
cv2.imwrite('lenna_gray_cv.jpg', image_gray)

5. Extract and Display Color Channels
baboon = cv2.imread('baboon.png')
baboon_rgb = cv2.cvtColor(baboon, cv2.COLOR_BGR2RGB)
blue, green, red = baboon[:, :, 0], baboon[:, :, 1], baboon[:, :, 2]
im_bgr = cv2.vconcat([blue, green, red])
plt.figure(figsize=(10, 10))
plt.subplot(121)
plt.imshow(baboon_rgb)
plt.title("RGB image")
plt.subplot(122)
plt.imshow(im_bgr, cmap='gray')
plt.title("Different color channels  blue (top), green (middle), red (bottom)")
plt.show()

6. Image Indexing
rows = 256
plt.figure(figsize=(10, 10))
plt.imshow(new_image[0:rows, :, :])
plt.show()

columns = 256
plt.figure(figsize=(10, 10))
plt.imshow(new_image[:, 0:columns, :])
plt.show()

7. Manipulate Color Channels
# Red channel
baboon_red = baboon.copy()
baboon_red[:, :, 0] = 0
baboon_red[:, :, 1] = 0
plt.figure(figsize=(10, 10))
plt.imshow(cv2.cvtColor(baboon_red, cv2.COLOR_BGR2RGB))
plt.show()

# Blue channel
baboon_blue = baboon.copy()
baboon_blue[:, :, 1] = 0
baboon_blue[:, :, 2] = 0
plt.figure(figsize=(10, 10))
plt.imshow(cv2.cvtColor(baboon_blue, cv2.COLOR_BGR2RGB))
plt.show()

# Green channel
baboon_green = baboon.copy()
baboon_green[:, :, 0] = 0
baboon_green[:, :, 2] = 0
plt.figure(figsize=(10, 10))
plt.imshow(cv2.cvtColor(baboon_green, cv2.COLOR_BGR2RGB))
plt.show()

8. Question 1

# Load and convert the image
baboon_blue = cv2.imread('baboon.png')
baboon_blue = cv2.cvtColor(baboon_blue, cv2.COLOR_BGR2RGB)

# Set the blue channel to zero
baboon_blue[:, :, 2] = 0

# Plot the image
plt.figure(figsize=(10, 10))
plt.imshow(baboon_blue)
plt.show()

References
Images from: University of Wisconsin - Madison
Pillow Documentation
OpenCV Documentation
Gonzalez, Rafael C., and Richard E. Woods. "Digital image processing." (2017)





















































































