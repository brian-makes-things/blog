---

title: CM4 for the C3
author: Brian VanLoo
post_status: preview
stick_post: no
featured_image: _images/CM4_4_C3.jpg
taxonomy:
    category:
        - hardware
    post_tag:
        - Raspberry Pi
        - CM4
        - Cinema Camera Controller
        - C3

---

I was talking with my colleague about some future projects and we got excited about the prospects of developing our own carrier board for a [Raspbery Pi Compute Module 4](https://www.raspberrypi.com/products/compute-module-4/?variant=raspberry-pi-cm4001000).
This development would be a little tricky because designing your own PCB and manufacturing it can be time consuming and a bit difficult to get right.
Given that, I proposed that we come up with something that would be kind of useful but lower-stakes to be used as a learning project.

After thinking through some other possible projects we eventually landed on making a carrier board for the [DIY Cinema Camera Controller (C3)](https://brollbanter.com/c3).
We'd pair it with the [4.3" screen](https://amzn.to/3UcMQC3) from the DIY stack and add our own flat LiPO battery with its charging circuitry on our carrier board.
This would allow us to build a much slimmer hardware stack than the DIY's separate modules.

# The Goal

The real goal here is to see how many of the functions on the carrier board we could make work.
That included adding some features that we might not ultimately want in a wireless camera controller but that we may want experience with for future carrier board projects.

Our required hardware features are:

  - One DSI controller to interface to the touch screen
  - Battery charger and power supply
  - A USB micro port for flashing the eMMC on the CM4
  - Two RGB LED rotary encoders (OK, we may not have needed the RGB part but it's going to be real cool)
  - Two buttons

The other features we wanted to gain experience with but that wouldn't be used in a wireless camera controller are:

  - One USB A port
  - One HDMI port

The CM4 module configuration we'll be targeting is one with WiFi (it needs that to remain wireless) and with eMMC (we don't want to mess around with SD cards).

# Development Tools

I'm already familiar with [KiCAD](https://www.kicad.org/) and have used it for building boards for my modular synthesizer work (I show how on [my youTube channel dedicated to DIY synthesizer projects](https://youtube.com/@eurorackDIY)).
It turns out there's a nice [reference implementation](https://datasheets.raspberrypi.com/cm4io/CM4IO-KiCAD.zip) available from the Raspberry PI folks, also done in KiCAD.
For designing the circuit I'll mostly be deleting things from that reference (board layout is another story).

Because the Raspberry Pi folks want the CM4 to be adopted into other hardware designs they've also done a great job of [providing documentation](https://www.raspberrypi.com/documentation/computers/compute-module.html) about the module.

# Current Status

I'm still doing the schematic capture for the circuit and hope to have that wrapped up in a couple of days.
From there I'll be moving on to laying out our board which will be sized to mount to the back of the 4.3" display.

The board layout will be a learning experience as there are signal lines that need to have specific impedences and matched trace lengths.

Once that's all done we'll be sending things off to [JLCPCB](https://jlcpcb.com/) to have the boards made and their surface mount components assembled.

Sign up for my newsletter to get future updates on the progress of this project.
