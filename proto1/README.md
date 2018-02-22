## Prototype 1

TOC:

- [Wed Feb 21 2018 - Attempted boardmount, new keycap print](#wed-feb-21-2018---attempted-boardmount-new-keycap-print)

### Wed Feb 21 2018 - Attempted boardmount, new keycap print

Printed the first proofs of concept for the cherry mx breakout mounting board, combining two parametric snap standoffs and the following settings:

SPCB Standoff oscad files: https://www.youmagine.com/designs/parametric-snap-in-pcb-standoff

#### standoff v1:

Files:

- [standoff peg - v1.stl](files/standoff%20peg%20-%20v1.stl)
- [standoff board - v1.stl](files/standoff%20board%20-%20v1.stl)
- [standoff board - v1 + v2.gx](files/standoff%20board%20-%20v1%20+%20v2.gx)

Standard module function in scad file. commented out the base square, translate function changed to match dimensions:

```
translate([0,0,1])boardmount(HoleD = 2.5, BoardThick = 1.70, lift=10);
```

#### standoff v2: 

Files:

- [standoff peg - v2.stl](files/standoff%20peg%20-%20v2.stl)
- [standoff board - v2.stl](files/standoff%20board%20-%20v2.stl)
- [standoff board - v1 + v2.gx](files/standoff%20board%20-%20v1%20+%20v2.gx)

Also printed a second proof of concept, same translate function, but changing the module function, line 28 from `1` to `.5` to read:

```
cylinder(r = (HoleD/2)+.5, h=lift); //standoff is always 1mm> post size (Diameter)
```

Both of these were printed at standard print settings, PLA 1.75mm, FlashForge Finder

#### Standoff v1 + v2 Results:

Once printed, the peg wouldn't pass through the mounting hole on the PCB, and when worked at to force in, snapped the pegs off, on both mounts.


#### Standoff v3: 

Files:

- [standoff peg - v3.scad](files/standoff%20peg%20-%20v3.scad)
- [standoff peg - v3.stl](files/standoff%20peg%20-%20v3.stl)
- [standoff board - v3.stl](files/standoff%20board%20-%20v3.stl)

next peg attempt, changing some of the parameters in the scad module section, but was unable to print/test due to time constraints

#### Keycap v2, round key mount

Files:

- [keycap - v2.stl](files/keycap%20-%20v2.stl)
- [keycap - v2 (lowfi, raft, x10, 180 rotated).gx](files/keycap%20-%20v2%20(lowfi,%20raft,%20x10,%20180%20rotated).gx)

I also created a new keycap design using tinkercad, this time with a round mount instead of the separated rectangular one (which broke after repeated use).

Printed x10, low fi settings, PLA 1.75mm, FlashForge Finder, however was unable to test on key due to time constraints
