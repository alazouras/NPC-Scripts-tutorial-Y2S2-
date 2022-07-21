# NPC-Scripts-tutorial-Y2S2-
Tutorial for how the NPC scripts work in '3D Blocks...' (year 2 semester 2 work)

For this tutorial, we need two scripts; one I called NpcMovement (for getting the NPCs to move around the map) and one called RangeToStop (to track when and why the NPC may stop along the way).

# 1) MpcMovement script
To start with, for this script we need the following components:

![image](https://user-images.githubusercontent.com/91538155/180267028-cdd15e3c-e227-47b6-8020-9bb953dfd953.png)

These NPCs have two instances where they'd stop; if the player is near enough to them to talk to them, and at random moments along their waypoint loops in order to make their walk cycles less repetitive and a bit more organic.

Next, in Start, we need to make sure both the Movement and Potential Stop coroutines (which we will write in a moment) are on:

![image](https://user-images.githubusercontent.com/91538155/180267313-7c1b43b5-d5bc-4575-97cf-fb0717d6e09a.png)

Next, deleting Update, we need the following void for starting and stopping the coroutines. For starting, we simply need to do the same thing as start and make sure both coroutines are running. This is so that if the coroutines stop for any reason, they can be started again:

![image](https://user-images.githubusercontent.com/91538155/180267486-cc2895a2-1534-496c-a1da-4f6128d30c33.png)

Next, for stopping, we need one line of code to stop both coroutines:

![image](https://user-images.githubusercontent.com/91538155/180267606-497f52e8-10ff-46df-9e2f-4196bc8fd1e3.png)

Now that that's sorted, we need IEnumerators for both Move (the NPCs moving around the map) and Interupt (when the NPCs stop or are stopped in their movement). Starting with Move, we need to first establish the offset with this if statement:

![image](https://user-images.githubusercontent.com/91538155/180267877-8f95aab2-981c-483a-add6-548f45f46cc5.png)

Next, we need a while statement underneath in order to get the NPCs to continue moving even if they stop at a point that's not one of the established waypoint empty game objects:

![image](https://user-images.githubusercontent.com/91538155/180268084-66b12465-4e4b-4059-a3e7-e519cb665e8e.png)

Finally for this function, we need to make it so that the NPC continues up an unestablished number in an array (as each NPC has a different number and placement of waypoints), therefore increase the offset, and finally restart the loop once the NPC has reached their final waypoint:

![image](https://user-images.githubusercontent.com/91538155/180268380-bf1ca87f-0118-4e4a-abf7-5a706489f342.png)

Next, in the Interupt function, we need to establish that the NPC will stop moving at random, publically editable times in their loops, in order to make the movement more organic. to do this, we need to allow for random time intervals and stop the movement coroutine for a set amount of time, and finally restart both he move coroutine (to get the NPC to move) and the interupt coroutine (to allow the game to restart the timing process to pause the NPC again:

![image](https://user-images.githubusercontent.com/91538155/180268744-722330cc-cbf4-460a-9d1c-980276b242d8.png)

That is all that is needed for this script.


# 2) RangeToStop script
This second script is to get the NPC to stop moving if the player is in range of their collider. This is to make talking to NPCs, especially the one's that move quickly, much easier, as talking to them while they're mid movement would be difficult to do.

For this simple script, we don't need any new components, Start or Update. All we need are two private voids; one to stop the NPC is the player is in range, and one to restart the NPCs movement in their initially set direction once the player is out of range again. For the first void, we need this if statement:

![image](https://user-images.githubusercontent.com/91538155/180269388-8397333a-8592-484b-8bf6-7f3930c185a9.png)

And finally, to restart the movement, we need this if statement:

![image](https://user-images.githubusercontent.com/91538155/180269456-7a83ee57-f345-4329-bd26-0ea9a47b0cae.png)

This is all that is needed for the scripts


# 3) Assigning in Unity
The NpcMovement script has to be assigned to the NPC Objects, not the dialogue boxes. RangeToStop can be left as is

# That is all that is needed for the NPC code
