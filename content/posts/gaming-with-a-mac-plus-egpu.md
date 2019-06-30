---
title: How to cram a gaming GPU into your MacBook
date: 2019-06-15T19:54:53.000+00:00
draft: true

---
## …or, the next best thing

## How we got here

After Apple released its (soon-to-be) previous generation Mac Pro, it probably didn't take long for them to realize they had a trash can fire on their hands, especially with [regard to GPU performance](https://marco.org/2019/06/09/apple-is-listening). When Apple announced eGPU support for macOS in 2017's [High Sierra release](https://web.archive.org/web/20170731114535/https://www.apple.com/macos/high-sierra-preview/), it was hard not to see the announcement as anything more than an admission that Apple's top-of-the-line desktops and notebooks shipped with subpar GPUs due to their severe thermal constraints. Of course, the Mac has always lagged behind Windows in GPU availability and support, because Apple has never considered AAA gaming to be an important function of its product. But by 2017 (and until the new Mac Pro tower releases this fall), the situation has been especially grim: even for workstation tasks like video encoding and 3D modeling, the internal GPUs Apple has been selling are so bad that they're driving a nontrivial number of creative professionals—a market Apple actually does care about—off its platform.

How else can you explain the absurd amount of effort it must have taken by Apple and Intel to make the following statement true in 2019: instead of putting a beefy graphics card _inside_ your computer, **you are now able to take a best-in-class GPU, seat it inside an external box, plug the into your computer, and—using a single high-bandwidth cable—push the necessary instructions to render 4K games at 60 frames per second on the card before (over the very same cable!) pushing those frames back to your notebook's built-in monitor without introducing any perceptible latency**. I've seen daily evidence of this for the last month and I gotta say: it's pretty freakin' cool. 

The idea that you'd be able to connect a GPU over a 2 meter cable and get desktop-class gaming performance out of the current crop of MacBooks Pro seems far-fetched. Even to me, as I literally play games with one. When reasonable people encounter Apple's marketing about eGPUs—which is only focused on creative professional workflows like [_modeling_ VR experiences as opposed to _experiencing_ them](https://www.youtube.com/watch?v=S48T-cOG0ks)—it would be unreasonable to make the logical leap to suppose "ah, yes, surely if I boot that computer into Windows, the eGPU enclosure would have the necessary drivers and the Thunderbolt 3 cable would have the necessary bandwidth to do render real-time games acceptably." 

And yet, AAA PC gaming is exactly what a MacBook + eGPU can do. It's just that nobody [other than Razer](https://www.razer.com/gaming-laptops/razer-core-x) is telling the market that.

## How to get started

First, everything here, I pieced together from dozens of forum posts, guides, and build data from the small-but-dedicated community at [eGPU.io](https://egpu.io). Because the very-newest Macs, eGPU enclosures, and operating system releases have made things much easier (so much so, that half the content in published guides no longer applies), I will present a stripped-down walkthrough that starts fresh with the latest operating systems and components.

**Hardware:**

* [13-inch MacBook Pro (mid-2019)](https://everymac.com/systems/apple/macbook_pro/specs/macbook-pro-core-i5-2.4-quad-core-13-mid-2019-touch-bar-specs.html)
* [AMD Radeon VII](https://www.amd.com/en/products/graphics/amd-radeon-vii) card
* [Razer Core V2](https://www.amazon.com/Razer-Core-V2-Thunderbolt-Enclosure/dp/B0791ZCH4Q) (which Razer has already discontinued in favor of the larger, cheaper [Razer Core X](https://www.razer.com/gaming-laptops/razer-core-x))
* Any certified [2 meter Thunderbolt 3 cable](https://www.amazon.com/gp/product/B01H5QF2TK/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1)
* Any TV or external monitor you want to output games to (Optional)

**Software:** 

* macOS 10.14.5 (18F132)
* Windows 10 version 1903 (18362.175)

Why an AMD card over Nvidia? Well, if I was only ever going to plug macOS ships with drivers to most AMD cards, but Nvidia card support is a tremendous pain, and zero drivers are available for their new [RTX](https://www.nvidia.com/en-us/geforce/20-series/) line)