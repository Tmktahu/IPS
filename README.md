![](https://i.imgur.com/ESphKtR.png)

[![GPLv3 License](https://img.shields.io/static/v1?label=Licence&message=GPL%20v3&color=green)](https://opensource.org/licenses/) [![GitHub Release](https://img.shields.io/static/v1?label=Version&message=1.2.0&color=blue)]()

This is the repository for the Independant Positioning System (IPS), coded by Fryke#0746 on Discord.

IPS is a coordinate based positioning system for the game Starbase. This README will be updated with current features and statistics as the system is upgraded and added to.

For installation instructions, check out the information found in the [Current Release](https://github.com/Tmktahu/IPS/tree/main/CurrentRelease) folder.

If you are curious about how the code was derived and the logic behind it, feel free to check out the [How It Works](https://github.com/Tmktahu/IPS/wiki/How-It-Works) wiki page.

## Features and Requirements

- Requires 4 Receivers
- 1 Basic YOLOL Chip
- 0.6 second update time
- Ability to set a custom origin point
- Ability to re-label and invert axes
- Can run alongside ISAN v2.5
- Module support

### Current Modules

- Velocity
- Waypoint Course System

## Grid Alignment

By personal choice, I have made the default coordinate grid alignment match the following picture:

<img src="https://i.imgur.com/OyOJq4F.png" width="50%">

Where positive-X goes inside the belt, positive-Y goes to the left\* of the belt, and positive-Z goes above\* the belt.
<br>
*\* depending on your current orientation*

But, this can be changed by modifying how you label the coordinate variables. If you wish to label the axes differently, check out the information found in the [Current Release](https://github.com/Tmktahu/IPS/tree/main/CurrentRelease) folder down in the "Configuration Options" section.

## Want to help?

If you are interested in contributing to this project, feel free to look through the [Issues](https://github.com/Tmktahu/IPS/issues) to see what is currently being worked on. Any thoughts, comments, or PRs are much appreciated. If you have any questions or ideas, also feel free to reach out to Fryke#0746 on Discord. You can find me in the official [Starbase Discord](https://discord.com/invite/starbase).

## TODO

- Mono Receiver option
- Fancier display text
- Velocity display?
- Come up with ideas for modules
- Research the ability to replace the transmitter stations
