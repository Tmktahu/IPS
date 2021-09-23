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

## Why separate velocity out into its own module?

I've decided to pull velocity calculations out into its own module for a couple reasons.

First off, it keeps me sane. Stuffing as much into base IPS as possible can be easier on users, but it makes things much more difficult to keep track of. It also requires me to code IPS in a way that allows it to function on both basic and advanced chips, which I opted to not do. Keeping the code seperate keeps requirements clear and things organized.

Secondly, I wanted the ability to try and make velocity and coordinates update as quickly as possible. Sticking it in IPS would require another line, bringing coordinate and velocity update time to 0.8 seconds. This is too long for some other modules I have in mind that require fast coordinate and velocity updates.

And lastly, line space in IPS is a tricky thing. I barely managed to get speed display squeezed in there, let alone the actual calculations and external variable storage. I wanted to not only calculate speed, but the directional vector as well. And I wanted to make those available to other modules if needed. Given how tight things are in IPS right now, putting velocity in a separate module was practically required.

## Notes on current implementation

Becuase our velocity updates every 0.4 seconds but our coordinates update every 0.6 seconds, timing on accessing the stored coordinates is offset. This results in odd situations where the velocity calculation is comparing 2 identical coordinates, which then 0s everything out. In addition, you also get noise from the coordinates themselves due to some odd script executing timing shenanigans.

So when I tried to just flat out calculate and display the velocity, it jumped around a lot between the actual velocty, a slightly larger velocty, ~2 times the actual velocity, and 0. Because of this, I sacrificed 0.2 seconds of update time to smooth the directional vector, which then smooths the speed.

Right now, we are using [basic exponential smoothing (Holt linear)](https://en.wikipedia.org/wiki/Exponential_smoothing%23Basic_%28simple%29_exponential_smoothing_%28Holt_linear%29) on line 3. This method uses a smoothing factor `f` defined on line 1, meant to have a value between 0 and 1. The smaller this number is, the smoother the value but the longer it takes to reach a real value. The larger it is, the less smoothing there is with no smoothing at 1.

There may be better methods of smoothing available, but this is the one I found that I could implement easily on 1 line. If you have any other smoothing algorithm suggestions, feel free to let me know.
