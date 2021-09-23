# Current Release

Here you will find information and files regarding the current stable release of IPS.

Currently IPS is version 1.2.

## Installation Instructions

### Setting up the Receivers

Currently, IPS v1.2 requires 4 recievers on your ship. They must all be wired into your ship's network as expected.

Each reciever has a number of fields on it. You must rename some of these fields for IPS to function correctly. Take note that a reciever is composed of 2 pieces: the turret base and the receiver itself. Make sure you are looking at the receiver itself when going to set these fields. The following table outlines the needed configuration. The spots marked with red ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+) are ones that must be set.

Default Field Names | Receiver #1 | Receiver #2 | Receiver #3 | Receiver #4
--------------------|-------------|-------------|-------------|-------------
Message | Message | Message | Message | Message | 
SignalStrength | ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+) A | ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+) B | ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+) C | ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+) D
![#c5f015](https://via.placeholder.com/15/c5f015/000000?text=+) ListenAngle | ListenAngle | ListenAngle | ListenAngle | ListenAngle | 
TargetMessage | ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+) AT | ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+) BT | ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+) CT | ![#f03c15](https://via.placeholder.com/15/f03c15/000000?text=+) DT
TargetFrequency | TargetFrequency | TargetFrequency | TargetFrequency | TargetFrequency | 
Frequency | Frequency | Frequency | Frequency | Frequency | 

In addition, you must change the ![#c5f015](https://via.placeholder.com/15/c5f015/000000?text=+) `ListenAngle` value from `45` to `180`.
See the below screenshot for an example of what a Receiver should be set to.

![https://i.imgur.com/IdbDVHI.png](https://i.imgur.com/IdbDVHI.png)

### Set up the Display

IPS v1.2 uses one Text Display. You may place this text display anywhere as long as it is attached to the network. You must change the `PanelValue` variable name to `o` as seen in the below screenshot.

![https://i.imgur.com/zl3ICVi.png](https://i.imgur.com/zl3ICVi.png)

### Pasting the Code like a Ninja

IPS v1.2 runs on a Basic Chip. Once you have one ready and waiting, you can find the code in the `IPS.yolol` file found in the same folder as this README file. You can also [click here](https://github.com/Tmktahu/IPS/blob/main/CurrentRelease/IPS.yolol) to go there.

Unfortunately, you will need to paste the code in line-by-line.

## Restarting IPS

If you do these things out of order or are jery rigging a system together, it is possible that IPS will freak out on you.

To restart the program you can go to the Text Display you set up and delete the **value** of the `o` variable (so delete the text being displayed). IPS should restart properly. If things are still broken, you can try removing and replacing the YOLOL Chip.

If everything hates you, feel free to reach out to Fryke#0746 on discord for debugging help.

## Configuration Options

### Changing the Origin Point

IPS v1.2 allows you to set a custom Origin Point `[0, 0, 0]` for the coordinate system. To do this, you will need to edit 3 variables in the code itself.

The target variables are on line 9:

- `a=??????` for the Origin X-Coordinate
- `b=??????` for the Origin Y-coordinate
- `c=??????` for the Origin Z-coordinate

But these variables come with default values. The default origin point is set to the center of the Warp Gate station.

In order to set a custom origin point, follow these steps:

1. Set all 3 Origin Coordinate variables to `0`.
2. Restart IPS.
3. Fly to the location you wish to use as the new Origin Point.
4. Write down your coordinates.
5. Place your recorded coordinates in the code on line 7.
6. Restart IPS by deleting the content of the text panel you are using for display.

### Changing the Axis Labels

You may wish to label the axis differently from the default scheme. You may even wish to invert them. This is not hard to do, but will require a little bit of code tweaking.

While mathematically the X-, Y-, and Z-axis will always be treated as such, you can rename, reorganize, and invert them on your text display.

The code that writes to your text display is by default:
`:o=fm+x/t*t+my+y/t*t+mz+z/t*t` found on line 12.

- `:o` this is the text panel variable that it will print to.
- `fm` this is a composed string that contains the `mx` string `"\nX: "` defined on line 1.
- `x` this is the final X coordinate.
- `/t*t` this divides and multiplies by 1000 to cut off the decimals.
- `my` this is the string `"\nY: "` defined on line 1.
- `y` this is the final Y coordinate.
- `mz` this is the string `"\nY: "` defined on line 1.
- `z` this is the final Z coordinate.

By changing the `mx`, `my`, and `mz` strings on line 1, you can re-label the various coordinates on your display.
To invert an axis, you may place a `-` on specific lines outlined below.

- Placing a `-` on line 11 right after the `x=` piece will invert the x-axis. For example, `x=-(ch*u-d*v+e*w)/m-a`
- Placing a `-` on line 11 right after the `y=` piece will invert the y-axis. For example, `y=-(f*u+j*w+k*v)/m-b`
- Placing a `-` on line 12 right after the `z=` piece will invert the x-axis. For example, `z=-(l*v-n*u+o*w)/m-c`

And by re-organizing any of the terms in the code you can adjust what coordinates are shown before others.

For example, if you wanted to mimic [ISAN's](https://github.com/Collective-SB/ISAN) coordinate grid for display purposes, you would use the following:
`:o=fm+y/t*t+my+z/t*t+mz+x/t*t`

Any changes should be followed by a restart of the system.
