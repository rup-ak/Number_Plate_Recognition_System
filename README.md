# Number_Plate_Recognition_System

This is a code for colab. And I store the dataset on google drive.

You can run this notebook and write the training and testing dataset path and then for testing you can upload an image on colab and then write the path on notebook.

then you can easily run the program

(The image need to be an image like exact from the font like this ![image](https://user-images.githubusercontent.com/93119678/225416787-d4ba1318-dfcc-42db-8a1b-d7c2caa04d2b.png)


 ## 1. Train the dataset to the model
 ## 2.	Building the System
 ## 3. Predict the detection of the image edge.
 ## 4. Recognize the number plate.
 ## 5. Show the output image.

Here for the dependency, I used Os, cv2, matplotlib.pyplot, easyocr, imutils, numpy, tensorflow.

 ### 1.  Train the dataset to the model

 First, I sort classes in ascending order and then convert the class into an index so that I can use them easily. Then I read the image path and then I read the image file, I resized the image file to 64*64 so that I only get the number plate size and after that, I converted the image file to a grayscale.
I store the image in array X where I store the value of image height, weight, and image scale like grayscale. I store the image class to the y array where the value will be which class the image is located. 
After that, I convert the X and y array to a numpy array and add channel dimension to the input array. Then I convert the labels to one-hot encoding

### 2. Building the System
Then I used Keras API of TensorFlow. It is then used to define the architecture of a convolutional neural network (CNN). Here I used five layers like
1.	Conv2D layer
2.	MaxPooling2D layer
3.	Flatten layer and 
4.	2 * Dense layer

   ![image](https://github.com/rup-ak/Number_Plate_Recognition_System/assets/93119678/c5ecad7f-28fa-40da-bddd-d2ddeb92ed6e)
   Visualize Model Architecture

In the conv2D layer, I used 32 filter whose shape is 3*3 and I used relu activation which indicate is the function is active or fires whenever the input is positive or zero but will not activate when the input is negative. Then I use MaxPooling2D which is a 2*2 shape and then The Flatten layer then I use the 1st Dense layer where I use 64 neurons and, in the 2nd, Dense layer, I use the neuron how many I have image class, and I used softmax activation. Then I compile the model and train the model with 20 epochs. 
Then I check the validation of the dataset with the same architecture of the model and then I test the dataset with totally different data I get 100% training accuracy and 93% testing accuracy and then I save the model for use later. 

Here my training accuracy is 100% and the training time is 322.95 seconds, and the accuracy is 100% of the training dataset and it takes 322.95 seconds.

![image](https://github.com/rup-ak/Number_Plate_Recognition_System/assets/93119678/49e230aa-dba5-4a99-9cb7-cd6dfc525334)


### 3. Predict and recognize the class of an Image.
Then I read an image, resize it to 64*64, and convert it to grayscale to predict the class. After the prediction. 

### 4. Recognize the number plate.
I need to recognize the number from the number plate. For that, I use bilateralFilter to reduce noise and use Canny for edge detection. Then I find the contours with the findContours function and draw the contours in a bounding box. 

![image](https://github.com/rup-ak/Number_Plate_Recognition_System/assets/93119678/22446427-cd93-42d9-8b2e-1ad21e694a57)
Preprocess for recognized image

### 5. Show the output image.
 Then I used easyOCR to read a text and render results which is a Python package for performing Optical Character Recognition on the cropped number plate image. This OCR step recognizes any additional text that may be present in the number plate image and returns the recognized text as a list of tuples. The recognized text is stored in the result variable.

 ![image](https://github.com/rup-ak/Number_Plate_Recognition_System/assets/93119678/a5ce2294-9fff-42d3-870b-c47d88a9dc08) 
Annotate the Number Plate
 ![image](https://github.com/rup-ak/Number_Plate_Recognition_System/assets/93119678/c96c9215-29db-4ee2-8839-a49af4095b61)
And this is the final result

