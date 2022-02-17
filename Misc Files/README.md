## Astrolabe v1.2 Usage Notes

### Left Panel

This is where the 4 primary receiver coordinates are displayed. The red buttons reset the relavent IPS instance and the white buttons change the raw format output to be copy-paste friendly.

### Center Panel

#### Cargo Lock Beam Sight

The top-left purple button is used to turn on the cargo lock beam aiming sight system. The vertical slider on the right is then used to adjust the sight.

In order to calibrate the sight, you want to adjust it so all cargo lock beams appear to be level with each other while while you are sitting in the pilot seat. Once calibrated, you aim the ship for measurements using the tip of the central cargo lock beam.

#### Displays

The IPS display is for the receiver directly behind the pilot seat. It is level with a standard endo's camera while they sit in the seat. This receiver is the starting point of the measured vector.

The `RawStrtPt` text panel holds the raw coordinate output of the IPS instance next to it.
The `AvgV` text panel holds the average directional vector calculated from the entire system.
The red button to the left of the IPS display resets the IPS instance when held.
The white button formats the text panels to be copy-paste friendly.
The green button normalizes the `AvgV` values.

The four lower text panels labeled `v21`, `v32`, `v43`, and `v41` hold the vector information between different receivers. For example, `v21` is the vector from receiver #2 to receiver #1.

#### Other Buttons

`Cruise` and `Turtle` are self-explanatory.

`Gen` automatically manages the generator. This should pretty much always be on.

`Precision` is a mode that allows you to better aim the ship with very very small movements. Useful when trying to aim at a celestial object.

### Right Panel

This panel currently contains thrust information, but is otherwise empty and available for any custom additios.

### Memory Chips

Underneath the center panel are 2 racks of memory chips. These memory chips hold information relavent to the entire system. Variables found in these chips are defined below.

#### Top-Left Memory Chip

Field | Description
------|------------|
OriginX | The origin X-coordinate for the whole system. IPS instances must be reset after changing this.
OriginY | The origin Y-coordinate for the whole system. IPS instances must be reset after changing this.
OriginZ | The origin Z-coordinate for the whole system. IPS instances must be reset after changing this.
x | The X-coordinate of receiver #5, the vector start point.
x | The Y-coordinate of receiver #5, the vector start point.
x | The Z-coordinate of receiver #5, the vector start point.
avgx | The X-component of the calculated average directional vector.
avgy | The Y-component of the calculated average directional vector.
avgz | The Z-component of the calculated average directional vector.
avgv | The entire calculated average directional vector as a string.

#### Middle-Left Memory Chip

Field | Description
------|------------|
x21 | The X-component of the 2=>1 directional vector.
y21 | The Y-component of the 2=>1 directional vector.
z21 | The Z-component of the 2=>1 directional vector.
v21 | The entire 2=>1 directional vector as a string.
--- | Unused.
--- | Unused.
x32 | The X-component of the 3=>2 directional vector.
y32 | The Y-component of the 3=>2 directional vector.
z32 | The Z-component of the 3=>2 directional vector.
v32 | The entire 3=>2 directional vector as a string.

#### Bottom-Left Memory Chip

Field | Description
------|------------|
x43 | The X-component of the 4=>3 directional vector.
y43 | The Y-component of the 4=>3 directional vector.
z43 | The Z-component of the 4=>3 directional vector.
v43 | The entire 4=>3 directional vector as a string.
--- | Unused.
--- | Unused.
x41 | The X-component of the 4=>1 directional vector.
y41 | The Y-component of the 4=>1 directional vector.
z41 | The Z-component of the 4=>1 directional vector.
v41 | The entire 4=>1 directional vector as a string.

#### Top-Right Memory Chip

Field | Description
------|------------|
s | Ship speed from Receiver #5.
u | The pre-rotation X-coordinate from Receiver #5.
v | The pre-rotation Y-coordinate from Receiver #5.
w | The pre-rotation Z-coordinate from Receiver #5.
m | Variable used in average vector calculation.
--- | Unused.
--- | Unused.
--- | Unused.
--- | Unused.
--- | Unused.

#### Middle-Right Memory Chip

Field | Description
------|------------|
nv | Receiver #5 North distance.
sv | Receiver #5 South distance.
ev | Receiver #5 East distance.
wv | Receiver #5 West distance.
rv1 | Receiver #1 distance values in copy-paste friendly string.
rv2 | Receiver #2 distance values in copy-paste friendly string.
rv3 | Receiver #3 distance values in copy-paste friendly string.
rv4 | Receiver #4 distance values in copy-paste friendly string.
rv5 | Receiver #5 distance values in copy-paste friendly string.
--- | Unused.

#### Bottom-Right Memory Chip

Currently unused.
