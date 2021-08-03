[Check us out on GitHub](https://github.com/PicoG/)    |    [Join the Discussion](https://github.com/PicoG/PicoG/discussions)

_More coming soon..._

picoG allows building and deploying LabVIEW NXG Web VIs to microcontroller boards like the [Raspberry Pi Pico](https://www.raspberrypi.org/products/raspberry-pi-pico/).

It does this by extracting the VI Assembly (VIA) files which contain the block diagram code for a Web VI and running it on a picoG's port of the [NI Vireo](https://github.com/ni/VireoSDK) open source runtime engine for (a subset of) LabVIEW.

Currently, picoG runs on the [Raspberry Pi Pico](https://www.raspberrypi.org/products/raspberry-pi-pico/) (and other compatible boards with the [RP2040](https://www.raspberrypi.org/documentation/rp2040/getting-started/) chip), but not Web VI functionality is supported (e.g. no floating point support yet).

![](https://user-images.githubusercontent.com/381432/127722850-715e39de-9642-4bb7-ae5c-262b6610d3c8.gif)
