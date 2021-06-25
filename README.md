# DSTA Brainhack SeeTrue 2021 Hackathon  


<p align="center">
  <img src="https://www.dsta.gov.sg/images/default-source/brainhack/seetrue-workshop-logo.png">
</p>


## Getting started

Information on this repository was taken from the [official code repository](https://github.com/brainhack-seetrue-2021/Hackathon) of DSTA Brainhack SeeTrue 2021 Hackathon with an addition of my own experience in this competition.

My model had clinched the 2nd place in the *University Category*, achieving a log loss score of 0.310793888.

Google Colaboratory was used as the main platform for developing the model, utilising the free GPU provided.


<p align="center">
  <img src="https://i.ibb.co/bRRrLGB/Top-3.jpg">
</p> 


## Dataset

The dataset can be downloaded via this [link](https://bit.ly/3w0xyBl). Usage of external dataset was strictly not allowed in this hackathon.

The dataset was given in 2 formats: 
1) Raw video – Participants had to process the video themselves
2) Extracted face from video frames - A group of images with facial features extracted from the given video


Directory structure of dataset:

<p align="center">
  <img src="https://i.ibb.co/b2q34PX/directory.png" width="600" height="600"/>
</p>

## Model

I have used the sample implementation of the InceptionV3 model provided, but changed the architecture of the model and added additional features for training.

The improved model uses the pre-trained model Xception as the base model and 2 additional layers at the end:
1) Global Average Pooling 2D layer
2) Activation Layer using the Sigmoid Activation Function

For the Optimiser, I had chose to use *Adam* with a learning rate of 0.0001 and the loss function selected was *Binary Crossentropy*.


## Training

During the training process, I used the metric *Accuracy* to monitor it and ModelCheckpoint to save the best weights.

In addition. I added EarlyStopping to cut down the training time if the model does not achieve a better validation loss after 20 epochs. 
For each training instance, I had set the number of epochs to be 80.


## Prediction

I had utilised the given helper function to iterate through the given video frames to obtain the prediction probability for each frame and get the aggregate score for each video.


<p align="center">
  <img src="https://i.ibb.co/4SpsfBP/save-csv.png" width="600" height="800"/>
</p>


## Reflection

Never would I have expect myself to be in the Top 3 for this competition. The 2 days of the competition was very tiring for me, as I had many other ongoing commitments such as my summer internship, CYSummit 2021 CTF & DSTA CDDC 2021.

The techniques that I have used were a replica of what I had did for my CS3244 Machine Learning project last year.

<br/>

If I had more time and was more free, here are some improvements that I would made to create a better model and obtain better predictions:

1) Data

I would have explored techniques to work on the actual video rather than the given video frames. As the main goal was to predict whether a given video was real or fake, I felt that it would be more satisfying to deal with the video itself.

Obtaining the video frame by ourselves would have ensure a greater level of consistency and let us have a better understanding of the dataset.

Nevertheless, kudos to the organising commitee for providing us with the frame for each video!

<br/>

2) Model

I would have explored more techniques such as finding the best pre-trained model for the job and explore different ways that I could have tweaked the model.

<br/>

3) Submission

Instead of taking the average of all the probability scores for the different frames of the video, I might have considered other schemes such as assigning weights to the frames.
