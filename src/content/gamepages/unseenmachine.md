---
---

# Unseen Machine

Unseen Machine is our first game. It is a cooperative stealth game where up to four players jump into the role of robot agents. The players are teleported into randomly generated dungeons where they have to evade enemies, steal everything in sight and escape unseen.

![Robot agent in action](/src/images/gamepages/UnseenMachine.png "Early concept art")

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
3. [Lobby](#lobby)
4. [Mission Generation and Design](#mission-generation-and-design)
5. [Game Mechanics](#game-mechanics)
6. [Player Character Design](#mission-generation-and-design)
7. [Enemy Design](#mission-generation-and-design)
8. [Visual Design](#mission-generation-and-design)
9. [Sound Design](#mission-generation-and-design)
10. [Networking](#mission-generation-and-design)

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

## Main Menu
## Lobby
After pressing the host or join button the player is brought into their own lobby or the lobby of the host they connected to, respectivly. The Lobby has is split into four areas:
- The spawning area
- The mission area
- The training area
- The social area
### Spawning Area
The spawning area consists of 4 personal pods, one for each player and the docks they connect. When a new player connects they will spawn in their personal pod.
### Mission Area
In the mission area the players can [customize their character](#character-customization) and [select and start missions](#mission-selection). In the middle of the area is the mission slection terminal, interacting with it opens the mission selection menu. Once a mission is selected all connected players have to move to the ready area. Once all players are in the ready area the mission starts. Before starting a mission the players can adjust their gear and appearance at the respective terminal.
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
This mix of generation techniques allows for...

### Tutorial Mission
### Randomly Generated Missions
For the mission generation Unseen Machine uses mix of designed assets and random generation. The generator differentiates between 
## Game Mechanics
### Movement
Unseen Engine offers a varity of movement mechanics to allow for quick, smooth traversel of the environment. Aside from regular first person movement mechanics 
### Interaction
### Visiblity
### Combat
## Player Character Design
## Enemy Design
## Visual Design
## Sound Design
## Networking
Unseen Machine relies on peer-to-peer networking. This eliminates the need for a server architecture. However players need to share a local network, or have the be conntected over a third party service such as [Steam's peer-to-peer networking](https://partner.steamgames.com/doc/features/multiplayer).

</details>

<details>
  <summary>Presentation</summary>
</details>