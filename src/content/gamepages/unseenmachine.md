---
---

# Unseen Machine

Unseen Machine is our first game. It is a cooperative stealth game where up to four players jump into the role of robot agents. The players are teleported into randomly generated dungeons where they have to evade enemies, steal everything in sight and escape unseen.

![Robot agent in action](@images/gamepages/UnseenMachine.png "Early concept art")

<details>
  <summary>Game Design Document</summary>

# Game Design Document

## Table of Contents

1. [Overview](#overview)<br>
1.1. [Look and Feel](#look-and-feel)<br>
1.2. [Gameplay loop](#gameplay-loop)<br>
1.3. [Playtime](#playtime)<br>
1.4. [Meta Progression](#meta-progression)<br>
1.5. [Prototype](#prototype)
2. [Main Menu](#main-menu)
3. [Lobby](#lobby)<br>
3.1. [Spawning Area](#spawning-area)<br>
3.2. [Mission Area](#mission-area)<br>
3.3. [Training Area](#training-area)<br>
3.4. [Social Area](#social-area)<br>
4. [Mission Generation and Design](#mission-generation-and-design)
5. [Game Mechanics](#game-mechanics)<br>
5.1. [Movement](#movement)<br>
5.2. [Interaction](#interaction)<br>
5.3. [Visibility](#visiblity)<br>
5.4. [Combat](#combat)<br>
5.5. [Abilities](#abilities)<br>
6. [Player Character Design](#player-character-design)
7. [Enemy Design](#enemy-design)<br>
7.1. [Robob](#robob)<br>
7.2. [MouseBot](#mousebot)<br>
7.3. [SpringBot](#springbot)<br>
7.4. [Motherscuttler](#motherscuttler)<br>
7.5. [Scuttler](#scuttler)<br>
7.6. [MoweBot](#mowebot)<br>
7.7. [BigBot](#bigbot)<br>
7.8. [SloBot](#slobot)<br>
7.9. [TurBot](#turbot)<br>
8. [Visual Design](#visual-design)
9. [Sound Design](#sound-design)
10. [Networking](#networking)

## Disclaimer
The player will be referred to as 'they' throughout this document, regardless of gender identity.

## Overview
Unseen Machine is a cooperative stealth-action game in which up to four players jump into the role of robotic burglars. Their goal is to explore randomly generated dungeons, extract valuable artifacts and escape unseen. On the way to the objective the players must avoid robotic guards and steal everything that isn't nailed to the walls.

Unseen Machine focuses on fast paced gameplay, placing high speed evasive movement over slow and methodic sneaking. Each player can customize their robot with different looks and abilities to overcome gameplay challanges in different ways.

### Look and Feel
Unseen Machine is set in a retro-futuristic setting, combining clean scifi astethics with crt-monitors and cassette tapes.

The player sees this world from a first person perspective, for immersive and tense gameplay.

### Gameplay loop
The player starts out in their lobby. The lobby, allows other players to join the hosts session. 

### Playtime
Since each level is randomly generated Unseen Machine offers a great degree of replayability. The player will spend between 5 to 20 minutes for one mission, depending on the generated mission's size and complexity. To keep the player engaged and offer a longtime motivation, the player will experience [Meta Progression](#meta-progression) in-between the actual missions. Ideally this will make the player come back to the game regularly to unlock and play new content.

### Meta Progression
Completing a mission will reward the player with currency, depending on the mission difficulity and the score reached. The player can then spend the currency in the base for permanent unlocks. The player can unlock new gameplay features and visuals for their character.

### Prototype
In the prototype the player will be able to host or join a game lobby from the main menu. Once in the lobby the player will be able to start a randomly generated mission. The mission will feature one main- and one side-mission-objective, as well as enemies. The player will be able to complete these missions and be extracted in the extraction area back to the lobby. There the player will be rewarded with currency. Meta progression will not yet be featured in the prototype, since focus is on the core gameplay loop.
## Main Menu
## Lobby
After pressing the host or join button the player is brought into their own lobby or the lobby of the host they connected to, respectivly. The Lobby has is split into four areas:
- The spawning area
- The mission area
- The training area
- The social area
![Early ship concept art](@images/base/ship.png)
### Spawning Area
The spawning area consists of 4 personal pods, one for each player and the docks they connect. When a new player connects they will spawn in their personal pod.
### Mission Area
In the mission area the players can [customize their character](#character-customization) and [select and start missions](#mission-selection). In the middle of the area is the mission slection terminal, interacting with it opens the mission selection menu. Once a mission is selected all connected players have to move to the ready area. Once all players are in the ready area the mission starts. Before starting a mission the players can adjust their gear and appearance at the respective terminal.
![Early bridge concept art](@images/base/bridge.png)
#### Mission Selection
Interacting with the mission selection terminal opens the mission selection menu. Every 30 minutes the mission selection menu generates a set of randomly generated missions. The missions are displayed with information about their complexity and size. Aside from these missions the player can always choose to play the tutorial mission.
#### Mission Ready
Once a player selects a mission the ready area opens up. Once all players are inside the ready area the lobby area is unloaded and the mission assets are generated.
#### Gear Terminal
At the gear area the player can choose different ablilities
#### Appearance Terminal
At the appearance terminal the player can choose different skins and paint jobs for their robot.
### Interacting with other Players

### Training and Social Area
The training and social area are optional areas of the lobby the players can use to try out their gear, spend time waiting for other players to join or to relax inbetween missions. The training area has a practice dummy and parkour elements. The social area has a jukebox that allows players to listen to the games soundtrack.
## Mission Generation and Design
To generate the missions Unseen Machine uses a complex mix of prodecural generation techiques. The generator differentiates between rooms and corridors. Rooms are predesigned assets with random elements. The generator creates a set of random rooms, including necessary rooms, such as the spawn, the extraction zone and the room(s) required for the mission objective. These rooms are then randomly distributed in 3d space. The generator then executes the following steps to ensure that all rooms are connected to each other, directly or indirectly.
- Delauney Triangulation: The generator creates an edge between all rooms, so that all connections form triangles that have no other rooms withhin the triangle.
- Min-Spanning Tree: The generator chooses a subset of the Delauney edges, so that all rooms are connected with a minimal amount of edges.
- Adding back random edges: The generator adds back random edges to create secondary connections.
- Corridor connection: The generator uses a grid and a modified A-Star algorithm to assign corridor attributes to the grid's elements.
- Corridor generation: Depending on it's attributes and neighbours each corridor element then generates the required walls, floor, stairs, etc.
Then each room is randomized to a degree. Each room has elements that are randomly choosen based on a given set of allowed elements.
This mix of generation techniques allows for unique but coherent levels. 
### Tutorial Mission
The tutorial mission is not randomly generated but offers different challanges that allow the player to test out all of the games mechanics in a controlled environment.
## Game Mechanics
### Movement
Unseen Engine offers a varity of movement mechanics to allow for quick, smooth traversel of the environment. the game uses regular first person movement mechanics, allowing the player to walk, sprint, crouch, slide, jump, wallslide and walljump.
#### sprinting
Holding down the shift-key on the keyboard increases the speed the player moves at.
#### crouching
Holding down the c-key the player enteres a crouched state. While crouched the players size, [visibility](#visiblity) and speed are reduced. Releasing the c-key returns the player from the crouched state as soon as the player has enough vertical room to stand up.
#### sliding
If the player enters the crouch state while sprinting, they start sliding. While sliding the player moves at increased speed at a loss of steerability. The players speed decreases steadily until the player is at crouching speed, at which point the player starts to crouch normally. While sliding the players' [visibility](#visiblity) is decreased.
#### jumping
Using the space bar the player jumps into the air. The player can press the space bar again to perform a double jump. The player then has to touch the floor or perform a [wallslide](#wallslide) in order to regain the ability to jump.
#### wallslide
If a jump ends touching a wall, the player slowly slides down the wall.
#### walljump
If the player presses space while wallsliding they jump of the wall.
### Interaction
Looking at an interactable object, the player can press the interaction-button. If the player is close enough to the object the interaction is executed. Examples for interactions are:
- Flipping light switches
- Collecting coins
- Opening doors
- Starting the mission objective
### Visiblity
When the player is in the sightcone of an enemy, their detectionmeter slowly fills up, until the enemy actually sees the player. How quickly the player is detected depends on their visibility. The higher their visibility the faster they are detected. Factors, like how illuminated the players' body is and if they are crouching affects how high their visibility is. How quickly and closely the player moves around enemies also affects their detection.
### Combat
Combat is best avioded, but when there's no other choice the player can defend themselves with meele and ranged attacks.
![Action Poses](@images/player/action_poses.png "Action Poses")
### Abilities
## Player Character Design
It's a robot lady
Very cool

<img src="/src/images/player/concept.png" alt="Robob concept art" width="79.5%" style="display:inline-block;" />
<img src="/src/images/player/main_character.png" alt="Robob concept art" width="19.5%" style="display:inline-block;" />

The arms are very important since they are almost always visible in the first person view.

<img src="/src/images/player/arms.png" alt="Robob concept art" width="45%" style="display:inline-block;" />
<img src="/src/images/player/arms_render.png" alt="Robob concept art" width="54%" style="display:inline-block;" />

## Enemy Design
### Robob
Robob is the standard enemy. What Robob lacks in special abilities it makes up in numbers. Seriously these guys are everywhere.

<img src="/src/images/robots/robob.png" alt="Robob concept art" width="29%" style="display:inline-block;" />
<img src="/src/images/robots/robob_render_front_2.png" alt="Robob Blender render" width="45%" style="display:inline-block;" />
<img src="/src/images/robots/robob_game_crop.png" alt="Robob Godot concept" width="24%" style="display:inline-block;" />

On the left is the concept art for Robob, in the middle a render taken in Blender and on the right an example image of how the model would look in the game, rendered in the Godot engine.

### MouseBot
MouseBot is fast, hard to spot and has only one thing on its mind: KILL! When MouseBot spots an enemy it races towards it beeping loudly. Once it reaches its destination it explodes, dealing massive damage to everything around it. Luckily it can be defused with a single well place shot.
![MouseBot](@images/robots/mousebot.png "MouseBot concept art")
### SpringBot
SpringBots have a laser focus, they chase down anything suspicous they see. They kick first and never ask questions due to a lack of a voice module.
![SpringBot](@images/robots/springbot.png "SpringBot concept art")
### Motherscuttler
The mother of all scuttlers. These bots move around slowly, releasing [Scuttlers](#scuttler) periodically to scout for them. While slow, Motherscuttlers have powerful ranged attacks.
![Motherscuttler](@images/robots/motherscuttler.png "Motherscuttler concept art")
### Scuttler
While one scuttler is harmless on its own, they always come in numbers. Scuttlers run around in the vicinity of their [Motherscuttler](#motherscuttler), latching onto the player and slowing them down so that the Motherscuttler can shoot them easier. One Scuttler can be dispatched easily but new ones keep coming until their source is destoryed.
![Scuttler](@images/robots/scuttler.png "Scuttler concept art")
### MoweBot
MoweBots move around the halls quickly. Their big frontal flashlight makes them a threat to every player hiding in the shadows.
![MoweBot](@images/robots/mowebot.png "MoweBot concept art")
### BigBot
BigBots are a real challenge even for the biggest weapons. However they are slow and loud, making them easy to avoid.
If BigBots manage to close the gap they pack a punch and can destroy the player quickly.

<img src="/src/images/robots/bigbot2.png" alt="BigBot concept art" width="49%" style="display:inline-block;" />
<img src="/src/images/robots/bigbot.png" alt="BigBot concept art" width="49%" style="display:inline-block;" />

### SloBot
SloBots are slow and harmless on their own, however they scan their surroundings in a 360 degree perimeter making them hard to get around. Once they spot the player they blair the alarm, notifying all nearby bots of the players position.
![SloBot](@images/robots/slobot.png "SloBot concept art")
### TurBot
TurBots are rare but dangerous. Their long arms allow them to move along all surfaces, making them able to hide in corners and attack from unusual angles. If they are unable to suprise the player they run away, hide and wait for another opportunity for a suprise attack.

<img src="/src/images/robots/turbot.png" alt="TurBot concept art" width="49%" style="display:inline-block;" />
<img src="/src/images/robots/turbot2.png" alt="TurBot concept art" width="49%" style="display:inline-block;" />

## Visual Design
Visually Unseen Machine is stronly inspired by retro-futuristic aesthetics. They can also be described as cassette-future, a future as it was often envisioned in 70s and 80s movies, like Alien (1979). Unseen machine blends these visuals with cartoon shaders and mid-poly topology to achive a unique and easy to read look. Many of the objects in the world also fit into the time period, featuring crts, cassettes, floppy disks and nonsense-machines like big table mounted monitors that display the newspaper. 

An outline shader is used to allow the player to see in total darkness.
## Sound Design
3D sound is important to the player to get an idea of their sorroundings beyond of what they can see.
## Networking
Unseen Machine relies on peer-to-peer networking. This eliminates the need for a server architecture. However players need to share a local network, or have the be conntected over a third party service such as [Steam's peer-to-peer networking](https://partner.steamgames.com/doc/features/multiplayer).

</details>

<details>
  <summary>Presentation</summary>
</details>