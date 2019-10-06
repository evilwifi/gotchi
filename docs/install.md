# Installation

The project has been developed to run on a Raspberry Pi 0 W configured as an [USB Ethernet gadget](https://learn.adafruit.com/turning-your-raspberry-pi-zero-into-a-usb-gadget/ethernet-gadget) device in order to connect to it via USB. However, given the proper configuration tweaks, any GNU/Linux computer with a WiFi interface that supports monitor mode could be used.

**An important note about the AI:** a network trained with a specific WiFi interface will ONLY work with another interface if it supports the *exact same* WiFi channels of the first one. For instance, you CANNOT use a neural network trained on a Raspberry Pi Zero W (that only supports 2.4Ghz channels) with a 5Ghz antenna; you will need to train one from scratch for those channels.

## Required Hardware

- [Raspberry Pi Zero W](https://www.raspberrypi.org/products/raspberry-pi-zero-w/).†
- A micro SD card, 8GB recommended, **preferably of good quality and speed**.
- A decent power bank (with 1500 mAh you get ~2 hours with AI on).
- One of the supported displays (optional).

† Many users have gotten Pwnagotchi running on other types of Raspberry Pi, but the RPi0W is the "vanilla" hardware config for Pwnagotchi.

### Display

The display is an optional component as the UI is also rendered via a web interface available via the USB cable. If you connect to `usb0` (by using the data port on the unit) and point your browser to the web ui (see `config.yml`), your unit can work in "headless mode".

If, instead, you want to fully enjoy walking around and literally looking at your unit's face, the supported display models are:

- [Waveshare eInk Display (both V1 and V2)](https://www.waveshare.com/2.13inch-e-paper-hat.htm)
  - [Product comparison](https://www.waveshare.com/4.3inch-e-paper.htm) (scroll down to `Selection Guide`)
  - [GitHub](https://github.com/waveshare/e-Paper/tree/master/RaspberryPi%26JetsonNano/python)
- [Pimoroni Inky pHAT](https://shop.pimoroni.com/products/inky-phat)
  - [Product page](https://shop.pimoroni.com/products/inky-phat)
  - [GitHub](https://github.com/pimoroni/inky)
- [PaPiRus eInk Screen](https://uk.pi-supply.com/products/papirus-zero-epaper-screen-phat-pi-zero)

Needless to say, we are always happy to receive pull requests adding support for new models.

**One thing to note:** Not all displays are created equally! TFT displays, for example, work similar to an HDMI display, and they are NOT supported. Currently, all the officially-supported displays are I2C displays. If you are still interested in using unsupported displays, you may be able to find a community-submitted hack in the [Screens](https://github.com/evilsocket/pwnagotchi/blob/master/docs/hacks.md#screens) section of the [Hacks](https://github.com/evilsocket/pwnagotchi/blob/master/docs/hacks.md) page. We are not responsible for anything you break by trying to use any display that is not officially supported by the development team!

#### Color vs. Black & White displays

Some of the supported displays support both **Black & White** and **Colored** versions. One common question whether there are meaningful differences between the two. There are:
- Color displays have a much slower refresh rate. In some cases, it can take up to 15 seconds; if slow refresh rates are something that you want to avoid, we recommend you use B&W displays.
- The 3-color 2.13" Waveshare displays have a slightly smaller pixel layout (104x212) compared to their B&W counterparts (122x250).

#### Recommendations
- Avoid the Waveshare eInk **3-color** display. The refresh time is 15 seconds.
- Avoid the Pimoroni Inky pHAT **v1.** They're discontinued due to a faulty hardware part source used in manufacturing that resulted in high failure rates.
- Many users seem to prefer the Inky pHATs. There are two primary reasons:
  - The Inkys feature better documentation and SDK support.
  - Many Waveshare resellers do not disclose the version of the Waveshare boards they are selling (v1 vs v2), and the type they are selling can be fairly unclear (i.e., Waveshare 2.13 vs 2.13 B vs. 2.13C, and so on.)

## Flashing an Image

The easiest way to create a new Pwnagotchi is downloading the latest stable image from [our release page](https://github.com/evilsocket/pwnagotchi/releases) and write it to your SD card. You will need to use an image writing tool to install the image you have downloaded on your SD card.

[balenaEtcher](https://www.balena.io/etcher/) is a graphical SD card writing tool that works on Mac OS, Linux and Windows, and is the easiest option for most users. balenaEtcher also supports writing images directly from the zip file, without any unzipping required. To write your image with balenaEtcher:

- Download the latest [Pwnagotchi .img file](https://github.com/evilsocket/pwnagotchi/releases).
- Download [balenaEtcher](https://www.balena.io/etcher/) and install it.
- Connect an SD card reader with the SD card inside.
- Open balenaEtcher and select from your hard drive the Raspberry Pi .img or .zip file you wish to write to the SD card.
- Select the SD card you wish to write your image to.
- Review your selections and click 'Flash!' to begin writing data to the SD card.

Your SD card is now ready for the first boot!
