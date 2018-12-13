### What are cameras in Unity?  
**Cameras** are a tool in Unity to show the virtual world to our users. Positioning the camera allows us to control and influence what our players see.    
  
### What is the camera’s clear flags property?    
The **clear flags property** tells our camera what to render if it doesn’t see a 3d object.    

Skybox is the default setting. It shows what the world looks like around your 3d models. A skybox is another type of material and could be a cityscape, desert, or just the sky.    

Solid color sets the background to a single color.  
Depth only is used when there’s multiple cameras, like when creating mixed reality footage.  

Don’t clear is NEVER used for VR. It uses the image from the previous frame as the background for the next frame. It’s very disorienting in VR.    

### How can I create my own skybox?  
Create a new material. Change the Shader from Standard to Skybox > Procedural. If you wanted to add this skybox to a camera, you’d add a Skybox component to the camera. Then drag the new skybox material to the Skybox component.

### What is the Culling Mask?  
The culling mask tells the camera which layers (or groups) of the scene it should render. It can be useful when we want to hide parts of our scene until we want them to be seen.  


### What’s the difference between Perspective and Orthographic cameras?
Perspective cameras work just like real life. Closer objects appear larger, and objects further away appear smaller. This is the one we use for VR cameras.    

Orthographic cameras render objects based on their size and not how close they are. A pencil that’s really close to the camera would appear smaller than a tree that’s much further away.  

### What about the rest of the camera’s properties?
**Field of View** controls the vertical angle that the camera will capture with a perspective projection. Based on that, Unity will calculate the horizontal angles. We typically don’t need to change this as the API we use for VR will typically handle this setting.  

Clipping Planes are two vertical planes is used to determine what gets rendered. Anything between those two planes will be rendered. The closer the two planes are, the better performance you’ll see. This is also known as frustum culling.  
  
**Viewport Rect** controls where on the scene our view is rendered. Normally a view is rendered to the whole screen width. We can change this if we wanted to change the percentage of the screen to use.  

### Why does the images for each eye need to be slightly offset?
Our brains go through a process called **stereopsis** that will fuse the two images together to create a sense of depth. Lens separation distance (LSD) is the space between the two lenses in our hmd and it directly correlates to the offset in the two cameras that are needed to render VR and the physical distance between the centers of our eyes (interpupillary distance or IPD). IPD ranges from 52 - 78mm (average is 63mm).  

### How could we build our own VR camera system?
Create an empty game object and position it in your scene.
Create two cameras - one for the left eye and the other for the right eye. Drag both cameras on top of the empty game object. Reset their positions.  

For the left camera, set the viewport width to 0.5.  

For the right camera, set the x coordinate of the viewport to be 0.5 and the width stay as 1.  

Shift the left camera to the left by an amount that’s half of the LSD value in meters. For example, if our LSD was 64mm, we’d shift the camera 32mm or 0.32 in Unity. (Remember that one Unity unit is equal to 1 meter.)
Shift the right camera to the opposite. If our left camera was shifted to 0.32, like in our example, the right camera would move to -0.32.  

### What is the difference between the Start and Update methods?
The start method is ran when an object is started up or created. The update method, however, is run each time a frame is rendered. For example, this could be as much as (or more than) 90 times per second for an Oculus Rift or HTC Vive or 60 times per second on a Google Cardboard headset.  

### How can we setup head tracking in our own VR system?
Create a new script and add it to the parent object of our two cameras. In the start method, we’ll enable the gyrometer.  

```c 

void Start() {
    Input.gyro.enabled = true;
}

// In our update method, we’ll use information from the gyrometer to adjust the cameras’ parent gameobject.

void Update () {
    // This line will get the rotation data from the gyrometer.
    Quaternion att = Input.gyro.attitude;  
    // This line will ensure that our gyrometer orientation lines up with our cameras’ parent’s orientation.
    att = Quaternion.Euler(90f, 0f, 0f) * new Quaternion(att.x, att.y, -att.z, -att.w);
    // Assign the converted rotation of the gyrometer to the camera’s parent orientation.
    transform.rotation = att;
}
```

### How does Google Cardboard sdk differ from the simple VR system we created?
Google’s sdk works to correct a couple of problem that occurs when you view a screen through a lense.  

The first is  **“Pincushion Distortion”**, this is the distortion we see when images appear to be “bulging” away from our eyes. Google fixes this by applying “Barrel Distortion” which effectively makes the image appear to bulge toward our eyes instead. When the images that’s bulging toward our eyes are viewed through our lenses, the pincushion distortion comes into play and makes the image appear flatter and more normal.  

The second issue is **“Chromatic Aberration”**. This distorts the colors on the edge of the lens shifting out in a rainbow-like pattern. Google’s sdk warps the colors on these edges to cancel out the distortion when viewed through lenses.  

In the VR system we created, we used the gyrometer to implement head tracking. Google’s sdk uses information from the gyrometer, accelerometer and the compass to achieve smoother tracking.  

### How do we setup Google’s VR sdk in our Unity scenes?
Once the sdk has been imported into Unity, it’s really quick to get it implemented for use in our scenes.  

#### Project Setup - Once per project.
1. Enable XR Settings by going to Edit > Project Settings > Player> XR Settings. Click the checkbox next to Virtual Reality Supported. Click the plus symbol and addCardboard.  

#### Scene Setup - Once per scene.
Add a GvrEditorEmulator to your scene. Place it where you’d want your camera to be located.  

Make your camera a child of the GvrEditorEmulator. Reset the camera’s transform component. Be sure your camera is tagged as “MainCamera”. Add a GvrPointerPhysicsRaycaster component to the camera. This will enable the camera to interact with 3D objects in your scenes.  

Add a GvrReticlePointer prefab as a child of your camera. This will give you the reticle (the little white dot) in the center of your camera. This is used to interact with things in your scene.  
