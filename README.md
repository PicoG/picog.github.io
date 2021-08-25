_Run G Dataflow code (i.e. LabVIEW) on Microcontrollers... it's free!_

## About picoG

picoG is a free (open source) tool that lets you deploy G Dataflow code to microcontrollers!

(It uses the free [G Web Development Software Community Edition](https://www.ni.com/en-us/support/downloads/software-products/download.g-web-development-software.html) (formerly LabVIEW NXG Web Module) as the G Dataflow IDE.)

\>> [Click here to get started with PicoG](https://www.picog.org/getting_started) \<\<

Here is a "hello world!" example, running on the [Raspberry Pi Pico](https://www.raspberrypi.org/products/raspberry-pi-pico/) board and outputting messages on the board's USB serial port:

![](https://user-images.githubusercontent.com/381432/127722850-715e39de-9642-4bb7-ae5c-262b6610d3c8.gif)

## How it Works

TL:DR - PicoG watches your G Web projects -- then, when you hit "Build" in G Web, PicoG will builds and deploys it to your RPi Pico.

Details: picoG extracts the VI Assembly (VIA) files from the Web VI build output (VIA contains the block diagram code for a Web VI) and then processes and deploys it to the RPi Pico.  The VIA runs on the picoG firmware (a microcontroller port of [NI Vireo](https://github.com/ni/VireoSDK)), which is an open source runtime engine for a subset of LabVIEW.

## Status

picoG currently runs on the [Raspberry Pi Pico](https://www.raspberrypi.org/products/raspberry-pi-pico/) (and other compatible boards with the [RP2040](https://www.raspberrypi.org/documentation/rp2040/getting-started/) chip) and supports basic LabVIEW functionality. We are working to support more and more functionality of LabVIEW, as well as more microcontroller chips and boards.

## Get Involved

If you'd like to help, please [post to our discussion forum](https://github.com/PicoG/PicoG/discussions).

In addition to LabVIEW experience, we're especially looking for people with C++, cmake, and microcontroller experience.
