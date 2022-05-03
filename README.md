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

We also added the collision event on the boxes and removed the bullet element from the scene after the collision.

We also learned how to navigate around the scene without colliding objects by creating a navigation mesh and using the movement-control component.

------------------------

We have enemy tanks models in the scene.
Now we should be able to fire bullets continuously from these tanks.


The direction of shooting will be from the enemies towards the player.

for 

to find the direction vector, we will get the object's position, the enemy object, and the player object, as the Three.js positions.
this, we need to find the direction vector between the enemy and the player.


We will take two variables and initialize Three.js vector variables using new THREE.Vector3().

Great! Let's look at the ememyShoot.js file that registers the A-Frame component called “enemy-bullets” with a function named shootEnemyBullet()

----------------
Since we want to shoot the bullets continuously, We can use the setInterval() method.


----------------
Suppose we have 10 enemies in the scene, then creating bullet entities for each tank will be cumbersome.
To avoid that, we are going to give a class name to each of the enemy tank entities and then we can access all the entities using the class name.

Now to access entities using class names we are going to use the document.queryselectorAll() method and the class name inside the brackets.
To select elements using class names we use dot instead of hash.


-----------

we should have to loop through all the elements to create the bullet entity for each one of them.

--------------
we need to set some velocities of the bullet so it starts moving.


We will use the Three.js method to see the direction of the enemy to shoot the player in such a way that it is always the player to shoot.


-----------

We need two THREE.Vector3() variables, position1 and position2 in which we can store the position of the enemy object and the player object.
We can use the getWorldPosition() method of the Three.js library to store the value of player position and enemy position as vectors.


----------

Now to get the direction vector from any two players, we need to use the subVectors() method which gives the result after subtracting two vectors.
Before we can use the subVectors() method, let's first understand the concept of finding direction vectors


----

vectors are mathematical objects which have magnitude and direction.
The magnitude value tells how long the length will be starting from one point to another.
The direction tells in which direction the vector will be starting from the origin that is (0 0 0).
Also, to find the direction between two points, say point 1 and point 2, we will have to subtract the position vectors of the points in the reverse order.

---------
take a direction variable and use a subVectors() method to find the vector between position1 and position2.
We use .normalize() to get the unit vector that is the direction vector of length 1.


once we get the standard vector we can multiply it with any number to increase the velocity in that direction.

--------------


we should be able to detect the collision between the bullet and the player to update the player’s life.
For this:
● Set dynamic-body attribute of the enemy bullet entity.
● Select the countLife text to update the player life count.
● Add the collide event listener to check if the weapon element has been hit.
● Decrease the player’s life and update the text attribute.

----

To make sure the collision is being detected by the weapon element:
● Update the weapon entity bounding shape to set the body and the shape component manually.

---

Once the player life is zero, we can show the over text and remove all the tank elements from the scene.




