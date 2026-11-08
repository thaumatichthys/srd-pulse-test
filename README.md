# Step Recovery Diode Pulse Generator

Note this thing hasn't been tested yet so all of this could just be stuff I dreamed up and might not work at all.

Unfortunately there seems to be only one step recovery diode (SRD) that is easily obtainable nowadays on Digikey or mouser. That being the MACOM MA144769-287T. 
This one is pretty mediocre compared to the high performance ones used in sampling heads etc, with a transition time of 150ps, around 1pF of capacitance, and it is a SOT-23 package which 
is pretty large and has a correspondingly huge package inductance. Therefore the performance of this pulse generator is not expected to be too crazy.

### SRD Drive

To get an SRD to "snap", you basically just run a forward current through it for a while, and it will build up an internal stored charge with the rate proportional to the amount of charge it has 
already. After it has a forward current running and some stored charge, you basically try to feed as much reverse current as possible, and it will basically start conducting using that stored charge.
After that runs out, it will abruptly stop conducting, and this impedance step is where the pulse comes from. This board uses the EPC21601 GaN eToF laser driver to do this. The EPC21601 seems to be pretty
good for this since it advertises <1ns fall time and was actually designed with timing accuracy in mind, unlike devices made for switching power supplies. It also has a gate driver built in and comes in a small
(read low inductance) package. Unfortunately that makes it kind of painful to assemble by hand.

