# 165

The AnimationMixer is a player for animations on a particular object in the scene. When multiple objects in the scene are animated independently, one AnimationMixer may be used for each object.
--------------------------------------------------------------
a-entity animation properties:

dir	Which dir to go from from to to.	normal	alternate, reverse
----------------------

We wrote the component to create bullet entities. In that we:

Get the camera direction as a Three.js object.
● Get the camera position as an A-Frame element.
● Set the velocity of the bullet.
