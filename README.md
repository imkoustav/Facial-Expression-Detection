# Facial-Expression-Detection
Dectection of Facial Expression using Haar Cascade

# Haar-Cascade
Haar cascade classifiers first were proposed by Paul Viola and Michael Jones and uses Haar kernels for extracing features and it uses multiple classifiers one after an other. The classifiers get more complex as data move forward. Each classifier will specify whether the image is maybe from the desired class or it is definitly not in the desired class and if it is maybe from the desired class will pass image forward to the next classifier.

For training these classifiers,first you need to collect images from desired class (positive data in our case face images) and everything else (negative data) especially from the environment which you want to test your model like chairs, tables, etc. (for better result its better to make the images grayscale). Also you need to make a description file for postive and negetive samples.

For positives you need to write in the following format: [filename] [number of object annotations] [coordinates of the objects bounding rectangles (x, y, width, height)] for example: img/img1.jpg 1 140 100 45 45
For negative images you only need to write the file name
After collecting data and creating the two description files, you have to install opencv and its dependencies. Then using following commands you can start training your model:

First you need to create a vector file from the positive image with the following command: opencv_createsamples -info [name of description file] -num [number of positive samples] -w [width of the output] -h [height of the output] -vec [name of the vector file] for example:

opencv_createsamples -info info/info.lst -num 9000 -w 20 -h 20 -vec positives.vec

Then after creating the vector file you can start the actuall training with the following command:

opencv_traincascade -data data -vec positives.vec -bg bg.txt -numPos 7000 -numNeg 3500 -numStages 10 -w 20 -h 20

I trained the haar cascade with 7000 positive images and 3500 negative images for 21 stage which it make a very few mistakes.

For more information you can reffer to opencv website.


Facial Expression or Facial Emotion Detector can be used to know whether a person is sad, happy, angry and so on only through his/her face. This Repository can be used to carry out such a task. It uses your WebCamera and then identifies your expression in Real Time. Yeah in real-time!

# PLAN
This is a three step process. In the first, we load the XML file for detecting the presence of faces and then we retrain our network with our image on five diffrent categories. After that, we import the label_image.py program and set up everything in realtime.

# STEP 1 - Implementation of OpenCV HAAR CASCADES
I'm using the "Frontal Face Alt" Classifier for detecting the presence of Face in the WebCam. 
Next, we have the task to load this file, which can be found in the label.py program. 
Now everything can be set with the Label.py Program. So let's move to the next Step.

# STEP 2 - ReTraining the Network - Tensorflow Image Classifier
We are going to create an Image classifier that identifies whether a person is sad, happy and so on and then show this text on the OpenCV Window. This step will consist of several sub steps:

-> We need to first create a directory named images. In this directory, create five or six sub directories with names like Happy, Sad, Angry, Calm and Neutral.
-> Now fill these directories with respective images by downloading them from the Internet. E.g., In "Happy" directory, fill only those iages of person who are happy.
-> Now run the "face-crop.py" file
-> Once you have only cleaned images, we are ready to retrain the network. For this purpose I'm using Mobilenet Model which is quite fast and accurate. 

# STEP 3 - Importing the ReTrained Model and Setting Everything Up
Finally, I've put everything under the "label_image.py" file from where we can get evrything. Now run the "label.py" file

It'll open a new window of OpenCV and then identifies your Facial Expression. Wow!!! we are done now!
