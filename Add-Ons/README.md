# Add-Ons and IPS Modifications

This section of the repository contains additional Add-Ons that are built to work with IPS. You can find instructions and details on each Add-Ons within its folder, but most of them require modifications to ISP to function. This README will cover different IPS modifications.

## Accessing the X, Y, and Z Coordinates

Many Add-Ons require access to the `[x, y, z]` coordinates that ISP generates. So we need to store these in memory slots.

Add-Ons that currently use this modification include:

- Waypoint Course Add-On

To do this, you must look at lines 10, 11, and 12 of IPS:

```
10: p=m-:d q=m-:a q*=q r=m-:c r*=r s=m-:b u=(p*p-q+g)/h v=(q-r+u*cn+ci)/cj
11: w=(r-s*s+u*ck+v*cl-cg)/cf x=(ch*u-d*v+e*w)/m-a y=(f*u+j*w+k*v)/m-b
12: z=(l*v-n*u+o*w)/m-c :o-- :o=fm+x/t*t+my+y/t*t+mz+z/t*t gotoi
```

You must replace this code with the following:

```
10: p=m-:d q=m-:a q*=q r=m-:c r*=r s=m-:b u=(p*p-q+g)/h v=(q-r+u*cn+ci)/cj
11: w=(r-s*s+u*ck+v*cl-cg)/cf :x=(ch*u-d*v+e*w)/m-a :y=(f*u+j*w+k*v)/m-b
12: :z=(l*v-n*u+o*w)/m-c :o-- :o=fm+:x/t*t+my+:y/t*t+mz+:z/t*t gotoi
```

Then we need to make sure there is a memory chip installed that has `x`, `y`, and `z` fields. From there, any external code or Add-On may access the current coordinates via `:x`, `:y`, and `:z`.
