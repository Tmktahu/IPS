# Add-Ons and IPS Modifications

This section of the repository contains additional Add-Ons that are built to work with IPS. You can find instructions and details on each Add-Ons within its folder, but most of them require modifications to ISP to function. This README will cover different IPS modifications.

## Accessing the X, Y, and Z Coordinates

Many Add-Ons require access to the `[x, y, z]` coordinates that ISP generates. So we need to store these in memory slots.

Add-Ons that currently use this modification include:

- Waypoint Course Add-On

To do this, you must look at lines 8, 9, and 10 of IPS:

```
8:  p=m-:d q=m-:a q*=q u=(p*p-q+g)/h r=m-:c r*=r v=(q-r+u*i+j)/k s=m-:b
9:  w=(r-s*s+u*cn+v*co-cg)/cf x=(ch*u-ci*v+cj*w)/m y=(ck*u+cl*w+cm*v)/m
10: z=(l*v-n*u+o*w)/m x-=a y-=b z-=c :o-- :o=d+x/t*t+e+y/t*t+f+z/t*t goto8
```

You must replace this code with the following:

```
8:  p=m-:d q=m-:a q*=q u=(p*p-q+g)/h r=m-:c r*=r v=(q-r+u*i+j)/k s=m-:b
9:  w=(r-s*s+u*cn+v*co-cg)/cf :x=(ch*u-ci*v+cj*w)/m-a y=(ck*u+cl*w+cm*v)
10: :y=y/m-b :z=(l*v-n*u+o*w)/m-c :o-- :o=d+:x/t*t+e+:y/t*t+f+:z/t*t goto8
```

Then we need to make sure there is a memory chip installed that has `x`, `y`, and `z` fields. From there, any external code or Add-On may access the current coordinates via `:x`, `:y`, and `:z`.
