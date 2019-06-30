---
title: Cramming a gaming GPU into your MacBook Pro
date: 2019-06-15T19:54:53.000+00:00
draft: true

---
## …without actually doing that

## How we got here

After Apple released its (soon-to-be) previous generation Mac Pro, it probably didn't take long for them to realize they had a trash can fire on their hands, especially with [regard to GPU performance](https://marco.org/2019/06/09/apple-is-listening). When Apple announced eGPU support for macOS in 2017's [High Sierra release](https://web.archive.org/web/20170731114535/https://www.apple.com/macos/high-sierra-preview/), it was hard not to see the announcement as anything more than an admission that Apple's top-of-the-line desktops and notebooks shipped with subpar GPUs due to their severe thermal constraints. Of course,  because Apple has never considered AAA gaming to be an important function of its products, the Mac has always lagged behind Windows in GPU availability and support. But by 2017 (and until the new [Mac Pro](https://www.imore.com/mac-pro-2019-everything-you-need-know) tower releases this fall), the situation has been especially grim: even for workstation tasks like video encoding and 3D modeling, the internal GPUs Apple has been selling are so bad that they're driving a nontrivial number of creative professionals—a market Apple actually does care about—off its platform.

How else can you explain the absurd amount of effort it must have taken from Apple (and Intel) so that nerds they don't care about could make the following statement in 2019: instead of putting a beefy graphics card _inside_ your computer, **you are now able to take a best-in-class GPU, seat it inside an external box, plug that box into your computer, and—using a single high-bandwidth cable—push the necessary instructions to render 4K games at 60 frames per second on the card before (over the very same cable!) pushing those frames back to your notebook's built-in monitor without introducing any perceptible latency**. I've seen daily evidence of this for the last month and I gotta say: it's pretty freakin' cool.

The idea that you'd be able to connect a GPU over a 2 meter cable and get desktop-class gaming performance out of the current crop of MacBooks Pro seems far-fetched. Even to me, as I literally play games with one. When reasonable people encounter Apple's marketing about eGPUs—which is only focused on creative professional workflows like [_modeling_ VR experiences as opposed to _experiencing_ them](https://www.youtube.com/watch?v=S48T-cOG0ks)—it would be unreasonable to make the logical leap to say, "ah, yes, surely if I boot that computer into Windows, the eGPU enclosure would have the necessary drivers and the Thunderbolt 3 cable would have the necessary bandwidth to render games in real-time at an acceptable frame rate and input lag."

_And yet_, AAA PC gaming is exactly what a MacBook + eGPU can do. It's just that nobody [other than Razer](https://www.razer.com/gaming-laptops/razer-core-x) is telling the market that.

## How to get started

Everything in this post, I pieced together from dozens of forum posts, guides, and build data from the small-but-dedicated community at [eGPU.io](https://egpu.io). Because the very-newest Macs, eGPU enclosures, and operating system releases have made things much easier (so much so, that half the content in published guides no longer applies), I will present a stripped-down walkthrough that starts fresh with the latest operating systems and components.

**Hardware:**

* [13-inch MacBook Pro (mid-2019)](https://everymac.com/systems/apple/macbook_pro/specs/macbook-pro-core-i5-2.4-quad-core-13-mid-2019-touch-bar-specs.html)
* [AMD Radeon VII](https://www.amd.com/en/products/graphics/amd-radeon-vii) card
* [Razer Core V2](https://www.amazon.com/Razer-Core-V2-Thunderbolt-Enclosure/dp/B0791ZCH4Q) (which Razer has already discontinued in favor of the larger, cheaper [Razer Core X](https://www.razer.com/gaming-laptops/razer-core-x))
* Any certified [2 meter Thunderbolt 3 cable](https://www.amazon.com/gp/product/B01H5QF2TK/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1)
* Any TV or external monitor you want to output games to (Optional)

**Software:**

* macOS 10.14.5 (18F132)
* Windows 10 version 1903 (18362.175)

### Initial questions you might have

**Why an AMD card over Nvidia?** If you plan on ever plugging the eGPU into macOS (as opposed to Windows), you're going to have a much easier time of it with an AMD card. macOS ships with drivers for most AMD cards, but Nvidia support is a [tremendous pain](https://egpu.io/forums/mac-setup/wip-nvidia-egpu-support-for-high-sierra/) that's only getting worse with time, as zero Mac drivers are available for their new [RTX](https://www.nvidia.com/en-us/geforce/20-series/) line.

**Why a Razer Core V2?** I chose this model because it's lightweight (at a "mere" 11 pounds), properly isolates bandwidth (5gbps) for its 4 USB ports, and is relatively small size (7.5 liter). It can't buffer much heat or noise, though. In truth, there are actually quite a few [decent options out there](https://egpu.io/external-gpu-buyers-guide-2019/), and most will incorporate the same Thunderbolt 3 controller doing the heavy lifting.

**Why an external monitor?** While both macOS and Windows can "loopback" frames rendered by the eGPU over the cable and onto the computer's built-in monitor, operating system support for this is very recent and it introduces a nonzero bandwidth cost which can result in lower framerates as well as frames being dropped. Adding to that, the relatively high DPI of Apple's displays makes running games at native resolutions more demanding than monitors designed for PC gaming.

**What about my pre-2019 MacBook Pro?** If your Mac has Thunderbolt 3 ports (e.g. [late-2016](https://everymac.com/systems/apple/macbook_pro/specs/macbook-pro-core-i5-2.0-13-late-2016-retina-display-no-touch-bar-specs.html) or later), you'll be able to figure out a way to make it work, but with an increased amount of futzing for each year you go back. I initially set all this up with a [mid-2017](https://everymac.com/systems/apple/macbook_pro/specs/macbook-pro-core-i5-2.3-13-mid-2017-retina-display-no-touch-bar-specs.html) MacBook Pro, but wound up spending six or seven hours applying various salves and incantations to try to work around "[Windows Error 12](https://egpu.io/forums/pc-setup/2016-macbook-pro-solving-egpu-error-12-in-windows-10/)", which is the nonsense Device Manager will spew when Windows can't figure out how to get sufficient bandwidth and memory addressed to use the eGPU.

Ok, with that out of the way. Let's see what it looks like to set this all up.

## Step-by-step instructions

At the risk of being too verbose, I've decided to document literally every little step of the process I took in setting things up, because even minor gaps I found in other people's builds online would often mask tremendous complexities that took me hours to figure out on my own.

### Assembling the eGPU

Start by unboxing your GPU and eGPU enclosure.

So, here's a Radeon VII card:

![Radeon VII card](/uploads/IMG_4111.jpg)

And here's a Razer Core V2 eGPU enclosure:

![A Razer Core V2 eGPU enclosure](/uploads/IMG_4113.jpg)

Razer's eGPU models have a simple handle locking mechanism that makes it trivially easy to get at the PCI slot and release or mount a card. Mounting a card is pretty easy: just remove the I/O plate facade, push the card's pins into the slot, and connect the two power cables into the top of the card. It'll look like this before you slide it back into place:

![A Radeon VII card seated inside the PCI slot of a Razer Core V2](/uploads/IMG_4112.jpg)

If you opt for the cheaper, quieter, larger Razer Core X, here's an idea of the size difference:

![a large Razer Core X and a small Razer Core V2 sitting side by side](/uploads/IMG_4114.jpg)

And finally, here's what it all looks like when thrown onto a desk with a monitor and a keyboard:

![monitor, keyboard, mouse, eGPU, and closed MacBook Pro](/uploads/IMG_4122.jpg)

The eGPU ships with a hilariously short 1 foot cable, so you'll want to reach for an active 2 meter cable as soon as possible.

### Setting up macOS

This one's easy: update macOS to the current release version, which (as of this writing) is 10.14.5. If you're on that version or newer, just plug the eGPU enclosure into a power outlet and connect it to the computer, and you should immediately see it recognized in the "About This Mac" view:

![macOS About This System dialog, showing version 10.14.5](/uploads/Screen Shot 2019-06-12 at 9.55.41 PM.png)

And that's it. On macOS, this is all truly plug-and-play. If you have any games that run on macOS, they should be able to immediately take advantage of the eGPU.

If you have certain apps that need an extra push to use that GPU, you can tell macOS to present only that GPU to them via the application's "Get Info" dialog in Finder:

_TODO_ 

And, while it's said that you can "hot" plug an eGPU at any time while running the computer, I think it'd be more fair to say you can merely "warm" unplug it. If you unplug the eGPU without giving macOS a chance to restart any applications currently using it, those apps will crash and macOS will yell at you. So, 