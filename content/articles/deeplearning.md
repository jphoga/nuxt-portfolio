---
title: Deep Learning on the Edge
date: '2019-09-06T23:46:37.121Z'
description: Detecting objects while driving on the highway
img: https://images.unsplash.com/photo-1580752300992-559f8e0734e0?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=634&q=80
alt: nice image
author:
  name: Peter
  bio: All about Peter and what he does and where he works
tags:
  - web development
---

I always thought that the realms of Deep Learning and Data Science were reserved for PhD students and insanely smart geeks calculating complex models on high-end computers.

Well, for the ongoing research in Deep Learning the PhD student part is probably true. But if you use certain freely available tools and methods to apply Deep Learning to real world problems it is actually comparatively easy to get started with and a lot of fun! Google's [Tensorflow Object Detection API](https://github.com/tensorflow/models/tree/master/research/object_detection) or Facebook's [Pytorch](https://towardsdatascience.com/object-detection-and-tracking-in-pytorch-b3cf1a696a98) are pretty handy and well-architectured frameworks to start with. Combine this with transfer learning (a method of training an existing model to recognize additional stuff e.g. [Pokemon](https://towardsdatascience.com/detecting-pikachu-in-videos-using-tensorflow-object-detection-cd872ac42c1d)) your imagination is your only boundary (of course there are some drawbacks but still it works really well).

![ML](./machine-learning-piano.jpg)

### A whole new world of detection

The project I got assigned to uses Deep Learning for **object detection**, a method to detect pre-trained objects inside a frame while also telling you where these objects are by applying a bounding box around it. There are other Deep Learning areas too like **image classification** (classifying the whole image to a category e.g. "National Park", "Desert" etc.) or **natural language processing** (detecting words and sentences out of spoken or written language).

Deep Learning is just one part of a broader world of Machine Learning with many more applications. But you have to start somewhere and object detection is definitely an interesting way to deep dive into the "deep" art of Machine Learning. Here's the Shibuya crossing seen by Tensorflow Object Detection API (cars and persons are quite accurately detected):

![Shibuya](./shibuya.jpg)

I won't go too much into the details of my project here (and I can't due to disclosure issues), but in general we built an _edge server_ (as opposite to a _cloud server_ like an **Ec2 on AWS**). This edge server is connected to a camera (normally a drive-recorder) and a GPS-card to recognize objects on the road while driving in your car. This can be signs on the road like stop signs or even other cars and their number plates. The really fun thing is to combine this with an **OCR model** to actually read what the signs says ("**30 miles to Tokyo**"! Yes!).

Training the model took me some time because I had to figure out how transfer learning works with Tensorflow (different versions in basically all necessary programs from Linux to Python to CUDA drove me nearly mad!). But after completing the tedious setup of the training environment (I used an **AWS Ec2 instance** named **p2.xlarge** which has a GPU attached and the hour price is just about one dollar), I just needed some nice data for the training and the fun could begin (haha, you wish!).

### Annotation hell

Data means in our case lot's of pictures while driving down the highway. My colleague took up the challenge and recorded some parts of his way to his weekend camping ground. I took the video, split it into 24 frames (= jpgs) per second and classified the pictures into different categories by hand (this is of course what we want to let the model do for you in the future!).

I remember it took me nearly half a day for all 1000 pictures to draw the annotation box around the object and name the file. In case you cannot really get your head around what annotation means, below is an example annotating different types of sushi using this pretty awesome [annotation tool](https://github.com/tzutalin/labelImg) (just do this for a hundred or better a thousand pictures and you are fine):

![Annotation](./annotation.jpg)

Now I could finally train the model and after a few tries (be aware of OpenCV's [color handling of RGB](https://www.learnopencv.com/why-does-opencv-use-bgr-color-format/)!) it finally worked: I had a fully functioning Tensorflow object detection model trained in just a few days without much prior knowledge of Machine Learning and Deep Learning. A great feeling!

### Into robotics

Another reason why this project was awesome lay in the fact that I got in touch with a framework called [ROS (Robotic Operating System)](https://www.ros.org/). We didn't do any robotic arms or self-driving cars in our project but nevertheless ROS is sometimes a great option when you want your application to run _autonomously_. This meant in our case: switch it on and let it run without any user control. There wasn't even a UI to control the app - pretty hard (and forbidden!) to use a UI while driving anyways.

Because of this project I got into Deep Learning and Robotics at the same time - _how cool is that_?
<i class="em em-snowflake" aria-role="presentation" aria-label="SNOWFLAKE"></i>
<i class="em em-snowboarder" aria-role="presentation" aria-label="SNOWBOARDER"></i>

I could even visit this years [ROS Con](https://roscon.ros.org/2019/) (yes, there is a big community around ROS) to meet all kinds of people and learn about projects using ROS in commercial robots and science around the world. In case you still wonder what ROS is all about: in short, ROS makes it possible to create robotic applications and robots more easily since it is open source, so you don't have to spend your first million dollars to create a functioning framework yourself to get your robot run.

![RosCon](./roscon.png)

Happy Deep Learning and robot development everyone!
<i class="em em-robot_face" aria-role="presentation" aria-label="ROBOT FACE"></i>
