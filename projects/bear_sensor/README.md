Bear Sensor
===========

My friend Kirti Chavan working to conserve the Himalayan Brown Bear in Zanskar, Ladakh. We are trying out different ways to detect when a bear is trying to enter houses in search of food. Idea is to alert the humans or scare the bear away and avoid human-animal conflicts. We will work on putting together simple electronic circuits and Kirti will test drive them out in the field to see which one works best and is easy to maintain.

Know more about Kirti's project:

 - [Fund Raiser](https://milaap.org/fundraisers/support-the-himalayan-brown-bear-project)
 - [His Facebook page](https://www.facebook.com/kirti.chavan.5891)
 - [His paper](https://digitalcommons.usu.edu/hwi/vol15/iss1/24/)


# 2022-04 Version 1 using BBC micro:bit


![Fritzing Sketch](v1_microbit_relay_hooter/sketch.png?raw=true "Fritzing Sketch")

The first version involves embedding BBC micro:bit in a wooden plank. Whenever a bear disturbs the wooden
plank, a sketch running inside the micro:bit would detect that by continuously observing the accelerometer readings - tilting the plank would change the orientation of the micro:bit and hence change the output of the accelerometer.

## Parts List with links to local vendors


  - [BBC micro:bit V2](https://robu.in/product/bbc-micro-bit-v2-pocket-sized-single-board-computer/)
  - Generic MicroUSB Cable for programming and power (don't buy bad quality ones that dont have wires for data signals). Need two of thes: one for powering the micro:bit and other for powering the 5 volts relay.
  - Generic 12 volts car or motor cycle sealed lead acid battery
  - Some local system for keeping the 12 volts battery charged using solar power
  - Generic cigarette lighter socket mobile charger for converting 12 volts. Non QC 3.0 charger will do as well. Needs to have 2 USB sockets - one for micro:bit and another for relay [Something like this one will do](https://www.amazon.in/Ambrane-Charger-Qualcomm-Certified-ACC29QCM/dp/B082251822)
  - [12 volts Hooter](https://www.amazon.in/gp/product/B08CBC6S8W)
  - Single channel opto-isolated relay to interface a 5 volts relay to 3.3 volts I/O of the BBC Micro:bit to switch 12 volts to the hooter. [This dual channel will do as well](https://www.amazon.in/xcluma-Channel-Expansion-Arduino-Raspberry/dp/B0716Z2CC2)
