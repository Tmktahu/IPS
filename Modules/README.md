# Modules and IPS Modifications

This section of the repository contains additional modules that are built to work with IPS. You can find instructions and details on each module within its folder, but most of them require modifications to ISP to function. This README will cover different IPS modifications.

## Accessing the X, Y, and Z Coordinates

Many modules require access to the `[x, y, z]` coordinates that ISP generates. So we need to store these in memory slots.

Modules that currently use this modification include:

- Waypoint Course Module

To do this, you must look at lines 8, 9, and 10 of IPS:

```
8:  w=s-:d z=(v-w*w+x*cf+y*cg-k)/j xa=(l*y-m*x)/s xr=(n*xa+o*z)/s
9:  za=(n*z-o*xa)/s ya=(-l*x-m*y)/s yr=(p*za-q*ya)/s zr=(-p*ya-q*za)/s
10: xr-=ox yr-=oy zr-=oz :o-- :o=a+xr/r*r+b+yr/r*r+c+zr/r*r goto7
```

The variables we need to tweak are `xr`, `yr`, and `zr`. We must place a `:` before each of these. So the code becomes:

```
8:  w=s-:d z=(v-w*w+x*cf+y*cg-k)/j xa=(l*y-m*x)/s :xr=(n*xa+o*z)/s
9:  za=(n*z-o*xa)/s ya=(-l*x-m*y)/s :yr=(p*za-q*ya)/s :zr=(-p*ya-q*za)/s
10: :xr-=ox :yr-=oy :zr-=oz :o-- :o=a+:xr/r*r+b+:yr/r*r+c+:zr/r*r goto7
```

Then we need to make sure there is a memory chip installed that has `xr`, `yr`, and `zr` fields. From there, any external code or module may access the current coordinates via `:xr`, `:yr`, and `:zr`.
