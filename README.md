# self-driving-vehicle

## 순서
* RGB threshold 선정
* 선정 threshold 이하 
* 삼각형 영역 선정
  * 왼쪽 아래, 가운데  위, 오른쪽 아래
* 식별한 영역에 특정 색상 입히기
* Edge 찾기
  * OpenCV Canny Edge
  * 먼저 대상 이미지를 greyscale로 변환
  * edges = cv2.Canny(gray, low_threshold, high_threshold)
* Hough Transform


```python
import matplotlib.pyplot as plt
import matplotlib.image as mpimg
import numpy as np

# Read in the image and print out some stats
image = mpimg.imread('test.jpg')
print('This image is: ',type(image), 
         'with dimensions:', image.shape)

# Grab the x and y size and make a copy of the image
ysize = image.shape[0]
xsize = image.shape[1]
# Note: always make a copy rather than simply using "="
color_select = np.copy(image)

# Define our color selection criteria
# Note: if you run this code, you'll find these are not sensible values!!
# But you'll get a chance to play with them soon in a quiz
red_threshold = 0
green_threshold = 0
blue_threshold = 0
rgb_threshold = [red_threshold, green_threshold, blue_threshold]

# Identify pixels below the threshold
thresholds = (image[:,:,0] < rgb_threshold[0]) \
            | (image[:,:,1] < rgb_threshold[1]) \
            | (image[:,:,2] < rgb_threshold[2])
color_select[thresholds] = [0,0,0]

# Display the image                 
plt.imshow(color_select)
plt.show()
```
