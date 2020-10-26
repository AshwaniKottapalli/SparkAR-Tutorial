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

First download the contents from [this link](https://drive.google.com/drive/folders/12YWuOooQGPqkYc-PadU9idMbZoNool3T?usp=sharing)  

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

IPL (Indian Premier League) is one of the top leagues in the world. In commonwealth countries, particularly in India : Cricket is considered as a religion. In this tutorial we will be creating a filter where you have option of selecting your favourite team and you will be wearing the cap of the team and the background will change to fan slogan of that team. 



Features to add:
1) UI Picker and Cap (1st half)
2) Background Segmentation (2nd half)
3) Effects (Super Over/Penalty)  (To be Added)

## 1st Innings: UI Picker and Cap

In the Patch Editor, add the Picker UI Patch under the User Interface section. (right click -> User Interface -> Picker UI)

Add all the 8 texture provided in [teams folder](https://drive.google.com/drive/folders/1KYS7ELUNJRb5yG-Fz39KvQCOU67ACnva?usp=sharing).


![Alt Text](https://i.ibb.co/Z8vjSL5/tex.png)

Select all the textures and in the inspector panel, select No compression (as Textures to be displayed in the Picker UI should not be compressed)


![Alt Text](https://i.ibb.co/SVLGVCS/com.png)


Now, in the Picker UI select the above 8 textures from texture 1-8 using dropdown as shown in the pic below :


![Alt Text](https://i.ibb.co/qp98CFM/picker.png)


At this stage, you can see different picker options in the simulator

![Alt Text](https://i.ibb.co/HhrX35b/simulator.png)

Next, we need to work on logics for changing the texture on the cap when a specific texture is selected in the picture.
For convenience we will use the same texture on the hat as used in the picker. 

In the Picker UI Patch, there are two outputs: Selected Option Index and Selected Texture. 
In the current case, we just need to take the Selected Texture output from the Picker UI Patch and join it to the texture of the material of the cap.

To do so, we need to click on the hat_mat, which is the material for the cap. In the inspector panel under diffuse, there is an option to select the texture for the cap,
on the left there will be an arrow, click on it to generate a patch for the Material's Texture.

![Alt Text](https://i.ibb.co/J3WCQvx/text.png)

Now just connect the Selected Texture Output of Picker UI to the Input of hat_mat Diffuse Texture Patch

![Alt Text](https://i.ibb.co/F8NhwQV/picker-Ui-Patch.png)

At this stage, our filter has a Native UI Picker which has all the 8 IPL Teams, on selecting a team the Face Tracked is made to wear the team's cap.

![Alt Text](https://i.ibb.co/Hn7rM8v/ss.png)


## 2nd Innings: Background Segmentation
We will further divide this innings into two subparts, Firstly  Enable Background Segmentation and then add the background depending on the Native UI Picker texture selected.

To Create the background segmentation effect, first in Scene Panel, click on Add Object and add two rectangles.
Name them user and bg respectively. Both of them would be visible in the scene panel as a child of Canvas Object.

Now, select both the user and bg rectangle by holding cntr(cmd for mac) and clicking on both. Once selected, in the inspector select **relative and 100%** for both width and height.

Now Select the bg rectangle and in the inspector, select the dropdown of Layer and add a new layer (Layer1 by default)

Next, create two materials user_mat and bg_mat and add them to the respective rectangles.

Now, select Camera object in the scene panel and click on the "+" for segmentation on the inspector panel and select person. This will create a person segmentation mask texture. Also click "+" next to the Texture Extraction for creating cameraTexture0.

Now select user_mat on Assets Panel and select the cameraTexture0 as its texture.

Lastly go to Layers Panel and keep Layer1 below Layer 0.

Your segmentation would be done!

If you are unable to follow the above instructions, check the [documentation](https://sparkar.facebook.com/ar-studio/learn/articles/people-tracking/background-segmentation#adding-objects)

Now that Segmentation is done, we want the texture of bg_mat to change with change in texture of Native UI Picker.

For this, we would be using the option picker patch and connect its option input  with the output Selected Index of the Picker UI Patch. 

![Alt Text](https://i.ibb.co/w6LGg41/option-Picker.png)


Once added, on clicking on the option picker patch, you get an option to select the data type at the bottom (Number by default), change it to texture.
Take cursor to the bottom most part of the patch and expand the patch for 8 inputs, as we have 8 teams.

Now based on the team name select the background from the given background in the [bg folder](https://drive.google.com/drive/folders/1UcEDSfmqzz6PTlc59jtTAzG1JEnmhy8w?usp=sharing) . When done just take the output from the Option Picker and connect it to the Texture Patch created from the bg_mat material.

![Alt Text](https://i.ibb.co/BZbb9Vs/final-Patch.png)

Its done!! 

The Simulator after 2nd innings:

![Alt Text](https://i.ibb.co/DD66LnH/sim.png)

Now we have our own IPL Filter! Use it to make stories supporting your team or you can be more creative and create reels with talk between supporters of different teams. The sky and your creativity is the limit!

As you noticed, Learning SparkAR to create filters is as easy as playing a game of football or cricket. All you need to know are the rules and features and then you too can create filters for the masses!




