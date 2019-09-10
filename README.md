# beginners-guide-to-ai-unity-course

Course notes to Beginners Guide to AI in Unity Udemy Course

## Vector Mathematics Refresher

Characters in 3D space have both a local and global axis in space.  These axis do not need to align to the same direction.  

Vectors are represented by a magnitude and direction (an arrow).  The magnitude of the ray is the sqrt(a^2 + b^2).  A vector in 3 dimensions has the same magnitude and direction, but adds the additional Z axis.  

In Unity, we can move a character from one position to the next using the transform.Translate() method.  To figure out the vector between a characters current position and their target position, you can use the formula: vector = target.position - character.position.

If you want the character to move over time, you need to break up the vector previously defined into smaller vectors pointing in the same direction.  You can do this by dividing that vector by some value (i.e. time).  A better practice, however, would be to divid a vector by an amount that causes the smaller vectors to maintain the same size regardless of distance.  This is known as normalization.  In normalization, the unit length of the vectors is 1.  To do this we divide the vector (x,y,z) coordinates by the magnitude.

In Unity, you can use the Vector3 data structure to work with objects in 3d space.  To get the direction between two vectors, take the goal - character.  You can grab the magnitude using the Unity function direction.magnitude and the normalized vector by using direction.normalized.

In Unity, there are a few ways to change the Rotation between where the character is facing in relation to the target.  If you wanted your character to immediately face the target, you could use the _LookAt_ method.  If you wanted a cleaner rotation towards the target, you could use the _Slerp_ method.  And finally, if you wanted to get the angle between the character and the target, you can use the _Angle_ method.

```csharp
// LookAt
stevie.transform.LookAt(granny.transform.position);

// Slerp
Vector3 direction = granny.transform.position - stevie.transform.position;
stevie.transform.rotation = Quaternion.Slerp(stevie.transform.rotation,
                            Quaternion.LookRotation(direction), 
                            Time.deltaTime * rotationSpeed);

// Angle
Vector3 direction = granny.transform.position - stevie.transform.position;
float angleOfRotation = Vector3.Angle(stevie.transform.forward, direction);
```

## Moving

### Moving in a Straight Line

### Traveling to a Goal Location

### Pushing the Character Forward

### Slerping

### About Animation and Translation

### Waypoints
