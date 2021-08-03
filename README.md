picoG lets you deploy LabVIEW NXG Web VIs to microcontroller boards like the [Raspberry Pi Pico](https://www.raspberrypi.org/products/raspberry-pi-pico/)!

Here is a "hello world!" example, outputting messages on its USB serial port:

![](https://user-images.githubusercontent.com/381432/127722850-715e39de-9642-4bb7-ae5c-262b6610d3c8.gif)

### How it Works

PicoG watches your LabVIEW NXG Web VI project and notifies you when it has been built. When you choose to deploy it to your RPi Pico, picoG extracts the VI Assembly (VIA) files from the Web VI build output (VIA contains the block diagram code for a Web VI) and then processes and deploys it to the RPi Pico.  The VIA runs inside of [PicoVireo](https://github.com/PicoG/PicoVireo) (a microcontroller port of the [NI Vireo](https://github.com/ni/VireoSDK)), which is an open source runtime engine for a subset of LabVIEW.

### Status

picoG currently runs on the [Raspberry Pi Pico](https://www.raspberrypi.org/products/raspberry-pi-pico/) (and other compatible boards with the [RP2040](https://www.raspberrypi.org/documentation/rp2040/getting-started/) chip) and supports basic LabVIEW functionality. We are working to support more and more functionality of LabVIEW, as well as more microcontroller chips and boards.

### How to Get Involved

If you'd like to help, please [post to our discussion forum](https://github.com/PicoG/PicoG/discussions).

In addition to LabVIEW experience, we're especially looking for people with C++, cmake, and microcontroller experience.
