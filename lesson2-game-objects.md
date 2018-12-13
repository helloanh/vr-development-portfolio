#Lesson 2: Game Objects  

In this lesson we learned…   

## What are VR scenes made of?  
Everything you see in a VR scene is made of something called meshes. Meshes are made of triangles which are made of points. We use triangles to represent 3D objects because it’s fast, easy, and computers are optimized for them.  

## What are Primitives and how can I make some in Unity?  
Primitives are very basic 3D meshes. Some examples of them include cubes, planes, spheres, and cylinders. There are a couple of different ways to make a primitive object in Unity. One way is to go to GameObject > 3D Object and then select the object you wish to create.  
   
## Does Unity support creating more complicated models?  
Unity focuses on rendering 3D scenes and does NOT support creating more complex models. You’d have to use a separate specialized program like Blender or Maya to create complex models. You can also get 3D models online (from a site like Poly) or through the Unity Asset store.  
## How can I bring a 3D object into my scene?  
To get the model from your computer into Unity, you can go to Assets > Import New Asset and navigate to where the model is on your computer. Once the model is in your project. Drag the 3D object from the Project window into the hierarchy. Use the move tool arrows to position the object where you’d like it to be.  

## What are transforms?  
Every gameobject in Unity has a Transform component. This is the component that tracks the object’s position, rotation, and scale. You can change the properties by changing the values in the Inspector or by using the move, rotate, or scale tools in the upper left corner of Unity.  

## What are transform hierarchies and how can I create one?  
Transforms can be “nested” inside of other transforms. This allows transforms to be grouped together. If the top level (also called “parent”) transform rotates, each transform that’s nested inside it (also called “children”) will also rotate. To create a nested group of transforms, click on one object in the hierarchy and drag it on top of another object in the hierarchy. Indentions in the hierarchy indicate these nested transforms and parent-child relationships.  

Tip: You can also create a hierarchy by clicking a gameobject in the project window and dragging it on top of an object that’s already in the hierarchy.  
