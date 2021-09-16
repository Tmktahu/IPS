# Waypoint Course Module

This module was originally created to facilitate races by allowing players to define a race track with a set of coordinate waypoints. As you fly from waypoint to waypoint in order the system tracks your progress, providing you with information as you go.

Current features include:

- Up to 15 waypoints in a course
- Display how far you are from the next waypoint
- Display what waypoint you are currently on
- 0/1 boolean state for each waypoint reached

## Requirements

This module requires the following:
- 1 Advanced YOLOL Chip for the code
- A modification to IPS which requires 3 memory slots for the current coordinates
- 1 memory slot for the distance to the current waypoint
- 1 memory slot OR 1 button for each waypoint tracking boolean
- 3 memory slots for each waypoint

## Preparing the Code

Since this module is meant to guide a pilot along a course of waypoints, there is some setup involved.
I first want to walk you through the different parts of the code.

```
1:  :w="\n==Waypoint\n==Course\n==Preparing" // Coded by Fryke#0746
2:  :w0=0 :w1=0 :w2=0 :w3=0 :w4=0 :w5=0 :w6=0 :w7=0 :w8=0 :w9=0 :w10=0
3:  :w11=0 :w12=0 :w13=0 :w14=0 cw=0 t=100 xw=:xw0 yw=:yw0 zw=:zw0
4:  :w="\n==Waypoint\n==Course\n==Running\nCurrent: "+cv
5:  :h=sqrt((:xr-xw)^2+(:yr-yw)^2+(:zr-zw)^2) goto(5+((:h<t)*(cw+1)))*:rst
6:  :w0=1 xw=:xw1 yw=:yw1 zw=:zw1 :w-=cw cw++ :w+=cw goto 5
7:  :w1=1 xw=:xw2 yw=:yw2 zw=:zw2 :w-=cw cw++ :w+=cw goto 5
8:  :w2=1 xw=:xw3 yw=:yw3 zw=:zw3 :w-=cw cw++ :w+=cw goto 5
9:  :w3=1 xw=:xw4 yw=:yw4 zw=:zw4 :w-=cw cw++ :w+=cw goto 5
10: :w4=1 xw=:xw5 yw=:yw5 zw=:zw5 :w-=cw cw++ :w+=cw goto 5
11: :w5=1 xw=:xw6 yw=:yw6 zw=:zw6 :w-=cw cw++ :w+=cw goto 5 
12: :w6=1 xw=:xw7 yw=:yw7 zw=:zw7 :w-=cw cw++ :w+=cw goto 5
13: :w7=1 xw=:xw8 yw=:yw8 zw=:zw8 :w-=cw cw++ :w+=cw goto 5
14: :w8=1 xw=:xw9 yw=:yw9 zw=:zw9 :w-=cw cw++ :w+=cw goto 5
15: :w9=1 xw=:xw10 yw=:yw10 zw=:zw10 :w-=cw cw++ :w+=cw goto 5
16: :w10=1 xw=:xw11 yw=:yw11 zw=:zw11 :w-=cw cw++ :w+=cw goto 5
17: :w11=1 xw=:xw12 yw=:yw12 zw=:zw12 :w-=cw cw++ :w+=cw goto 5
18: :w12=1 xw=:xw13 yw=:yw13 zw=:zw13 :w-=cw cw++ :w+=cw goto 5
19: :w13=1 xw=:xw14 yw=:yw14 zw=:zw14 :w-=cw cw++ :w+=cw goto 5
20: :w14=1 :w="\n=You have\n=finished\n=the course!" goto 20*:rst
```

- Lines 1-4 are setup. They reset all waypoint tracking booleans `:w#`, grab the first waypoint `[xw0, yw0, zw0]`, and define the distances tolerance `t`.
- Line 5 is the distance checking math. This line runs every 0.2 seconds once the system is going.
- Lines 6-19 are used to flip between different waypoints.
- Line 20 is the final line that ends the program.

The first step is deciding on how many waypoints the course will have. For our purposes, we will have 3 waypoints. So we need to delete lines from the 6-19 chunk to match how many waypoints we want.

```
1:  :w="\n==Waypoint\n==Course\n==Preparing" // Coded by Fryke#0746
2:  :w0=0 :w1=0 :w2=0 :w3=0 :w4=0 :w5=0 :w6=0 :w7=0 :w8=0 :w9=0 :w10=0
3:  :w11=0 :w12=0 :w13=0 :w14=0 cw=0 t=100 xw=:xw0 yw=:yw0 zw=:zw0
4:  :w="\n==Waypoint\n==Course\n==Running\nCurrent: "+cv
5:  :h=sqrt((:xr-xw)^2+(:yr-yw)^2+(:zr-zw)^2) goto(5+((:h<t)*(cw+1)))*:rst
6:  :w0=1 xw=:xw1 yw=:yw1 zw=:zw1 :w-=cw cw++ :w+=cw goto 5
7:  :w1=1 xw=:xw2 yw=:yw2 zw=:zw2 :w-=cw cw++ :w+=cw goto 5
8:  :w14=1 :w="\n=You have\n=finished\n=the course!" goto 20*:rst
```

Remember that the first waypoint is grabbed on line 3 `[xw0, yw0, zw0]`. So our first waypoint is `0`, second waypoint is `1`, and third waypoint is `2`.

The next step is to modify line 8. We need to change `:w14=1` to match our last waypoint and the `goto 20*:rst` to match the line we are on. So our code becomes:

```
1:  :w="\n==Waypoint\n==Course\n==Preparing" // Coded by Fryke#0746
2:  :w0=0 :w1=0 :w2=0 :w3=0 :w4=0 :w5=0 :w6=0 :w7=0 :w8=0 :w9=0 :w10=0
3:  :w11=0 :w12=0 :w13=0 :w14=0 cw=0 t=100 xw=:xw0 yw=:yw0 zw=:zw0
4:  :w="\n==Waypoint\n==Course\n==Running\nCurrent: "+cv
5:  :h=sqrt((:xr-xw)^2+(:yr-yw)^2+(:zr-zw)^2) goto(5+((:h<t)*(cw+1)))*:rst
6:  :w0=1 xw=:xw1 yw=:yw1 zw=:zw1 :w-=cw cw++ :w+=cw goto 5
7:  :w1=1 xw=:xw2 yw=:yw2 zw=:zw2 :w-=cw cw++ :w+=cw goto 5
8:  :w2=1 :w="\n=You have\n=finished\n=the course!" goto 8*:rst
```

Next, we want to delete all the `:w#=0` on lines 2 and 3 that we don't need. Since we are only going to up 2, the code becomes:

```
1:  :w="\n==Waypoint\n==Course\n==Preparing" // Coded by Fryke#0746
2:  :w0=0 :w1=0 :w2=0
3:  cw=0 t=100 xw=:xw0 yw=:yw0 zw=:zw0
4:  :w="\n==Waypoint\n==Course\n==Running\nCurrent: "+cv
5:  :h=sqrt((:xr-xw)^2+(:yr-yw)^2+(:zr-zw)^2) goto(5+((:h<t)*(cw+1)))*:rst
6:  :w0=1 xw=:xw1 yw=:yw1 zw=:zw1 :w-=cw cw++ :w+=cw goto 5
7:  :w1=1 xw=:xw2 yw=:yw2 zw=:zw2 :w-=cw cw++ :w+=cw goto 5
8:  :w2=1 :w="\n=You have\n=finished\n=the course!" goto 8*:rst
```

And finally, we need to decide on a distance tolerance in meters. This is the variable `t` on line 3. The ship must come within this distance of a waypoint for it to be checked off. By default, this is 100.

With that done, the code is ready. Next up we need to prepare the memory chips.

## Preparing the Memory Chips

### Distance to Next Waypoint
On line 5, we have the `:h` variable. This is the distance from the ship to the next waypoint. If you don't want to display this information, you can make it a local variable by removing the `:`, so the line becomes `h=sqrt((:xr-xw)^2+(:yr-yw)^2+(:zr-zw)^2) goto(5+((h<t)*(cw+1)))*:rst`.

If you do want to display this information, then you need a memory slot for it. Go into your memory chip and rename one of the slots to `h`. Then use the `h` variable on a display of your choice, or `:h` in other code.

For our case, we will store it in memory.

### Waypoint Booleans

Each waypoint has a `:w#` 0/1 boolean variable that stores whether or not the waypoint has been reached. You can store these in memory, or you can store them on buttons. I found using tiny simple buttons worked well because they click in and light up as you traverse the course. But you can also just story them in memory if you want.

For our purposes, we will store them on buttons. So these take up no memory.

### Waypoint Coordinates

Each waypoint requires you to store the `x`, `y`, and `z` coordinate in the format `[xw0, yw0, zw0]`, `[xw1, yw1, zw1]` ... `[xw#, yw#, zw#]` where `#` is the waypoint number. Currently, you must enter the values for these variables manually. But in the future I will write a companion script that allows you to set these with the click of a button.

Since each waypoint coordinate requires 3 memory slots, we will be using 9 memory slots for our example.

It is **_critical to note_** that the coordinates you record are **_dependant on your custom origin point_**. Other pilots that want to use your course must use the same origin point you used to create the waypoints.

### The Memory Chip

For our example, we have:
- 1 memory slot for distance
- 9 memory slots for coordinates
- 0 memory slots for booleans because we are using buttons for those

So we can fit everything on one memory chip. Though, remember that the modification to IPS requires 3 memory slots as well, so overall we will need 2 memory chips. Note that the coordinates we use here are testing coordinates around Origin 6. The Custom Origin Point used to get these coordinates is `[0, 0, 0]`.

The chips will be set up as follows:
| Field Name | Field Value |
| ---------- | ----------- |
| xw0 | 19938 |
| yw0 | 106166 |
| zw0 | -15292 |
| xw1 | 20302 |
| yw1 | 105374 |
| zw1 | -15611 |
| xw2 | 19635 |
| yw2 | 104012 |
| zw2 | -14849 |
| h | 0 |

## Setting up the Controls

For controls, we have:
- 1 `w` text panel for system output. 
- 1 `rst` reset hybrid button that is used to reset the system.
- 1 `h` progress bar we will use to display the distance.
- 3 `w0`, `w1`, `w2` small buttons we use for the waypoint booleans.

For the reset hybrid button, we want it to be set up like this:
| Field Name | Field Value |
| ---------- | ----------- |
| rst | 1 | 
| ButtonOnStateValue | 0 |
| ButtonOffStateValue | 1 |
| ButtonStyle | 0 |

For the progress bar, we will use a `PanelMaxValue` of 2000 for our example, but this can be whatever you want.

And for the small buttons, we set them up like this, where `w#` is `w0`, `w1`, `w2` for the different buttons:
| Field Name | Field Value |
| ---------- | ----------- |
| w# | 1 | 
| ButtonStyle | 0 |

## Running the System

Now that the code is ready, the memory chips are in place, and the controls are prepared, we are goog to go. Paste the code into an Advanced Chip and hit the Reset button to reboot the system.

As you fly from waypoint to waypoint, the boolean variabls and distances will update for each consecutive waypoint. Once the course is finished, the system will sit there until you hit the reset button.
