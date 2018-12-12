### My Notes 

## Challenges of VR  

- simulator sickness  
= anything that causes a mismatch from your body's internal sense of motion and the brain

## Short History of VR  

- 3d display tech, in steraoscope in 1838  
- English inventor Sr Charles Wheatstone - one pic shows on the left eye, one on the right eye.  mirrors at 45 angle to view the same object.  

- sword of Damocles is considered the first, Ivan Sutherland in MIT in 1968 - first device to track head motion. user is shown privitive 3d objects like square boxes  

-1990s, VR first promoted to the public. example: Nintendo the Virtual Boy headset was a flop.  it caused headaches, too bulky.  hype died away.  

- until 2012, kickstarter started for Oculus Rift. used a single panel device system.  now acquired by Fb.  

- now we are experiences second wave of VR and it's here for good.
## 3-DOF vs 6-DOF   

**Degree of Freedoom**: 3dof tracks xyz axis, usually what mobile vr.   6DOF tracking for your head AND position.    

### 3-DOF  

How they do it?  Inertial Measurement Unit - a tiny sensor to detect rotations.  Use gravity and earth's magnetic field to detect which direction you are viewing.  All 3-DOF tracking uses some kind of IMU.  

### 6-DOF  

Things are trickier.  Any area of ongoing research.  Almost every high-end VR uses a different system.  Magnetism and acoustics, etc.  

Oculus Rift uses constellation - uses LEDs.  Constellation is good and cheap.  HTC Vive uses Lighthouse, which also uses infrared lasers, by using the time it takes between flashes.      

## Mobile vs. Desktop  

Mobile only 3DOF, not position.  Mobile VR is untethered, no wired.  Less powerful.  You have to optimize more.  

Desktop, you get 6DOF.  Headset is tethered, you need a cable.  Usually high visual quality.  Sometimes has hand controllers. 

## Types of VR Development Platforms  

Code or graphical editor-based environment for VR.  You can use game engine, like Unity.  Can reduce iteration time.  

Game Engine provides: 3d rendering, physics, sound, scripting, asset management, etc.  Packages of tools to make it easier to build game.  

There's also Unreal Engine, Lumberyard, etc.  You can also use OpenGL, Microsoft DirectX.  Native Development has more flexibility but longer development times.   

There's also web browers, like WebVR, but not currently good enough for production use.  

For now, as a VR developer, our main choice is a Game Engine or Native.  

###  Major components of hardware 

**Low persistence** causes each pixel in your VR display to illuminate for only a brief period of time. This reduces motion blur when you turn your head. As a side effect, it actually slightly decreases the apparent brightness of the display.   

**Tracking** IMUs or inertial measurement unit enables high speed rotational tracking.  IMU cannot tell where the object is located in space, only how it is located.  In order to tell where the object is located, VR systems use lasers and precise clocks, magnetic field, and cameras.  

VR requires some kind of tracking in order for it to work.  
