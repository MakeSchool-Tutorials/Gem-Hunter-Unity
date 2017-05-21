---
title: "Level Setup"
slug: level-setup
---
We’re ready to set up our level.

First off, our camera view isn’t in the best spot for a top-down game, so let’s adjust that.

> [action]
>Select Main Camera.

This is the way players will see in our game!  Since you can have more than one camera in a scene, probably the most important feature of Main Camera is the tag MainCamera. Unity looks for the object with this tag to use as the Camera to use to make a scene’s Game View.

![MainCamera tag](../assets/image_27.png)

> [action]
>Set Main Camera’s position to (0,8,-8) and set its rotation to (45,0,0), so that it’s a little more interesting than straight downward.

As you were doing this, you may have noticed that the Scene View provides you with a handy preview of what the Camera sees in the bottom corner. You can view through a Main Camera also by selecting the Game View at the top at any time.

![Camera view](../assets/image_28.png)

Now for the level.

> [action]
>Create a new Plane (GameObject->3D Object->Plane) and position it at (0,0,0) if it isn’t already.

When you look through the camera, you may notice it’s a little difficult to make out the geometries you’ve got there.

![Too much light...](../assets/image_29.png)

> [action]
>Set the Directional Light’s Light Type from Directional to Point and Bounce Intensity to 0.

![Point light to the rescue!](../assets/image_30.png)

Much better.

Our plane at (0,0,0) is currently going through our Player, but rather than moving our Plane down, let’s move our Player’s child Cube up a bit.

> [action]
>Select the Player’s Cube and set its position to (0,0.5,0).

![Set Player's position](../assets/image_31.png)

The reason we’ve moved our Cube up rather than our Plane down is because then y = 0 will be the ground, which is easier to remember than y = -0.5.

> [action]
>Add a Cube at position (5,0.5,0) and scale (1,1,10) to make a wall.

![A Wall](../assets/image_32.png)

> [action]
>Now add 3 more such Cubes to make the remaining walls along the other edges of the Plane. You may find it helpful to use the coordinate widget in the top right of the Scene View to make sure everything is aligned as you’d like it to be. You can click a second time on the widget to switch between Perspective and Orthographic views.
>
![4 Walls](../assets/image69.gif)

If you Play the game now, you’ll be able to move around in the space, but you’ll go through the walls.

![Collisions missing](../assets/image_34.png)

> [action]
>Add a Sphere Collider component to Player and set its center to (0,0.5,0).

![A sphere collider added](../assets/image_35.png)

The Cube has done us well so far, but now we want something that clearly faces a direction so we can make our Player face the direction of motion.

> [action]
>Open up the Asset Store window (Window->Asset Store) and search "Survival Shooter Essentials."

![Survival Shooter, searched](../assets/image_37.png)

Hit "Enter" and click on Survival Shooter.

![Survival Shooter, found](../assets/image_38.png)

> [action]
>Click on Download to begin the download process. You may need to create an account or sign in to the Asset Store.
>
![Download](../assets/image_39.png)
>
![Create account, if need be](../assets/image_40.png)
>
Read and accept the license agreement if need be.
>
![License agreement](../assets/image_41.png)

<!-- -->

> [action]
>You may get a warning, since this project involves some Project Settings. We don’t plan on importing them, but you’ll need to click "Import" to progress to the next step.

![Import project settings](../assets/image_42.png)

When you do, a window should appear listing all the bits and pieces that come with this package. Check marks indicate items that will be imported when the "Import" button in the bottom right is clicked.

![Check marks everywhere](../assets/image_43.png)

> [action]
>Go ahead and click "None" to uncheck everything, and then check the following:
>
* Materials/ZombearMaterial.mat
>
* Models/Characters/ZomBear.fbx
>
* Prefabs/ZomBear.prefab
>
* Textures/ZomBearDiffuse.png
>
* Textures/ZomBearEmission.png
>
* Textures/ZomBearNormal.png
>
![Assets img 1](../assets/image_44.png)
>
![Assets img 2](../assets/image_45.png)
>
![Assets img 3](../assets/image_46.png)
>
![Assets img 4](../assets/image_47.png)

<!-- -->

> [action]
>Then click "Import."  When you do, new folders should appear in your Project Panel.

![New folders appear](../assets/image_48.png)

> [action]
>For better organization, create a new folder called Downloads and drag in the new folders that were created (Materials, Models, Prefabs, Textures).

![Organization is good](../assets/image_49.png)

Now we’re going to replace our cosmetic Cube that’s a child of Player with a ZomBear.

> [action]
>Select the Scene tab to switch back to your Scene View from the Asset Store.

![The Scene tab](../assets/image_50.png)

> [action]
>Select Player in the Hierarchy Panel. In case you can’t see it in your Scene View, with Player selected, hover over the Scene View and press the "f" key.

![Player selected](../assets/image33.gif)

> [action]
>Now Drag a ZomBear Prefab from Downloads/Prefabs/ in your Project Panel onto Player in your Hierarchy.

![Adding the ZomBear](../assets/image23.gif)

> [action]
>Delete the Cube from Player (right-click it and select "Delete"), and your Player should now just be visually represented with the ZomBear!

![Cube deleted](../assets/image_53.png)

If you try to run the game though, you’ll notice a few issues. First, the Player appears to glitch to the side on the first few frames.

![Moving to the side](../assets/image60.gif)

Second, if you select the Console Panel in the bottom, you’ll notice a few Warnings.

![Warnings](../assets/image_55.png)

We’ll fix these issues by removing some components the ZomBear Prefab has that we simply don’t need.

These are occurring because we didn’t import the scripts that the ZomBear Prefab uses to make it act like a ZomBear, because we don’t want it to. Even so, the Prefab imported with references to these nonexistent scripts, so we’ll want to remove them.

> [action]
>Select the ZomBear nested under Player and scroll through its components until you see a missing script. Simply remove each of those components (there should be 3).

![Missing Scripts](../assets/image_56.png)

> [action]
>Additionally, remove the:
>
* Animator
>
* Rigidbody
>
* Capsule Collider
>
* Sphere Collider
>
* Nav Mesh Agent
>
* Audio Source

That’s… pretty much everything actually, so when you’re done, only the Transform should remain.

![Just the transform](../assets/image_57.png)

You may notice when you remove the Animator component that the ZomBear flips 90 degrees. 

> [action]
>To fix this, set its rotation to (0,0,90).

![90 degree flip](../assets/image_58.png)

Now when you run the Scene, you should get no Warnings in your Console, nor should the Player appear to glitch to the side.

By the way, in case you want to make the Console visible at all times, you can reposition it by clicking and dragging on the tab.

![Drag console](../assets/image01.gif)

If you rearrange the panels in a way that you prefer, you can save that layout by selecting Layout->Save Layout in the top right-hand corner.

![Layout dropdown](../assets/image_60.png)

![Layout menu](../assets/image_61.png)

If you’ve saved a layout, you can use it at any time by selecting it from this menu. This tutorial uses the Default layout, by the way.

We’re also going to clean up ZomBear a little bit.

> [action]
>Expand ZomBear, and you’ll notice it has some children of its own.

![ZomBear children](../assets/image_62.png)

Zombear (not to be confused with ZomBear) has the mesh that makes the form and color of the model and has an object with a light nested to it. HitParticles and DeathParticles are Particle Systems that rely on some things we haven’t imported.

> [action]
>Delete HitParticles and DeathParticles.

![Delete stuff](../assets/image_63.png)

Great!  Not only is this model pretty, but it's also asymmetrical so we know which way its facing.
