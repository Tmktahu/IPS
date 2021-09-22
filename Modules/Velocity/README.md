# Waypoint Course Module

This module is specifically designed for calculating and storing the ship's velocity.

Current features include:

- 0.2 minimum second update time (note this is different than display update time).
- Speed storage for use in other places.
- Optional directional vector storage.

## Requirements

This module requires the following:

- 1 Advanced YOLOL Chip for the code.
- A modification to IPS that requires 3 memory slots for coordinates.
- 1 memory slot for Speed.
- 3 optional memory slots for the directional vector.

## Modifying IPS

This module requires a modification to IPS. You must implement the `Accessing the X, Y, and Z Coordinates` modification detailed [here](https://github.com/Tmktahu/IPS/tree/main/Modules).

If you wish to actually display the speed on the same text panel as the coordinates, then you must use the tweaked version of IPS found here in this folder, called `IPS_Speed_Display.yolol`.

## Installation and Configuration

This module will work as-is provided the IPS modifications and memory chip values are set up correctly.

You will need `x`, `y`, and `z` memory variables for the coordinates from IPS. You will also need a `s` memory variable for the speed.

Optionally, you may also store the calculated directional vector in memory. To do this, place `:` before the following variables in the code on line 2:

- `u` => `:u`, set up a memory variable `u`, used for the x-coordinate of the vector.
- `v` => `:v`, set up a memory variable `v`, used for the y-coordinate of the vector.
- `w` => `:w`, set up a memory variable `w`, used for the z-coordinate of the vector.

## A note on update times

This module mathematically updates the current velocity every 0.2 seconds. But the math is dependant on how often the coordinates update. So even though this runs every 0.2 seconds, it will only spit out new values every 0.6 seconds if you use the standard version of IPS.

In addition, this module does **not** handle display of the values. Display update time will also effect how often you get new values. For IPS, this is also 0.6 seconds.
