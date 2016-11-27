# MIDI2DMX

##Control DJ lights and LEDs from any software or hardware that can transmit MIDI

##This project came out of research associated with my work at Portland Community College as an Audio Programming Instructor in the Music and Sonic Arts department.

Eagle files for the PCB are published here - but you can also order them from OSHPark: https://oshpark.com/shared_projects/hyqqaC5r

Besides a Teensy (I've tested with a 3.2 - an LC should also work though) https://www.pjrc.com/store/teensy32.html

The mouser BOM is here: http://www.mouser.com/ProjectManager/ProjectDetail.aspx?AccessID=11855f0a7f

If you want a more detailed guide I've published this: http://www.instructables.com/id/MIDI2DMX/

This is an easy way to get total control over a wide variety of lights - using existing music software (ableton live, logic, bitwig, garage band, pro tools etc). It also allows for easy interfacing with programming environments like Pure Data, MaxMSP, Processing etc).

This makes it easy to sequencing lights for live music performances, do algorithmic light programming, map lights using sound analysis, data from the internet, or sensor data etc.

It unlocks cheap DJ lights, turning them into flexible and expressive tools/instruments.

It turns out that it's pretty hard to find a good, well supported, inexpensive DMX controller.

There are a lot of expensive DMX controllers with proprietary drivers. There are a lot of cheap DMX controllers with little or no documentation. (Although these days a lot of them are copied from the uDMX project). Some of them work intermittently, some work only on windows, and some work only with specific (unexciting) DMX control software.

The uDMX project http://www.anyma.ch/research/udmx/ is the only well documented open source option out there, but in my experience - it's not that good. It suffers from choppy framerates and frequent drop outs, and on top of that, all the units I tried became unresponsive fairly often in a variety of software applications. There is a fundamental design flaw: it relies on your computer to send DMX frames. If your computer is processing audio (from Pure Data or Max for instance) - you end up with pretty severe audio dropouts. Also your framerate suffers due to varies computer and USB bus performance issues.

This project uses a Teensy - with some rock solid and extremely fast code from Paul Stoffregen.

The Teensy is programmed to be a USB midi device, and is setup to translate midi cc's into DMX channel values. (Mapping CC numbers directly to DMX channel numbers).

I designed this PCB to make the circuit easy to build, and have assembled quite a number of them with some of students in my interactivity courses at Portland Community College.

##PD STUFF:
In the PD folder you'll find a few example patches.

DMX_color_presets.pd shows how to translate RGB and HSV color values into messages you can send to your lights. Google has a nice color picker tool.

hsv2rbg.pd is an abstraction that the other patches rely on. All of these pd patches need to be put in the same folder to work correctly.

DMX_color_organ.pd has a simple midi mapping using Scriabin's pitch-color associations. (https://en.wikipedia.org/wiki/Clavier_%C3%A0_lumi%C3%A8res)

This makes any DMX light playable from a midi keyboard or midi sequencer like Ableton Live, Logic, Bitwig - as well as hardware sequencers like MPCs and Octatracks. This is my preferred method for programming custom light shows for live PA's.

Finally DMX_audio_analysis.pd demonstrates pitch and amplitude tracking and translation into light color and intensity using pd. You need to make sure you have an audio input setup in PD (Media -> Audio Settings) - although the built-in mic on your laptop should work just fine.

