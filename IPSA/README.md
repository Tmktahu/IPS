![](https://i.imgur.com/bzVLS2a.png)

[![GPLv3 License](https://img.shields.io/static/v1?label=Licence&message=GPL%20v3&color=green)](https://opensource.org/licenses/) [![GitHub Release](https://img.shields.io/static/v1?label=Version&message=1.0.0&color=blue)]() ![](https://img.shields.io/static/v1?label=Blueprint&message=Available&color=blueviolet)

This is the folder for Independant Positioning System - Asynchronous (IPS-A), coded by Fryke#0746 on Discord.

IPSA is a plug-and-play Quad 7-chip IPS module for the game Starbase meant to calculate and provide information about position and velocity. This README will be updated with current features and statistics as the system is upgraded and added to.

## Features

- A compact module blueprint that can be installed on any ship.
- 0.2 second update time.
- Coordinate and velocity information.
- A plug-and-play system that only requires a single connection.
- ~1300 Ship Strength Rating for framed blueprints.
- Isolated internal network to keep uneeded globals out of the ship network.
- Customizable output variables.

## IPSA vs IPSA Queued

There are two versions of IPSA available, each with their own benefits.

| IPSA | IPSA Queued |
|------|-------------|
| ![#c5f015](https://via.placeholder.com/15/c5f015/000000?text=+) 0.2s Update Rate | ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+) 0.4s Update Rate |
| ![#c5f015](https://via.placeholder.com/15/c5f015/000000?text=+) Slightly smaller at 96x120x168cm (width/height/depth) | ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+) Slightly larger at 96x120x192cm (width/height/depth) |
| ![#c5f015](https://via.placeholder.com/15/c5f015/000000?text=+) Less Expensive | ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+) More Expensive (+2 memory relays, +2 memory chips, +2 advanced chips) |
| ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+) Less accurate velocity calculations | ![#c5f015](https://via.placeholder.com/15/c5f015/000000?text=+) More accurate velocity calculations |
| Better for Coordinates | Better for Velocity |

If you are a standard user, normal IPSA should fit your needs unless the 0.2s slow down is worth a more accurate speed display to you.

If you are a developer or are planning on interacting with IPSA for other velocity-based calculations, then I recommend you use IPSA Queued.

## Requirements and Installation

 You will need 4 Receivers configured in the same manner as 1-chip IPS. You can find receiver setup instructions in the [Current Release](https://github.com/Tmktahu/IPS/tree/main/CurrentRelease) folder.

Included in the Blueprints folder are four blueprints.

- `IPSA.fbe` is the standard plug-and-play module. You can find the blueprint statistics below.
- `IPSA_No_Frame.fbe` is the same module, but with the plates and beams stripped out for minimalist installations.
- `IPSA_Queued.fbe` is the Queued version of IPSA.
- `IPSA_Queued_No_Frame.fbe` is the Queued version of IPSA without plates or beams.

Once the receivers and text panel are ready, go ahead and plug the box into the system by the provided connector/socket. Note that this system must be specifically connected at certain locations to operate correctly. See the diagram of the inner workings further below to see where the correct connections are.

## Blueprint Information

Below are screenshots and tables of information regarding the blueprints and how the system is set up. If you want to read more about how IPSA is setup and how it functions, check out the [How IPSA Works](https://github.com/Tmktahu/IPS/wiki/How-IPSA-Works) wiki page.

The following variables are provided globally to the ship's network. If you want to change the name of these variables, you can tweak them on the `External Output Memory Chip` seen in the IPSA Chip and Layout Diagram further down this page.

Field Names | Field Value
------------|------------
x | Final X Coordinate
y | Final Y Coordinate
z | Final Z Coordinate
is | Calculated Speed
vx | Normalized Velocity X Component
vy | Normalized Velocity Y Component
vz | Normalized Velocity Z Component
vxr | Raw Velocity X Component
vyr | Raw Velocity Y Component
vzr | Raw Velocity Z Component

`IPSA.fbe` and `IPSA_Queued_No_Frame` Blueprints

<img src="https://i.imgur.com/ayXXeOW.png" width="60%">

`IPSA.fbe` Material Cost

<img src="https://i.imgur.com/62jZOBh.png" width="40%">

`IPSA.fbe` Full Part List

<img src="https://i.imgur.com/9eoMs8u.png" width="50%">

`IPSA.fbe` Building Budget

<img src="https://i.imgur.com/ozCSn2y.png" width="30%">

IPSA Chip and Layout Diagram

![IPSA Chip and Layout Diagram](https://i.imgur.com/6zciqzF.png)

## Want to help?

If you are interested in contributing to this project, feel free to look through the [Issues](https://github.com/Tmktahu/IPS/issues) to see what is currently being worked on. Any thoughts, comments, or PRs are much appreciated. If you have any questions or ideas, also feel free to reach out to Fryke#0746 on Discord. You can find me in the official [Starbase Discord](https://discord.com/invite/starbase).

## Special Thanks

- Aersaud#2007 for a ton of development help, bug squashing, and testing
- spedione#9006 for testing
- [Thaccus#0591](https://www.twitch.tv/thaccus) for testing and bug squashing

