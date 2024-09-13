# Convolutional Deep Neural Network for Digit Classification

## AIM

To Develop a convolutional deep neural network for digit classification and to verify the response for scanned handwritten images.

## Problem Statement and Dataset
Digit classification and to verify the response for scanned handwritten images.

The MNIST dataset is a collection of handwritten digits. The task is to classify a given image of a handwritten digit into one of 10 classes representing integer values from 0 to 9, inclusively. The dataset has a collection of 60,000 handwrittend digits of size 28 X 28. Here we build a convolutional neural network model that is able to classify to it's appropriate numerical value.

![image](https://github.com/user-attachments/assets/2fdde38c-be0c-4263-a364-ed68c6fca221)

## Neural Network Model

![image](https://github.com/user-attachments/assets/c82b9aa7-c103-4712-b983-d69a35e75a89)


## DESIGN STEPS

### STEP 1:
Import tensorflow and preprocessing libraries.
Import tensorflow and preprocessing libraries.

### STEP 2:
Download and load the dataset

### STEP 3:
Scale the dataset between it's min and max values

### STEP 4:
Using one hot encode, encode the categorical values

### STEP 5:
Split the data into train and test

### STEP 6:
Build the convolutional neural network model

### STEP 7:
Train the model with the training data

STEP 8:
### Plot the performance plot

### STEP 9:
Evaluate the model with the testing data

### STEP 10:
Fit the model and predict the single input

## PROGRAM

### Name: SHOBIKA P
### Register Number: 212221230096

```
import numpy as np
from tensorflow import keras
from tensorflow.keras import layers
from tensorflow.keras.datasets import mnist
import tensorflow as tf
import matplotlib.pyplot as plt
from tensorflow.keras import utils
import pandas as pd
from sklearn.metrics import classification_report,confusion_matrix
from tensorflow.keras.preprocessing import image

(X_train, y_train), (X_test, y_test) = mnist.load_data()
X_train.shape
X_test.shape
single_image= X_train[0]
single_image.shape
plt.imshow(single_image,cmap='gray')
y_train.shape
X_train.min()
X_train.max()
X_train_scaled = X_train/255.0
X_test_scaled = X_test/255.0
y_train[0]
y_train_onehot = utils.to_categorical(y_train,10)
y_test_onehot = utils.to_categorical(y_test,10)
type(y_train_onehot)
y_train_onehot.shape
single_image = X_train[500]
plt.imshow(single_image,cmap='gray')
y_train_onehot[500]
X_train_scaled = X_train_scaled.reshape(-1,28,28,1)
X_test_scaled = X_test_scaled.reshape(-1,28,28,1)
model = keras.Sequential()
model.add(layers.Input(shape=(28,28,1)))
model.add(layers.Conv2D(filters=32,kernel_size=(3,3),activation='relu'))
model.add(layers.MaxPooling2D(pool_size=(2,2)))
model.add(layers.Conv2D(filters=64,kernel_size=(3,3),activation='relu'))
model.add(layers.Flatten())
model.add(layers.Dense(32,activation='relu'))
model.add(layers.Dense(10,activation='softmax'))
print("Name : Shobika")
print("Reg No : 212221230096")
model.summary()
model.compile(optimizer='adam',loss='categorical_crossentropy',metrics=['accuracy'])
model.fit(X_train_scaled ,y_train_onehot, epochs=5,
          batch_size=64, 
          validation_data=(X_test_scaled,y_test_onehot))
metrics = pd.DataFrame(model.history.history)
print("Name : Shobika")
print("Reg No : 212221230096")
metrics.head()
print("Name : Shobika")
print("Reg No : 212221230096")
metrics[['accuracy','val_accuracy']].plot()
print("Name : Shobika")
print("Reg No : 212221230096")
metrics[['loss','val_loss']].plot()

x_test_predictions = np.argmax(model.predict(X_test_scaled), axis=1)
print("Name : Shobika")
print("Reg No : 212221230096")

print(confusion_matrix(y_test,x_test_predictions))
print("Name : Shobika")
print("Reg No : 212221230096")
print(classification_report(y_test,x_test_predictions))
img = image.load_img('grey.jpg')

img = image.load_img('grey.jpg')
img_tensor = tf.convert_to_tensor(np.asarray(img))
img_28 = tf.image.resize(img_tensor,(28,28))
img_28_gray = tf.image.rgb_to_grayscale(img_28)
img_28_gray_scaled = img_28_gray.numpy()/255.0
x_single_prediction = np.argmax(
    model.predict(img_28_gray_scaled.reshape(1,28,28,1)),
     axis=1)
print(x_single_prediction)
print("Name : Shobika")
print("Reg No : 212221230096")
plt.imshow(img_28_gray_scaled.reshape(28,28),cmap='gray')
img_28_gray_inverted = 255.0-img_28_gray
img_28_gray_inverted_scaled = img_28_gray_inverted.numpy()/255.0

x_single_prediction = np.argmax(
    model.predict(img_28_gray_inverted_scaled.reshape(1,28,28,1)),
     axis=1)

print(x_single_prediction)
     
```


## OUTPUT
### Training Loss, Validation Loss Vs Iteration Plot
![image](https://github.com/user-attachments/assets/13e7ee31-9beb-4f04-af3c-ef0d44e9a71f)


![image](https://github.com/user-attachments/assets/f9c8f151-d3f0-4d62-93f6-cfd6fbe8fe57)


![image](https://github.com/user-attachments/assets/febfbbe1-6b15-4636-9425-416523af5927)


![image](https://github.com/user-attachments/assets/ea880326-9ef0-47dc-8bfb-479fde6d079e)

### Classification Report

![image](https://github.com/user-attachments/assets/d3848de1-1f03-4f2e-9b6a-8e881f0e211a)

### Confusion Matrix

![image](https://github.com/user-attachments/assets/7eb52761-de44-4423-bf98-37def17ffac3)

### New Sample Data Prediction
![image](https://github.com/user-attachments/assets/2838defd-b7a7-4e85-98e0-1ee81674ec1e)


![image](https://github.com/user-attachments/assets/4cbe0bd6-bef4-4722-b7c1-a5dc125ce3e6)



## RESULT
A convolutional deep neural network for digit classification and to verify the response for scanned handwritten images is developed sucessfully.

