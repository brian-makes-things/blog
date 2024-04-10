---

title: Time for an Upgrade
author: Brian VanLoo
post_status: draft
featured_image: _images/upgrades.jpg
taxonomy:
    category:
        - software
        - resources
    post_tag:
        - Vue
        - Pinia

---

Previously I'd done some development to build a cinema camera controller powered by a Raspberry Pi.
It provided a wireless controller that gave access to most of the camera's settings.
I'd last worked on it with a colleague about two years ago and while dusting the project off it became apparent that we'd need to upgrade the technology stack so that we can run it with current OS versions.
The OS version upgrade then leads to running newer versions of the tech stack which then leads to needing to upgrade the code for the application itself.

## The hardware stack

As mentioned, this is all meant to run on a Raspberry Pi.
In the case of what we're currently doing, we've chosen a 3B+ since it offers both the compute power needed to build what we want and at a lower power consumption than other, newer Pi offerings.
The power draw is critical as this is meant to be a wireless controller so we also wanted to maximize battery life.

The initial user interface is provided by a touch screen which is connected to the Pi via a DSI cable.
We're using a [4.3" class screen](https://amzn.to/3UcMQC3) that the Pi board itself is bolted onto.

For power we've opted for a [UPS hat](https://amzn.to/4aJW9Pe) that is also bolted on, creating a robust stack of hardware.

## The software stack

Because the Pi offers a full Linux offering I decided the best way to create a UI would be to run a browser on the screen desktop in kiosk mode.
That browser would show a single page app hosted by a [Vue.js](https://vuejs.org/) server, also on the Pi.
This way a clean UI could be developed with little fiddling with the UI components and using CSS to control placement and look and feel of the controls.

Previous development was done with Vue version 2 and it allowed for most of the logic to control the camera to be written in JavaScript and run inside the browser.

## The problem

Upon re-opening the project to finish off some features and build ourselves a working prototype that we could take in the field I discovered that I could no longer do development on my laptop as I'd upgraded the version of Node (the JavaScript interpreter) that I'm running.
The packages used by our previous development efforts no longer ran with the current version of Node.

Just upgrading those packages led to more problems with some releases for some dependencies no longer working, etc.
This feels like a common problem in the JavaScript world.

Further, the version of the Raspberry Pi OS is now two years old and it would be a good idea to catch up there too.
Newer versions will also upgrade the Node version they want to run, creating much the same problem as I have on my development laptop.

## What I ended up doing about it

So it's time to modernize things.
Vue is now at version 3 so I started with a fresh install of that as a base and started working through the changes I needed to make to the code I'd previously written.

The app itself mirrors the state of the settings on the camera so that they display correctly as the app is navigated and the camera settings are updated.
The biggest changes were around how state for the app was maintained so I adopted [pinia](https://pinia.vuejs.org/) and then had to change all my state management.

## What's next

Now that I have the app returned to it's previous functionality with upgraded hardware I need to put the changes back into our development repo.
After that it's time to put the new software on the Pi with an upgraded OS and verify that it all works together.

Then let's hope we don't need to make such a drastic upgrade two years from now...
