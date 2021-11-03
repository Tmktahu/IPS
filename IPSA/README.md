![](https://i.imgur.com/bzVLS2a.png)

[![GPLv3 License](https://img.shields.io/static/v1?label=Licence&message=GPL%20v3&color=green)](https://opensource.org/licenses/) [![GitHub Release](https://img.shields.io/static/v1?label=Version&message=1.0.0&color=blue)]() ![](https://img.shields.io/static/v1?label=Blueprint&message=Available&color=blueviolet)

This is the folder for Independant Positioning System - Asynchronous (IPS-A), coded by Fryke#0746 on Discord.

IPSA is a plug-and-play Quad 7-chip IPS module for the game Starbase meant to calculate and provide information about position and velocity. This README will be updated with current features and statistics as the system is upgraded and added to.

## Features

- A compact module blueprint that can be installed on any ship.
- 0.2 second update time.
- Coordinate and velocity information.
- Add-On support for future projects.

## IPSA vs IPSA Queued

There are two version of IPSA available, each with their own benefits.

| IPSA | IPSA Queued |
|------|-------------|
| <span color="green">0.2s Update Rate</span> | <span color="red">0.4s Update Rate</span> |
| <span color="green">Slightly smaller at 96x120x148cm (width/height/depth)</span> | <span color="red">Slightly larger at 96x120x148cm (width/height/depth)</span> |
| <span color="green">Less Expensive</span> | <span color="red">More Expensive (+2 memory relays, +2 memory chips, +2 advanced chips)</span> |
| <span color="red">Less accurate velocity calculations</span> | <span color="green">More accurate velocity calculations</span> |

If you are a standard user, normal IPSA should fit your needs unless the 0.2s slow down is worth a more accurate speed display to you.

If you are a developer or are planning on interacting with IPSA for other velocity-based calculations, then I reccomend you use IPSA Queued.

## Requirements and Installation

 You will need 4 Receivers configured in the same manner as 1-chip IPS. You can find receiver setup instructions in the [Current Release](https://github.com/Tmktahu/IPS/tree/main/CurrentRelease) folder.

Included in this folder are two blueprints.

- `IPSA.fbe` is the standard plug-and-play module. You can find the blueprint statistics below.
- `IPSA_No_Frame.fbe` is the same module, but with the plates and beams stripped out for minimalist installations.

## Blueprint Information

Below are screenshots of information regarding the blueprints and how the system is set up.

If you want to read more about how IPSA is setup and how it functions, check out the [How IPSA Works](https://github.com/Tmktahu/IPS/wiki/How-IPSA-Works) wiki page.

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

- spedione#9006 for testing
- [Thaccus#0591](https://www.twitch.tv/thaccus) for testing and bug squashing
- Aersaud#2007 for testing, bug squashing, and development help
