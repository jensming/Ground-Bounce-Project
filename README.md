Ground Bounce Project is a collection of netlists, schematics, artwork as well as drill files, and among others from using OrCAD Capture
and Allegro PCB Editor to design the test circuit. The PCB (2-layer copper clad board with a FR-4 substrate) was milled using the M60 LPKF and all surface mount components were soldered on by hand.


Below is the v1.2 test circuit with a +5V power supply (upper left) and an input clock signal of 1MHz at 1.5Vpp (lower left) connected to it. The PCB exhibits a deterious electrical phenomena known as ground bounce where the internal ground reference of an IC (the SN74AHC174 in this case) changes. This induces unwanted shifts in input thresholds and output margins that are observed as glitches when logic devices switch from one state to another. The effects of ground bounce on a digital system were observed on an oscilloscope.

![IMG_3157](https://user-images.githubusercontent.com/65200990/179433968-1e4fb3cd-7efa-4c60-993c-fb0898315b0e.jpeg)


The image below shows the observed results on the oscilloscope where the yellow waveform is the clock signal, the purple waveform is the 
reset signal (essentially the clock signal delayed), and the blue waveform is the experimental ground bounce. The ground bounce occurs at
the falling edge of the reset signal (master resets SN74AHC174) as expected. This logic switching produces a massive current surge on the 
device-to-ground path which works across the package’s ground pin and induces a shifting voltage seen over the bond-out lead inductance 
according to Lenz’s Law.

![IMG_3188](https://user-images.githubusercontent.com/65200990/179433997-bc577a0f-db8c-4e37-bea1-e31924354a9d.jpeg)
