# Unity Documentation  
The Unity Documentation is divided up into two main sections, the manual and scripting. The manual shows you how Unity is designed and how to use the editor. The scripting section is concerned with Unity programming. For the course, we’ll primarily be focusing on the scripting.  

## What are namespaces and how do I include them in my scripts?
The scripting API is divided into namespaces, which establish groups between related objects. Unity uses UnityEngine and UnityEditor primarily. The UnityEngine namespace contains objects that have to do with when the app is actually running. The UnityEditor namespace is all about extending the Unity editor. We’ll primarily be using what’s in the UnityEngine namespace.  

To use the UnityEngine namespace, for example, we’d write this at the top of our scripts.  

```c
using UnityEngine;
```

This line of code gives us access to everything within that grouping or namespace.    

The UnityEngine.Classes namespace contain all the important classes or objects that we should learn in Unity. Classes represent what’s common between objects. For example, all cameras have things in common and those things are described in the camera class.  

Tip: To jump directly to a components documentation, click the icon of the book with the question mark in the Inspector window.  

## What are references and how can I create one?
References allow you to pass objects and components into a script through the Unity Editor so you can control them in the script. References are defined in scripts at the top, above any methods the script may have. For example, you might have some of the following references in a script:  

```c
public float runSpeed;
public GameObject player;
public string playerName;
```

The word public in each of the lines above, allow us to see and change these in the Inspector. It’s also an “access modifier.” This means that other scripts in the project can see these things and use them. Other access modifiers are private and protected. Private means that only this script can access the references and we won’t be able to see them in the editor.  

The next part of the references is the “data type” of the reference. In our example above, we’ve got float, GameObject, and string. A data type lets our code know what kind of data we’re storing. In our runSpeed variable, we’d be storing a float like 2.5.  

Tip: A script can also be a data type. For example, let’s say we have a Door script.  

```c
public class Door {
    public bool isOpen;

     void Start() {
    isOpen = false;
     }

    public void Open() {
         isOpen = true;
         // Open door.
     }
    public void Close() {
        isOpen = false;
         // Close door
     }
}
```

We could have a second script that has a reference to an this door script that’s attached to a gameobject.  

```c
public  Door myDoor;
```

Inside that second script, we’d be able to call methods in our door script, by doing the following:  

```c
myDoor.Open();
```

The last part of references is the variable name. These names are written in “Camelcase,” which means that the first word is lowercase and each subsequent word is capitalized. Notice how there’s no spaces between the words? The capital letters help indicate a new word and make it easier to read. For example, playerrunspeed is much harder to read than playerRunSpeed.   

## What are Vector 3s?
The Vector3 variable type is how we specify positions in 3D space. Each Vector3 has an X coordinate, a Y coordinate, and a Z coordinate.  

## What are Quaternions?
Quaternions are how Unity handles 3D rotations. Unity uses them because they’re better for simulations. Unity handles all the complex math for us.  

I know I can control objects with code. Can I also create objects with code?
Yes! We can “Instantiate” objects, create a new instance of something, through code. We used the Instantiate method to create copies of gameobjects.  

```c
// objectToCreate is a GameObject that we have a reference to.
Object.Instantiate(objectToCreate, new Vector3(2, 4, 6), Quaternion.identity);
```

The instantiate can be used in a variety of ways. In the above example, the method is called and we pass in the reference to what we want copied (objectToCreate), where we want the object to be (the new Vector3 position), and how we want it rotated (Quaternion.identity is equal to the same rotation as the objectToCreate reference has).  

Sometimes we may want to save a reference to an object we create to change it in some way. (Like changing the color, adjusting the position, etc.) To do that we need to add a few more things to our instantiate line.  

```c
GameObject newObject = (GameObject) Object.Instantiate(objectToCreate, new Vector3(2, 4, 6), Quaternion.identity);
```

The first GameObject is the data type of the object we’re creating. The second part (newObject) is the variable name that we make up. The “(GameObject)” is called a “cast”. When we call the Object.Instantiate method, an object with a datatype of object gets returned. The cast is how we say that we plan on using that object as a Unity GameObject and not as a generic object type.  


## What are prefabs and how can I make one?  
Prefabs are Unity’s way of allowing you to save a GameObject in a file. This file includes all of the GameObject’s components and settings. Prefabs are a way for you to setup objects and reuse them across scenes. Prefabs are shown with little blue cube icons.  

To create a prefab, click and drag the object from your Hierarchy to your Project window.  

Tip: References can be created by dragging objects from the Hierarchy and the Project window. If you are creating objects via scripts and they aren’t looking like you expect, it’s likely because your reference is the object in the Hierarchy and not the prefab. To fix this, drag the prefab from the Project window into your scripts reference instead.  
