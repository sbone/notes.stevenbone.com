---
layout: post
title: "Hackintosh Build Log"
---

Stumbled across tonymacx86's [Buyer's Guide](http://www.tonymacx86.com/building-customac-buyers-guide-november-2015.html) and [Installation Guide](http://www.tonymacx86.com/el-capitan-desktop-guides/172672-unibeast-install-os-x-el-capitan-any-supported-intel-based-pc.html),
and assumed the process had been ironed out by the community.

My goal was to replace an aging Mac Mini that was my HTPC, running Plex Server. So, I went with the [CustoMac Mini Deluxe](http://www.tonymacx86.com/building-customac-buyers-guide-november-2015.html#CustoMac_Mini_Deluxe).
Hardware details:

- CPU: **i7-4790S** (9624 Passmark = 6x 720p streams in Plex, or 4x 1080p!)
- RAM: **16GB**
- SSD: **Samsung 850 EVO 500GB**
- PSU: **Corsair CS450M** (Even 450W is a little overkill for this build)
- MOBO: **Gigabyte GA-H97N-WiFi**
- CPU Cooler: **Noctua NH-L9i** (I bought CPU used, and the case I chose had very low cooler clearance)
- CASE: **Cooler Master Elite 110**

I ran into a couple issues once all the hardware was put together:

1. **Grab El Capitan directly from the App Store.** Two older versions (that included MAS receipts, etc.) I grabbed from reliable sites threw errors. I ended up using the El Capitan installer directly from the App Store.
2. **Use an up-to-date Mac to create the Unibeast USB Drive.** I was still running 10.7.5 on my old Mini, and grabbed the App Store's El Capitan. My Hackintosh wouldn't boot from it. Creating it on my Macbook Pro running El Capitan worked, though.
3. **In Multibeast, set a proper System Definition.** Following the logic for building a Mac Mini replacement, I initially chose a Mac Mini System Definition. But, my system wouldn't come back up correctly (unless I was booting in Verbose mode, it would get stuck on the gray loading screen).
On my second attempt I set it to a Mac Pro definition, but that just caused kernel panics. I cross-referenced models on [EveryMac](http://www.everymac.com/) and found my configuration was more similar to a high-end iMac. Success!
4. **Drobo 5D acts strange on reboot.** I haven't found a fix for this, but when I reboot, my Drobo 5D (connected via USB 3), doesn't appear on its own. I've had to unplug and plug it back in a couple times.
5. **Intel HD 4600 is limited in screen resolution.** Another issue I haven't found a fix for, but I can't get a resolution higher than 2048x1152.

<img src="/i/hackintosh-info.png" alt="My Hackintosh Specs" />

I've been running Plex Media Server and Sonarr smoothly for a couple days now.

FYI - I haven't tried my Hackintosh Wifi, Bluetooth, or most other features. I run this box headless, connected to ethernet.
