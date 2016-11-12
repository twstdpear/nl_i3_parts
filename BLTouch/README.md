# Mount for the BLTouch.  

It's a direct bolt-in mount which uses the same screws and holes as the 
capacitive probe mount. V2 is strongly recommended. The probe is *almost*
in line with the nozzle (Y+3mm off), which prevents the BLTouch from
hitting things on the bed (e.g., binder clips holding a piece of glass on
the bed).  V1 was rotated 90 degrees and something like Y+15.  

In addition to the screws reused from the old mount, it requires: 
* (2) m3x10mm screws
* (2) m3 nuts or locknuts
* (2-10) m3 washers

The washers are used as shims between the mount and the BLTouch to fine-tune 
the height.  The exact number may vary, but 2 on each side is probably a 
good starting point.  

Included is my Configuration.h and Configuration_adv.h for Marlin.  It should 
be a plug-in replacement for RCBugFix commit #8ddd039, which is post RC7 and 
has proven to be pretty stable for me.  Note that this is for a BG8 machine, 
which has a RAMBo controller. It's recommended to use Marlin RC7 or above, 
since it natively supports the BLTouch without additional modifications.  Any 
other version will require side-by-side comparison of the configuration file 
at a minimum.
