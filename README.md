# Vehicle Detection using Yolo with CPU

Runs on Python version 3.0.x - 3.6.x <br>
create a virtual environment to run algorithm using anaconda if it fails to run on your local base machine. <br>
`conda create --name py36-tf python=3.6` <br>
`conda activate py36-tf` <br>

## Introduction

Vehicle Collision Warning System is a safety system that is designed to assist
drivers to avoid collisions with other vehicles and passengers through warnings and
alerts. Its major role is to reduce road accidents, deaths and injuries caused by alerting
the driver to the risks.
In this specific project we were asked to design and develop a Vehicle
Collision Warning System that uses the Vehicle Dash Cam Video Stream to help
drivers through producing warning signs. This particular system tracks the movements
of the vehicles and predicts their movements for two seconds ahead. If the other
vehicles are predicted to enter into the Danger Area marked by the user in the next
two seconds then a Warning Sign is generated to alert the driver. Here already
recorded Dash Cam Videos were taken as inputs to test the system.

![image](https://user-images.githubusercontent.com/84805141/188260923-93f02564-1133-461d-92a8-9146102480a7.png)

## Methodology 

We used project TensorFlow which is the platform for machine learning and
you only look once (YOLO) which is an object detection algorithm for real-time
vehicle detection in our project for detecting the vehicles. By combining TensorFlow
Yolo and other dependencies with python as a programming language, we have
detected vehicles in real-time Specifically, by drawing bounding boxes around these
detected vehicles, which allow us to locate where said vehicles are in a given scene. In
our project, we have used the latest version of TensorFlow and version 3 of YOLO.
And we also have used then the Deep Sort algorithm in our project.Deep Sort
Algorithm involves tracking of the objects using Kalman Filters.By using Kalman
filters we are predicting the next position of the car and using deep sort and getting the
Intersection over union (IOU)value of the bounding box area. We have set the
predicted IOU value to 0.8, which means that if the calculated IOU value is greater or
equal to 0.8 then both bounding boxes are for one vehicle otherwise they both are
different vehicles.
And for the warning sign, we have drawn a red bounding box in front of the
dashboard. And first, we tried to get the warning sign by predicting the next position
of the bounding box of a vehicle. And the idea was if the next position touches the red
bound box the system will generate a warning message. But when we tried that way
the system was trying to predict the warning sign for an array of consecutive
predictable bounding boxes and the system took a long time and did not work as we
expected due to the amount of time which we had on our hand, we decided to use
another method for the warning prediction.
So what we did was without predicting the warning sign for the next
predictable bounding box of a vehicle, we used the current bounding box of a vehicle
for detecting the warning.

## Experimental Evaluation

In this project, we tested our Vehicle Collision Warning System with various
video inputs (1 - 2 minutes) that are taken from the Dash Cam at various locations at
different time periods. We calculated the number of Correct Warnings (emergency
situation and warning given), the number of False Warnings (warning given but no
emergency situation) and the number of Missed Warnings (emergency situation but
no warning given) for each result video of the input video. The table below shows the
results we gained through testing.

| Video | Correct Warnings | False Warnings | Missed Warning |
|-------|------------------|----------------|----------------|
|Test 1 |         7        |        0       |        0       |
|Test 2 |         9        |        1       |        0       |
|Test 3 |        18        |        0       |        1       |
|Test 4 |        12        |        0       |        0       |
|Test 5 |        16        |        0       |        0       |

Given below are some of the screenshots taken from the resulting video sets.

![image](https://user-images.githubusercontent.com/84805141/188261201-a5d385fb-ffea-4ef7-ad2f-8f3548adc962.png)

![image](https://user-images.githubusercontent.com/84805141/188261214-c9f5a613-dc95-45b4-ac46-be87708f3f5b.png)

![image](https://user-images.githubusercontent.com/84805141/188261223-c48492bf-2b48-47f5-abd4-ebea81dd645f.png)
