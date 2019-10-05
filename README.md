# Traffic Sign Detection Sweden
My solution to [Kaggle Project](https://www.kaggle.com/c/sweden-traffic-signs-classification-eng/overview) to detect Traffic signs in Sweden and Classify them

## Dataset
The dataset is made up of 3113 traffic sign images belonging to
Sweden. The Kaggle competition from which the dataset
was picked, divided the dataset into a training set of 2503
images and a testing set of 610 images. Each image consists
of different dimensions in terms of height and width but
all the images are made up of 3 color channels, i.e, RGB
(Red, Green, Blue). Further, the intensity of light and pixel
resolution of each image varies independent of the class which
sometimes leads to the images being too difficult for a human
to recognize. The complete dataset consists of 17 classes in
total and each class represents a traffic sign in common except
for one class named ”others” which represents traffic signs
that does not belong to the other 16 unique classes.

## Data Augmentation
The dataset provided for training will not be sufficient for
a model to generalise well. Figure 1 represents the class
distribution in the training dataset. Most of the classes have
less images for a model to train on.
<p align="center">
<img src="/images/1.png" width="50%" height="50%">
</p>

Therefore, the dataset is expanded by flipping the images so
that the flipped images still represent the same class after
flipping. 
<p align="center">
<img src="/images/2.png" width="50%" height="50%">
</p>
Similarly, images belonging to class ”30 SIGN” are invariant
to vertical flipping. Hence, flipping it vertically resulted in
an image as shown in figure 3. Therefore, images that are
invariant to horizontal or vertical flipping were transformed to
extend the dataset size while keeping the number of classes
constant. 
<p align="center">
<img src="/images/3.png" width="50%" height="50%">
</p>
Finally, the initial training dataset of 2503 images is
expanded to a final training dataset of 4917 images.

## Network
To solve the problem at hand, we chose a Residual Network
variant which consists of 50 layers, i.e, ResNet-50. The
motivation behind considering such a network is due to the
fact that ResNet-50 is fairly faster to train yet so powerful.
Choosing a more deeper network could result in a higher
accuracy but needs a significant amount of time to train along
with a powerful Graphical Processing Unit (GPU).

## Results
ResNet-50 model was successfully trained to classify Sweden
traffic signs. The model trained on augmented dataset has
achieved an F1-score of 84%. 

| Precision  | Recall | F1-Score |
| ---------- | ------ | -------- |
|    0.88    |  0.80  |   0.84   |

Although the dataset was very
small, we could effectively train the powerful ResNet model to
achieve the desired results with the help of transfer learning.
There is more scope for performance improvement by further
increasing the dataset size using various data augmentation
and also by implementing different preprocessing techniques.
