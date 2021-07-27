# Face-detection-using-openCV
#### In this repository i'll show you how to make a face detection using your webcam 

### for more detailed steps on how to make face recognition please refere to this repository
**https://github.com/eadh21/openCV-face-recognition.git**


Here we will make face detection program which detect anyface in general without recognition

### The result will be something like this

![image](https://user-images.githubusercontent.com/5675794/127233665-e7d4ae7c-d37b-4505-adb1-1a4857219988.png)


To do something similar first please refer to the face recognition repository mentiond above to install openCV and other necessary programs

**use the following code for your program**

```ruby
import numpy as np
import cv2

faceCascade = cv2.CascadeClassifier("C:/Users/eadh2/Desktop/openCV projects/Cascades/haarcascade_frontalface_default.xml")  use the Cascades found in the data file mentiond in the (face recognition) repository     
cap = cv2.VideoCapture(0)                                                  # take the stream of the web camera you have
cap.set(3,640)                                                             # set Width
cap.set(4,480)                                                             # set Height

while True:
    ret, img = cap.read()                                                  # take one frame from the web camera 
    gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
    faces = faceCascade.detectMultiScale(                                  # use the faceCascade found in the data file mentiond in the (face recognition) repository
        gray,                                                              #detecting the face will be in the gray scale not in the RGB 
        scaleFactor=1.5,
        minNeighbors=5,     
        minSize=(20, 20)
    )
    for (x,y,w,h) in faces:                                                #after detecting the face make rectangle around it
        cv2.rectangle(img,(x,y),(x+w,y+h),(255,0,0),2)
        roi_gray = gray[y:y+h, x:x+w]
        roi_color = img[y:y+h, x:x+w]  
    cv2.imshow('video',img)                                                #show the image through the window to the user
    
   if cv2.waitKey(1) & 0xFF == ord('q'):                                   #use the 'q' button to close the window
    break
    
cap.release()
cv2.destroyAllWindows()
```

