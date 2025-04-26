# Sturdy-Octo-Disco-Adding-Sunglasses-for-a-Cool-New-Look

Sturdy Octo Disco is a fun project that adds sunglasses to photos using image processing.

Welcome to Sturdy Octo Disco, a fun and creative project designed to overlay sunglasses on individual passport photos! This repository demonstrates how to use image processing techniques to create a playful transformation, making ordinary photos look extraordinary. Whether you're a beginner exploring computer vision or just looking for a quirky project to try, this is for you!

## Features:
- Detects the face in an image.
- Places a stylish sunglass overlay perfectly on the face.
- Works seamlessly with individual passport-size photos.
- Customizable for different sunglasses styles or photo types.

## Technologies Used:
- Python
- OpenCV for image processing
- Numpy for array manipulations

## How to Use:
1. Clone this repository.
2. Add your passport-sized photo to the `images` folder.
3. Run the script to see your "cool" transformation!

## Applications:
- Learning basic image processing techniques.
- Adding flair to your photos for fun.
- Practicing computer vision workflows.

Feel free to fork, contribute, or customize this project for your creative needs!
## program developed by
RAKSHA DHARANIKA V
212223230167
```
# Import libraries
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Load the Face Image
faceImage = cv2.imread('Harshini.jpg')
plt.imshow(faceImage[:,:,::-1]);plt.title("Face")
```
![image](https://github.com/user-attachments/assets/3ee22427-e015-4931-bab0-32df3be205d5)

# Load the Sunglass image with Alpha channel
# (http://pluspng.com/sunglass-png-1104.html)
```
glassPNG = cv2.imread('sunglass.png',-1)
plt.imshow(glassPNG[:,:,::-1]);plt.title("glassPNG")
```
![image](https://github.com/user-attachments/assets/04012c98-dec3-431b-bf7d-95a86d4a6738)



# Resize the image to fit over the eye region
```
glassPNG = cv2.resize(glassPNG,(90,30))
print("image Dimension ={}".format(glassPNG.shape))
```
![image](https://github.com/user-attachments/assets/3bb10e9d-2c98-470c-94f2-79e6b7fa3b7f)

```
# Separate the Color and alpha channels
```
glassBGR = glassPNG[:,:,0:3]
glassMask1 = glassPNG[:,:,3]
```

# Display the images for clarity
```
plt.figure(figsize=[15,15])
plt.subplot(121);plt.imshow(glassBGR[:,:,::-1]);plt.title('Sunglass Color channels');
plt.subplot(122);plt.imshow(glassMask1,cmap='gray');plt.title('Sunglass Alpha channel');
```


![image](https://github.com/user-attachments/assets/3ece9f02-cbf2-4bc0-beb0-1fe22a663824)


# Make a copy
```
#faceWithGlassesNaive = resized_faceImage.copy()
faceWithGlassesNaive = faceImage.copy()
```
# Replace the eye region with the sunglass image

```
faceWithGlassesNaive[60:90,60:150]=glassBGR

plt.imshow(faceWithGlassesNaive[...,::-1])
```
![image](https://github.com/user-attachments/assets/4ab88f32-bee7-4540-a63d-803eca9c9085)

