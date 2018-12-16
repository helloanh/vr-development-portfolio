## How can I use Unity’s UI elements in my VR scenes?
Unity’s Canvas defaults to a “Screen Space - Overlay”, which renders everything over the whole main camera. However, in VR we can’t use it in that mode. We need to switch the canvas Render Mode to be “World Space”.  

After we change the render mode, we then have to size the canvas appropriately. We can use the scale tool to resize the entire thing down. Then we need to position it in the scene.  

## The text on my canvas is blurry. How can I fix it?  
To fix blurry text on a canvas, we’ll increase the Canvas’s Dynamic Pixels Per Unit. This value defaults to 1. Increasing it will sharpen the text. Increasing this number too much can lead to performance issues, so it’s recommended to keep this as low as possible.  

## How do I make a 3D object interactable?
We need to add a couple of things to make an object interactable.  

Add the GvrEventSystem to the scene. Or you can make your own by creating a new event system and adding the GvrPointerInputModule component to it.  

Add a collider to the 3D object. This can be a box collider, a sphere collider, or any type of collider.   

Add an Event Trigger component to the 3D object.  

Click Add New Event Type to add a PointerClick event.  

Click the plus to add an empty object holder. This will hold the object that will perform some action when the event happens.  

Wire up the object by clicking and draging the object with the method you want to call from the Hierarchy over to the object holder box in the PointerClick event trigger.  

Decide on a method to run by clicking on the “No Function” dropdown. Navigate to the script and method you want to call when the event happens.  

## What’s a debug log statement and what are they used for?
Debug log statements are used a lot for testing and problem solving our code. We’ll see these messages in the Console window. To write one:

```c
Debug.Log(“My message here”);
```
You can include any message in a debug log statement. If we wanted to test if a method was called that could be  

```c
Debug.Log(“My method was called.”);
```

Debug log statements can also include variables through a process called “Concatenation”. It will essentially put strings together. For example, let’s say we wanted to print out a player’s score when he scores a point.  

```c
public float score = 0; 

public void ScorePoint() {
    score++;
    Debug.Log(“We’ve scored a point. We now have “ + score + “ point(s).”);
}
```

Whenever the ScorePoint method is called, we would increment the score value by one and print out a line with the score’s value. The first time the method is called, we’d print out a line that would say “We’ve scored a point. We now have 1 point(s).”    

## How can I write a script that changes the scene?
Be sure that your scenes have been added to the build settings.  

Open build settings by going to File > Build Settings.  
Click and drag your scenes from your Project window into the “Scenes in Build” box at the top of the Build Settings.  

Tip: The first scene listed in the build settings is going to be the first scene that loads up in your build files.  

Add some code in a script to change the scene.  

```c
using UnityEngine.SceneManagement;

public class ChangeScene : MonoBehaviour {
     public void GoToScene() {
          SceneManager.LoadScene(“Name of scene to load“);
     }
}
```

Replace the “Name of scene to load” with the name of the scene you want to switch to.    

Another way we can accomplish the same thing is to use a variable (also known as a parameter) to set the scene name. This would give us some flexibility with our script, so we could change the scene we load in the Unity editor.  

```c
using UnityEngine.SceneManagement;

public class ChangeScene : MonoBehaviour {
     public void GoToScene(string sceneToLoad) {
          SceneManager.LoadScene(sceneToLoad);
     }
}
```

When we do the next step (setting up the Event Trigger), we’ll need to include the name of the scene we want to go to in the box underneath the function name.  

Call the script with an Event Trigger. (See the above review question for making 3D objects interactable if you need a review.)  
