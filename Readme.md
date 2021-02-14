This Project is about making a smart camera which records video (in the night), and saves 
it only when there is movemente there.  
It doesn't use AI for the moment. Just some Computer Vision euristics.  
The idea is to use it to record wild life in the forest.


### The project can be divided into multiple subprojects (or subpipelines):

#### Connect a camera to a Raspberry:
We will start with the cero version, since it's cheaper and comsumes less energy).  
Get to be able to save video from it.

#### Be able to detect movement.
Build a movement sensor based on pixel values. We will create a heatmap of areas where the pixel value   
are different to one fram to another (it should have some memory or at least be robust to frame errors).  
example: if frame 3 is different to frame 2, also compare frame 4 with frame 1. If True, there is a change,  
i.e., somehting is moving).  

We will build a heat map of areas with biggger pixel differences.  

- For this we will lower the camera resolution and the fps (from 30 fps to 10 fps probably), so it doesn't consume all the battery.
- I've check movement sensors, but they are just low resolution cameras, so we can build that with our camera.


#### Take actions
1. Record only when movement happens
- Build methods to start-stop recording easily.  

2. Move the camera. (this is a whole new project).

#### Move Camera
1. Build a servo camera. These are the steps:
  - Buy a servomotor and make it move 45º every 10 secs (one lap in 80 secs).
  - Be able to move right and left (in the future also up and down).
  - Put all together ... see next point.  

#### Put all together:
- camera starts at position 0.
- It moves by default 45º every 8 secs (1 lap every 64 secs).
- But, if it detects movement it stays in position and does the next.
  - If object moving is in one side of the image, it will rotate 5º per sec until the object is kinda centered.
- After no movement in last 10 secs camera comes back to saving battery. It stops recording and keeps rotating until movement is detected.

#### Final thoughts:
This is a project to record what happens in the night. It could be used for security or for monitoring wild life
In the future we could add a microphone, improve the camera, battery life etc.
It can also be a first approach to drones and robotics.

