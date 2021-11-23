![](https://i.imgur.com/ESphKtR.png)

[![GPLv3 License](https://img.shields.io/static/v1?label=Licence&message=GPL%20v3&color=green)](https://opensource.org/licenses/) [![GitHub Release](https://img.shields.io/static/v1?label=Version&message=1.3.0&color=blue)]() [![Discord](https://img.shields.io/static/v1?label=Discord&message=Click%20to%20Join&color=purple)](https://discord.gg/Vafdx5JWBh)

This is the repository for the Independant Positioning System (IPS), coded by Fryke#0746 on Discord. Check out our [Discord Server](https://discord.gg/Vafdx5JWBh).

IPS is a coordinate based positioning system for the game Starbase. This README will be updated with current features and statistics as the system is upgraded and added to.

For installation instructions, check out the information found in the [Current Release](https://github.com/Tmktahu/IPS/tree/main/CurrentRelease) folder.

If you are curious about how the code was derived and the logic behind it, feel free to check out the [How IPS Works](https://github.com/Tmktahu/IPS/wiki/How-IPS-Works) wiki page.

If you're interested in a plug-and-play module, check out [Independant Positioning System - Asynchronous](https://github.com/Tmktahu/IPS/tree/main/IPSA).

And finally, I have had the fantastic oppertunity to work with other YOLOL developers to incorporate IPS into their systems. Check out more information on the [Collaborations](https://github.com/Tmktahu/IPS/blob/main/Collaborations.md) page.

## Features and Requirements

- Quad Receiver OR Mono Receiver Options
- 1 Basic YOLOL Chip
- 0.6 second update time
- Ability to set a custom origin point
- Ability to re-label and invert axes
- Can run alongside ISAN v2.5
- Add-On support

### Current Modules

- Velocity
- Waypoint Course System

## Grid Alignment

By personal choice, I have made the default coordinate grid alignment match the following picture:

<a href="https://github.com/Tmktahu/atlas" target="_blank"><img src="https://i.imgur.com/tMJ851Y.png" width="70%"></a>

- Positive +X goes inside the belt
- Positive +Y goes to the left of the belt, towards the West transmitter station
- Positive +Z goes above the belt, towards the North transmitter station

In addition the default origin point is the Warp Gate, which is aligned to what I am calling [The Sacred Grid](https://github.com/Tmktahu/IPS/wiki/The-Sacred-Grid).

But, this can be changed by modifying how you label the coordinate variables. If you wish to label the axes, invert the axes, or modify the origin point, check out the information found in the [Current Release](https://github.com/Tmktahu/IPS/tree/main/CurrentRelease) folder down in the "Configuration Options" section.

## Want to help?

If you are interested in contributing to this project, feel free to look through the [Issues](https://github.com/Tmktahu/IPS/issues) to see what is currently being worked on. Any thoughts, comments, or PRs are much appreciated. If you have any questions or ideas, feel free to join the [IPS/Atlas] Discord(https://discord.gg/Vafdx5JWBh).

## TODO

- Come up with ideas for Add-Ons
- Research the ability to replace the transmitter stations

## Special Thanks

- spedione#9006 for bug testing and taking measurements
- [Thaccus#0591](https://www.twitch.tv/thaccus) for redundant code optimization
- Azurethi#0789 for inspiration
