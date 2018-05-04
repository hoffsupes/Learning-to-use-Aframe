# Learning-to-use-Aframe
Aframe relies on AR.js to make WebVR applications. I'm uploading my own attempt at learning to use Aframe or at least the basics of it. It uses HTML and javascript to do the same.


Hello!

I'm teaching myself various things from time to time. 

This time, it's Aframe! In this excercise I'm trying to solve some problems which I faced before when trying to use aframe (and I also found that people go through the same when they start off with using aframe so I hope they can use this as a handy guide if they run into those problems and come across this repo)

## A1

1.) What are basic parent child relationships in aframe? Create an example on how this concept can be used to build something in aframe?

2.) How to use 3D models in aframe, especially OBJ files?

## A2

Common Problems faced:

1.) OBJ models do not show up

2.) Placing custom models is a pain when manually changing values, unable to find a proper frame of reference

## A3

Other problems faced elsewhere:

1.) How to traverse from one VR page to another?

2.) I implemented 1.) but its not working! I click on it but nothing happens!

3.) How to create a 360 degree panorama in aframe?

4.) Can I add cool effects to my entities?

5.) I'm working with a marker in the real world, but the track keeps getting lost! That is, the 3D object shows up but never stays for more than a few seconds, or does not show up at all!

# Solutions:

## A1

1.) All properties for a parent are also inherited into the child entity (animations, scale etc.), moreover the coordinate system for the child entity is centered at the parent entity. That is, whenever we talk about child position coordinates, we're talking about a relative coordinate system!

2.) OBJ files require you to also have the corresponding MTL files, otherwise they might not show up

## A2

1.) Try scaling them down! If not check your files, are you naming them correctly when you type them in? Everything is case sensitive!

2.) Pretty handy for me, open the inspector, **Ctrl + Alt + I**. You can move stuff around and change the position of your viewing window 

Protip for **1**: Use a combination of **A2 1 and 2**, that is insert the object at a slighty scaled down size, say [0.1 0.1 0.1] along the X , Y and Z axes and then if it does not show up, visually inspect to see if it atleast shows up in the world, try zooming out! If not, then there is some problem with the OBJ file or your naming convention, are you sure you also included the MTL file?

## A3

1.) Use links! https://aframe.io/docs/0.8.0/components/link.html#sidebar

2.) You need a *cursor*, aframe relies on something akin to *raytracing* called *raycasting*. The (very) principal idea here is that one shoots a ray from the user's cursor and determines the first point in the world that it hits and marks that point as being visible by the user. Since the cursor is also over it, that point is considered as being hovered on. Mouse clicks can now be detected! So declare a cursor and make sure that the cursor *is pointed at the portal/link* when you click. This is what an end user would also do when using the app on their phone!

3.) Use a sphere <a-sphere> </a-sphere> texture with an equirectangular image projection, typically created with a number of images (projection of spherical coordinates onto a horizontal and vertical coordinates )

4.) <a-animations> </a-animations> help!

5.) Decide on your application, are you moving the marker or the camera? https://aframe.io/blog/arjs/#move-the-camera-or-the-marker. Fix your objects as child entities to it afterwards!
