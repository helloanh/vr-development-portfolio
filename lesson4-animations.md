How can I create an animation?
Select an object in the hierarchy. In the Animation window, click Create. Choose a name for your animation and save it to an appropriate folder in your project. Click Add Property and select a property you want to animate.

The timeline (also known as a dopesheet) contains all of the frames of our animations. Keyframes are indicated by diamond shapes in the timeline and are key points in our animation where we can update properties. To create new keyframes, double click on the timeline. You only need to define a few keyframes to create smooth animations. The points in between keyframes are created using interpolation, averaging and smoothing.

What is the difference between the Play button in the Animation window and the Play button at the top of our Unity editor?
Clicking the Play button in the Animation window, runs only the animation. The Play button in the top of the editor will play our entire scene.

Our animations might not loop seamlessly. It tends to lag a bit at the start or end of our animation. How can we fix that?
This can happen if the tangents of our animation are not set to be linear. To resolve this, in the animation window, there are two tabs. One for “Dopesheet”, which is the one that we start on by default. The other is “Curves”. Click on Curves and you’ll see a line that represents our animation. Click on the first keyframe, and set “Both Tangents” to “Linear”. Do this for the last keyframe as well.

Tip: If you’re working with a larger animation with more keyframes, you may want to do this with all your keyframes.

What are animation controllers?
Animation controllers are the files that controls all the animations associated with a given object. These controllers control properties of the animations like when an animation is played, how to transition between animations and blending animations together.

What is the difference between the Animator window and the Animation window?
The Animator window is what controls all our animations for a given object. The Animation window lets us see and modify a specific, individual animation.

What is the Mechanim State Machine?
In the Animator window, you’ll see several boxes. By default, an animator controller has Entry, Any State, and Exit states. The Entry and Exit states are used for when the object starts up and ends, respectively. The Any State is a special state that represents all other animation states. There will also be one for each animation on the object. The Mechanim state machine is what connects the various states together and handles transitions between animations, or “states”. At any point, our object can only be in one state and playing one animation.

How do I transition between states in the Animator (Mechanim State Machine)?
Right click on a state and select Make Transition. Then click on another state. This will create a transition (represented by an arrow) from one state to another.

How do I control states in the Animator?
We use parameters to control the various states in our Animator. To create a parameter, click on the Parameter tab in the Animator window. Click the plus icon, then select the type of parameter you’d like to create. There are options for floats (decimals), int (whole numbers), bool (true or false), and trigger (a bool that resets back to false immediately after the transition occurred).

I have my parameter setup, but how do I actually use it?
In the Animator window, click on the transition (arrow) you want to use the parameter. Then in the Inspector window, you will add it to the “Conditions” by clicking the plus icon.

I want my transitions to happen immediately. How can I adjust when my parameters take effect?
By default, Unity assumes that an animation should complete before transitioning to another state or animation. This is a concept called “Exit Time”. To change this, click on the transition arrow in the Animator window. Uncheck “Has Exit Time”.