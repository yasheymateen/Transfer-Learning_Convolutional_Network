# Transfer-Learning_Convolutional_Network

## Introduction
This project involves application of the Inception V3 convolutional network through classification odels for the CIFAR-10 dataset, containing about 6000 images for each training class.

## Methods
* Learning Rate Decay: Needed to avoid moving away from the minimum achieved by making each step smaller, thus the learning rate must be decreased
* Early Stopping: Needed to prevent model getting even worse after a prolong period of training, in which case it is necessary to stop the model before it begins down this path
* Transfer Learning: This idea is what gives us the ability to use the knowledge gained from one problem's solution process, and applying it to a related problem. In this case, we are able to use a previous trained network while maintaining achievement of good accuracy. By taking the InceptionV3 architecture, we replace the final thousand classes and add two more layers, one of which is used to classify the 10 classes in our dataset
* Upsampling: This was necessary to pass our images to the model since the CIFAR-10 dataset contains images that were a lower minimum size than that accepted by InceptionV3's model (75, 75, 3). This process is commonly used to handle data imbalance if a subset of data indicate a separate feature or set of behaviors than that of another subset or majority
* Adam Optimizer: This model is an adaptive learning rate optimization algorithm designed for training deep neural networks. This was used to compile our model
* Jupyter Notebook: Used Jupyter Notebook to do final testing using hosted runtime, as it is significantly faster.

## Results
While the training was originally planned to undergo 30 iterations (epochs) of the algorithm, the model was stopped by early stopping as mentioned above, and we were able to obtain 87% accuracy in the validation data set and 98% accuracy in the training data set.

* `Epoch 00001: LearningRateScheduler reducing learning rate to 0.001.`
  `Epoch 1/30`
  `782/782 [==============================] - 120s 154ms/step - loss: 1.1956 - accuracy: 0.5866 - val_loss: 0.8274 - val_accuracy: 0.7155`
* `Epoch 00002: LearningRateScheduler reducing learning rate to 0.0005.`
  `Epoch 2/30`
  `782/782 [==============================] - 118s 150ms/step - loss: 0.6822 - accuracy: 0.7675 - val_loss: 1.1287 - val_accuracy: 0.6351`
* `Epoch 00003: LearningRateScheduler reducing learning rate to 0.0003333333333333333.`
  `Epoch 3/30`
  `782/782 [==============================] - 119s 152ms/step - loss: 0.4651 - accuracy: 0.8458 - val_loss: 0.5581 - val_accuracy: 0.8128`
* `Epoch 00004: LearningRateScheduler reducing learning rate to 0.00025.`
  `Epoch 4/30`
  `782/782 [==============================] - 119s 152ms/step - loss: 0.2679 - accuracy: 0.9112 - val_loss: 0.5211 - val_accuracy: 0.8453`
* `Epoch 00005: LearningRateScheduler reducing learning rate to 0.0002.`
  `Epoch 5/30`
  `782/782 [==============================] - 118s 151ms/step - loss: 0.1413 - accuracy: 0.9540 - val_loss: 0.5720 - val_accuracy: 0.8574`
* `Epoch 00006: LearningRateScheduler reducing learning rate to 0.00016666666666666666.`
  `Epoch 6/30`
  `782/782 [==============================] - 118s 151ms/step - loss: 0.0804 - accuracy: 0.9736 - val_loss: 0.6445 - val_accuracy: 0.8571`
* `Epoch 00007: LearningRateScheduler reducing learning rate to 0.00014285714285714287.`
  `Epoch 7/30`
  `782/782 [==============================] - 118s 151ms/step - loss: 0.0425 - accuracy: 0.9863 - val_loss: 0.6563 - val_accuracy: 0.8714`


## Discussion
Some things to note during this process include the importance of using a lower learning rate to capitalize on the weights of the pre-trained model. This comes into play when selecting hyperparameters. We used the Adam Optimizer, but others would work as well such as SGD, and all affect the epochs(iterations of the algorithm) required to obtain a sufficiently trained model.

Another noteworthy observation is the first validation accuracy is actually higher than the training accuracy, 72% and 59% respectively. This is most likely due to the the Keras dropout use that displays different behaviors in the training and testing sets. The final rate is due to the adjustment from continuous model changes on training, as dropout is turned off during testing. In addition, the validation accuracy is higher in epoch 5 than in epoch 6, which again relates back to the dropout use, in addition to layering and complexity of the training set.

Freezing application layers takes precedence as well, otherwise computation time goes off the charts, especially with a dataset of this size, and since the layers always produce the same output. Layers may be added as needed to configure any adjustments to the model.

## Author
* **Yashar Mateen** - [yasheymateen](https://github.com/yasheymateen)

## MIT License

Copyright (c) 2020 Yashar Mateen

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
