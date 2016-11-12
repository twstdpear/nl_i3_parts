# Mount for the BLTouch.  

This is a direct bolt-in mount which uses the same screws and holes as the 
capacitive probe mount. V2 is strongly recommended. The probe is *almost*
in line with the nozzle (Y+3mm off), which prevents the BLTouch from
hitting things on the bed (e.g., binder clips holding a piece of glass on
the bed).  V1 was rotated 90 degrees and something like Y+15, so it hit my
binder clips.

In addition to the screws reused from the old mount, it requires: 
* (2) m3x10mm screws
* (2) m3 nuts or locknuts
* (2-10) m3 washers

The washers are used as shims between the mount and the BLTouch to fine-tune 
the height.  The exact number may vary, but 2 on each side is probably a 
good starting point.  Too many is better than too few.

Included is my Configuration.h and Configuration_adv.h for Marlin.  You shoudl be able to drop it right into Marlin RCBugFix commit #8ddd039, which is post RC7 
and has proven to be pretty stable for me.  Note that this is for a BG8 
machine, which has a RAMBo controller. It's recommended to use Marlin RC7 or 
above, since it natively supports the BLTouch without additional modifications.
Any other version will require side-by-side comparison of the configuration 
files at a minimum, maybe more.

# Installation/configuration

Here's some videos demonstating what we're trying to accomplish:

[Tutorial - ANTCLABS BLTouch Install - Part 1 - 3D Printing](https://www.youtube.com/watch?v=dB6QjifoYDU)
[Tutorial - ANTCLABS BLTouch Install - Part 2 - 3D Printing](https://www.youtube.com/watch?v=OoWP5C8lSig)

To get your Z height correct, I found that 2 post-it notes put the hot end of 
my BG8 printer at just the right height.  You should *just barely* feel some 
drag on the two sheets and no drag at all on 1 sheet.  You should do this with 
your nozzle hot, maybe not at full printing temperature, but warm enough that 
any plastic on the end of the nozzle is soft (e.g., 170C+ for PLA, 220C+ for 
PET), otherwise any cooled plastic on the nozzle may throw things off.

After that, print some [test frogs](http://www.thingiverse.com/thing:3284) and
fine tune it based on the results from your real-world test.

If you're a little too high, subtract from your M851 value 
(e.g., M851 Z-1.24  -> M851 Z-1.29).  If you're a little too close, add to 
your M851 value.  Earlier versions of Marlin handled this differently and 
apparently used positive values, so do your research before taking my word
for it.

You'll need a computer for this process, such as Pronterface or the Aduino 
IDE's terminal.  You can also adjust the M851 value from the LCD menu at the 
top of the Control->Motion menu.

G0 F9000 ; only need this the first time to set your speed
G28 ; Home X/Y/Z
G0 X100 Y100 Z0 ; go to Z=0 and test with the paper
M851 Z-1.25 ; Adjust your Z offset based on the results.  
;Go back to G28 above.
M500 ; when you're happy with the results to save it to the EEPROM

Your M851 value should be somewhere between -1.0mm and -2.0mm.  I prefer it to 
be closer to -1.0mm so the probe is a little higher when stowed, so there's 
just a little more clearance if your print curls up.

# Connecting it to your RAMBo

[RAMBo board documentation](http://reprap.org/wiki/Rambo)
[RAMBo connector diagram](http://reprap.org/mediawiki/images/5/5c/Rambo-conn-all.jpg)

You'll be connecting your BLTouch to pins 1-3 of the X20 motor extension and 
the "S" and "-" pins of Z-min endstop connector.

Review the connector diagram above.  The X20 motor extension is the leftmost 
of the three, and Pin 1 is at the bottom.  You should already be using Z-min 
for your existing probe.

BLTouch Red -> X20 Pin 1 (5V)
BLTouch Brown -> X20 Pin 2 (GND)
BLTouch Orange -> X20 Pin 3 (Signal)
BLTouch Black -> Z-min "-" (GND)
BLTouch White -> Z-Min "S" (Signal)

You Since X20 Pin 2 and Z-min "-" are both grounds, you can save a wire by using the following:

BLTouch Red -> X20 Pin 1 
BLTouch Brown -> X20 Pin 2
BLTouch Orange -> X20 Pin 3
BLTouch Black -> tie to BLTouch Brown
BLTouch White -> Z-Min "S"

Whatever you do, check, check and re-check the 5V and GND, or you could damage 
your BLTouch.

#Conclusion

Hopefully that gives you enough breadcrumbs to get everything set up.
