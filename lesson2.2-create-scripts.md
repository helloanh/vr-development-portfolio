# What are scripts?  
Scripts are behaviors that get attached to Game Objects in Unity. Scripts are made up of methods and properties.   

Methods are typically the major verbs. For example, the Start method contains all the instructions that need to be run when you first load the scene.   

Methods are a great way to organize your scripts into logical parts. For example, you might have a method that contains instructions for when a certain thing happens.  

## How could we add physics to an object to make it fall?
One way is to add a collider on the object and then add a rigidbody. This will use Unity’s physics system to simulate gravity and it will fall realistically.  

If we wanted to be more specific about how we wanted our object to fall, we would remove the rigidbody and collider from the object and add some code (in a script). If we decide that we want an object to fall until it hits the ground and then stop, we could add the following code in a script attached to the object we want to fall.  

```c
void Update() {
    // First we check to see if the coconut is above the ground.
    if(transform.position.y > 0.6f) { 
        // If the coconut is above the ground, we’ll make it drop a little. 
        transform.Translate(0, -2.5f * Time.deltaTime, 0, Space.World);
     }
}
```

## What does Time.deltaTime do?
If we’re doing something in an Update method, we don’t really know how often it will be called. It could be anywhere from 60 to 120 times a second for VR. Time.deltaTime helps smooth out any animations or updates over time, which means that it helps give framerate-independent animations and updates. This means that the animations or updates will look the same regardless of the frame rate. The variable Time.deltaTime contains the amount of time it took to render the previous frame. If we multiply that by a constant variable, our animation will run (or, in the given example, our coconut will fall) at the same speed if your frame rate is 60, 90, or 120 fps.  

#How could we get an object move back and forth between two points?
Our Mathf.Sin function is great for these types of use cases. In a script attached to an object we want to move between two points along the vertical (Y) axis, we’d add this bit of code in the Update method.  

```c
void Update() {
    transform.position = new Vector3(0, 5 + Mathf.Sin(Time.time * 5.0f), 0);
}
```

This line of code is basically, changing the object’s Y position every frame to a new position which is a Vector3. A Vector3 is a variable that contains an X, a Y, and a Z. In our example above, we create a new Vector3 each frame that has a 0 for X and Z and then the Y is the only variable that changes based on the Mathf.Sin function.  

## What are if statements?
If statements are very common in programming. They are essentially statements that check to see if something is true or false. Let’s take a non-code based example first and think about the logic behind it. If I have food in my refrigerator, Then I can make dinner at home. If I don’t have food in my refrigerator, Then I must go to the store or order takeout. The statements above can be shown in code.  

```c

bool refrigeratorHasFood = true;

if(refrigeratorHasFood) {
    CookDinner();
} 
```  

The if statement here, checks to see if my “refrigeratorHasFood” variable is true, which it is, so it goes into the if statement and runs my “CookDinner()” method. If statements often come with “else” statements. These are statements that get run if the if statement is false.     

```c
bool refrigeratorHasFood = false;

if(refrigeratorHasFood) {
    CookDinner();
} else {
    OrderTakeOut();
}
```

This time, the “refrigeratorHasFood” variable is false, so it doesn’t make it into the if statement. Instead, the code goes into the else statement and my “OrderTakeOut()” method is run.  
