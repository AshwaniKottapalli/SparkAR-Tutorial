# Making an Instagram Filter is as easy as playing a sport

What is the first thing you do to learn or play a sport? Reach its playground.

## Reaching the Playground
To download SparkAR Studio, click [on this link](https://sparkar.facebook.com/ar-studio/download/)
Once done, install the application on your system

Now the application is like your playground or stadium to start playing(making filters)


Before starting to learn any sport, the first thing is to analyze the ground, how many features ,etc does the ground have?

## Knowing your Playground

As soon as you open SparkAR Studio, this will be the entrance of your playground:

![Alt Text](https://i.ibb.co/dDsYMnx/entrance.png)

At the Entrance, you can either start fresh with New Project, or can choose from any of the templates. Templates are just widely used pre-sets on which you can make chages to make your own filter.

As we are new to this sport, select the *Head Decoration* Template

Vola! You are now inside the playground!

![Alt Text](https://i.ibb.co/yk50YFv/pp.png)

For the complete analysis of the playground and its basic components check [official documentaion](https://sparkar.facebook.com/ar-studio/learn/articles/fundamentals/navigating-the-interface#the-layers-panel)


## Getting the equipments to Play

First download the contents from [this link]()  

You will have the following Assets:

Drag and Drop all the models, textures, etc to the Assets Panel.

Now, that you have all the equipments ready, lets place some of them 

![Alt Text](https://i.ibb.co/M7rbKTr/scene.png)

In the Scene's panel, delete the deleteMe object and drag the Vision.fbx from assets panel and drop it as the child of dragHere in the Scene Panel.

![Alt Text](https://i.ibb.co/6Pt5S3R/nn.png)

You have perfectly placed the Cap as a Head Decoration!


## Basics of the Sport (optional)

To code for the logics, you either use javascript scripting oruse the visual Drag and Drop based Patch Editor.
These are like the rulebooks of sports, which you design for proper functioning of your filter.

To create and effect you will be requiring a combination of Objects and Assets. Treat them as the players of your sport.
There are different types of object which can be added and can be categorised as:

Captain(Main): Scene Understanding
1) Face Tracker : Find Follow and Select faces in your scene
2) Plane Tracker : Identifies horizontal plane to place objects on the ground
3) Fixed Target Tracker : Can be used to track specific images in your scene.
4) Hand Tracker (only for facebook) : Can be used to track Hand's position in a scene.

(scene here is the camera feed which will be taken while using the filter)

Other Players: 3D, 2D, Lights, Effects
1) You can add 3D and 2D objects,Text,Planes, etc in your scene
2) There are 5 types of lighting available to light up your scene
3) You can also add sound effects and particle effect


Managers : Assets
All the material, textures, scripts, controllers, blocks, etc which may or may not be applied to your filter comes under the assets.



## The Effect to create

..............Text comes here..................................

Features to add:
1) UI Picker and Cap (1st half)
2) Background Segmentation (2nd half)
3) Effects (Super Over/Penalty)

## 1st Innings: UI Picker and Cap

In the Patch Editor, add the Picker UI Patch under the User Interface section. (right click -> User Interface -> Picker UI)

Add all the 8 texture provided in color texture folder
![Alt Text](https://i.ibb.co/Z8vjSL5/tex.png)

Select all the textures and in the inspector panel, select No compression (as Textures to be displayed in the Picker UI should not be compressed)
![Alt Text](https://i.ibb.co/SVLGVCS/com.png)

Now, in the Picker UI select the above 8 textures from texture 1-8 using dropdown as shown in the pic below :
![Alt Text](https://i.ibb.co/qp98CFM/picker.png)

At this stage, you can see different picker options in the simulator
![Alt Text](https://i.ibb.co/HhrX35b/simulator.png)


