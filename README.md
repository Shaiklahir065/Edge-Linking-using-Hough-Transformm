# Edge-Linking-using-Hough-Transformm
## Aim:
To write a Python program to detect the lines using Hough Transform.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
### Step1:

Import all the necessary modules for the program.
### Step2:

Load a image using imread() from cv2 module.
### Step3:

Convert the image to grayscale.
### Step4:

Using Canny operator from cv2,detect the edges of the image.
### Step5:

Using the HoughLinesP(),detect line co-ordinates for every points in the images.Using For loop,draw the lines on the found co-ordinates.Display the image.

### Program:
```python
DEVELOPED BY: shaiklahir
REG NO: 212224240148
```
#### Read image and convert it to grayscale image
```python
import numpy as np
import cv2
import matplotlib.pyplot as plt
img=cv2.imread("dog.jpg",0)
img_c=cv2.imread("dog.jpg",1)
img_c=cv2.cvtColor(img_c,cv2.COLOR_BGR2RGB)
gray=cv2.cvtColor(img,cv2.COLOR_GRAY2RGB)
gray = cv2.GaussianBlur(gray,(3,3),0)
plt.figure(figsize=(13,13))
plt.subplot(1,2,1)
plt.imshow(img_c)
plt.title("Original Image")
plt.axis("off")
plt.subplot(1,2,2)
plt.imshow(gray)
plt.title("Gray Image")
plt.axis("off")
plt.show()
```
#### Find the edges in the image using canny detector and display
```python
canny=cv2.Canny(gray,120,150)
plt.imshow(canny)
plt.title("Canny Edge Detector")
plt.axis("off")
plt.show()
```
#### Detect points that form a line using HoughLinesP
```python
lines=cv2.HoughLinesP(canny,1,np.pi/180,threshold=80,minLineLength=50,maxLineGap=250)
```
#### Draw lines on the image
```python
for line in lines:
    x1,y1,x2,y2=line[0]
    cv2.line(img_c,(x1,y1),(x2,y2),(255,0,0),3)
```
#### Display the result
```python
plt.imshow(img_c)
plt.title("Result Image")
plt.axis("off")
plt.show()
```
## Output

### Input image and grayscale image
![image](https://github.com/user-attachments/assets/29e8dea8-6790-4b50-9996-a93c42c6e9f1)


![Screenshot 2025-04-28 223925](https://github.com/user-attachments/assets/2782b1e8-0e95-4a20-8145-844ab8b18ba2)

### Canny Edge detector output
![image](https://github.com/user-attachments/assets/ba652bcb-0d23-4d07-b708-caf7faf46450)

### Display the result of Hough transform
![WhatsApp Image 2025-04-28 at 22 54 25_e9c5e7e8](https://github.com/user-attachments/assets/3a8e6df5-7d01-4765-b457-106e00cdb22a)

