Here's how to get started with PicoG.  Don't worry, it'll be much easier, soon...

Currently, you will need to run PicoG from source (or build the EXE from source). We're working an installer that will make getting started a lot easier (especially if you're just interested in using picoG and not actually contributing to the project).

Also, your deployed applications will need to be redeployed after restarting your RPi Pico Board -- meaning: the program does not persist on the board's non-volatile memory. We are working on ways for you to burn/flash your program onto the board, so that it runs automatically at startup. If you want to help out with this, [join the discussion](https://github.com/PicoG/PicoG/discussions).

## Running or Building PicoG from Source

### Prerequisites (to install)

1.  [LabVIEW NXG Community Edition](https://www.ni.com/en-us/support/downloads/software-products/download.labview-nxg-community.html#370014) version 5.1 or later (for developing WebVIs -- see NXH Web Module sub-bullet, below)
    1.  [LabVIEW NXG Web Module](https://www.ni.com/en-us/support/downloads/software-products/download.labview-nxg-web-module.html#369493) version 5.1 or later (for developing WebVIs to generate the VIA that is processed and downloaded to the microprocessor boards)
2.  [LabVIEW 2020 Community Edition](https://www.ni.com/en-us/support/downloads/software-products/download.labview-community.html#370001) version 2020 SP1 or later (for running and building PicoG Desktop from source)
    1.  MGI Solution Explorer this is an option during the LabVIEW 2020 installation. Be sure to install it.
    2.  If you don't have it installed, you can install it with NI Package Manager
        1.  Open NI Package Manager
        2.  Enable the configuration setting to "Show available packages and feed management tools"
        3.  Go to the "Packages" tab, then find MGI Solution Explorer and install it.
3.  [VI Package Manager](vipm.io/desktop) version 2020 or later (for installing packages required by PicoG Desktop sources)

### Building and/or Running PicoG Desktop from Source

Note that we are working on an installer, which will not require any of the steps below -- you will simply run the installed PicoG App from the Windows Start Menu.

1.  **Get the PicoG Desktop Sources** - Clone or download the [PicoG Desktop](https://github.com/PicoG/PicoG) git repository, using one of the following:
    1.  Command Line: `git clone https://github.com/PicoG/PicoG.git`
    2.  [Open with GitHub Desktop](x-github-client://openRepo/https://github.com/PicoG/PicoG)
    3.  [Download a ZIP](https://github.com/PicoG/PicoG/archive/refs/heads/main.zip)
2.  **Install Required VI Packages** - this will install (using VIPM) the packages required by the PicoG Desktop sources
    1.  double-click the `picog.vipc` (VI Package Configuration) file to open it in VIPM.
    2.  When prompted to install the packages, choose LabVIEW 2020
3.  Automatic Build of All PPLs and EXE (Requires MGI Solution Explorer / Skip if you want to do #4 below)
    1.  You can build all PPLs and the EXE by building the `PicoG-LV.lvsln` (LabVIEW Solution) using MGI Solution explorer
    2.  Double click the `PicoG-LV.lvsln` file to open it in MGI Solution Explorer and then build the solution
    3.  after building, look in the .\\Builds\\picoG folder for the executable and run it.
4.  Manual Build of **Build PPLs (skip if you did #3 above)** -- you can skip this step if you did step number 3, above
    1.  In LabVIEW 2020 open and build the following PPLs:
        1.  PicoG-Core.lvproj >> My Computer >> Build Specifications >> PicoG-Core
        2.  Platform-RP2040.lvproj >> My Computer >> Build Specifications >> RP 2040 PPL
    2.  Run PicoG from Source code
        1.  PicoG-Processor.lvproj >> PicoG-Processor.lvlib >> Main.vi
        2.  Run `Main.vi` in LabVIEW
5.  Success! PicoG is now running and ready to deploy WebVIs to microprocessors!

## Preparing your Raspberry Pi (RPi) Pico

### Installing picoG on your Raspberry Pi (RPi) Pico

1.  Download the pico.uf2 firmware file
2.  Put your RPi Pico in bootloader mode by pressing the Bootloader button before/while plugging it into your USB port
3.  Copy the pico.uf2 file to the PICO usb drive
4.  The pico will reboot automatically and should now be running PicoVerio, allowing PicoG Desktop to deploy your webVIs

## Editing and Deploying WebVis to your RPi Pico Board

### Deploying WebVIs to your RPi Pico board

1.  Open `PicoG-Lib.lvproject` in LabVIEW NXG
2.  Open `PicoG-Lib\Examples\HelloBlink.gcomp\HelloBlink.gviweb`
    1.  This is your WebVI source code
    2.  Edit it as you wish
3.  Open `PicoG-Lib\Examples\HelloBlink.gcomp\HelloBlink.gcomp`
    1.  This is your Web component that will get built into VIA
    2.  Click "Build" to build the web project and generate the VIA
4.  In the PicoG Desktop app (if it's not running already, run it now), click on the Folder icon/button and browse/select the `PicoG-Lib.lvproject` file.
    1.  This will cause PicoG Desktop to watch the project for WebVI build outputs
    2.  You should see HelloBlink in the list of discovered build outputs
    3.  Click on the "Deploy" button to deploy HelloBlink to your RPi Pico board
    4.  Select `RP2040` as the device type
    5.  Select the COM port your RPi Pico is connected to
    6.  If you see your RPi Pico's LED blinking, that means you have successfully deployed LabVIEW to your RPi Pico!
    7.  Celebrate!

### Editing and Re-Deploying the HelloBlink Application

1.  Choosing a new value for the Wait Millisecond timer, which should change the rate of blinking
2.  Rebuild HelloBlink.gcomp and notice that PicoG Desktop blinks to let you know it sees a new build
3.  Reset your RPi Pico board (so that it's not running your HelloBlink code and is ready for deploying new VIA) by unplugging it and plugging it back in (but don't press the bootloader buttonm since we want to keep PicoVireo firmware running).
4.  Click the "Deploy" button to download your new version of HelloBlink to the RPi Pico board
5.  Notice that the rate of blinking has changed to whatever value you specified

### RPi Pico Library Vis

Notice the VIs in PicoG-Lib.lvproject >> Pico-G-Lib >> PicoGLib.gcomp

*   Core
    *   MemUsed - Gets the total memory used by the RPi Pico - 256k is the max memory available
    *   Println - Prints a line of text to STDOUT (e.g. the USB Serial Port, which you can read using HyperTerminal or Putty at 115200 baud, 8N1, XON/XOFF)
*   GPIO
    *   Init
    *   Read
    *   SetOutput
    *   SetPulls
    *   Write
