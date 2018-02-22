## Prototype 1

### Wed Feb 21 2018 - Attempted bourdmount, new keycap print

Printed the first proofs of concept for the cherry mx breakout mounting board, combining two parametric snap standoffs and the following settings:

SPCB Standoff oscad files: https://www.youmagine.com/designs/parametric-snap-in-pcb-standoff

#### standoff v1: Standard module function. commented out the base square, translate function changed to match dimensions:

```
translate([0,0,1])boardmount(HoleD = 2.5, BoardThick = 1.70, lift=10);
```

#### standoff v2: Also printed a second proof of concept, same translate function, but changing the module function, line 28 from `1` to `.5` to read:

```
cylinder(r = (HoleD/2)+.5, h=lift); //standoff is always 1mm> post size (Diameter)
```

Both of these were printed at standard print settings, PLA 1.75mm, FlashForge Finder

#### Standoff v1 + v2 Results:

Once printed, the peg wouldn't pass through the mounting hole on the PCB, and when worked at to force in, snapped the pegs off, on both mounts.


#### Standoff v3: next peg attempt, but was unable to test due to time constraints:

```
$fn=50;
module boardmount(HoleD,BoardThick,lift)
{
	topZ = lift+BoardThick;
	pegR = HoleD/2;
	// this is really a setting.
	notchW = pegR/1.45;//width of the flexy notch in terms of peg radius
	difference()
	{
		union()
		{
			cylinder(r= pegR,h = topZ); //master peg
			translate([0,0,topZ])cylinder(r1=pegR,r2= pegR+.35, h =1);// relief for overhang
			translate([0,0,topZ+1])cylinder(r1=pegR+.35,r2= pegR-.25, h =1); // insertion cone
			cylinder(r = (HoleD/2)+.5, h=lift); //standoff is always 2mm> post size (Diameter)
		}
	cylinder(r= pegR-.5, h = topZ+3);
	translate([-(HoleD+2)/2,-notchW/2,lift])cube([HoleD+2,notchW,6]);//notch for insertion flex
	}//difference
}; //module


// Sample part for test fitting
// translate([-2.25,-2.25,0])cube([4.5,4.5,1]);
translate([0,0,1])boardmount(HoleD = 2.5, BoardThick = 1.70, lift=10);
```

#### Keycap v2, round key mount

I also created a new keycap design using tinkercad, this time with a round mount instead of the separated rectangular one (which broke after repeated use).

Printed x10, however was unable to test on key due to time constraints
