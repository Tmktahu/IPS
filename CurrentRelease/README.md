# Current Release

Here you will find information and files regarding the current stable release of IPS.

Currently IPS is version 1.0

## Installation Instructions

- Install 4 Receivers
- Configure Receivers (get screenshot)
- Set up display (get screenshot?)
- Get a Basic Chip
- Paste code like a ninja

## Configuration Options

IPS v1.0 allows you to set a custom Origin Point `[0 ,0 ,0]` for the coordinate system. To do this, you will need to edit 3 variables in the code itself.

The target variables are on line 6:
- `ox=??????` for the Origin X-Coordinate
- `oy=??????` for the Origin Y-coordinate
- `oz=??????` for the Origin Z-coordinate

But these variables come with default values. The default origin point is set to the middle of the Warp Gate station.

In order to set a custom origin point, follow these steps:
1. Set all 3 Origin Coordinate variables to `0`
2. Fly to the location you wish to use as the new Origin Point
3. Write down your coordinates
4. Place your recorded coordinates in the code on line 6
5. Restart IPS by deleting the content of the text panel you are using for display
