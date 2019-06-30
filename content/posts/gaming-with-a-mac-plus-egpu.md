---
title: Cramming a gaming GPU into your MacBook Pro
date: 2019-06-15T19:54:53.000+00:00
draft: true

---
## …without actually doing that

## How we got here

After Apple released its (soon-to-be) previous generation Mac Pro, it probably didn't take long for them to realize they had a trash can fire on their hands, especially with [regard to GPU performance](https://marco.org/2019/06/09/apple-is-listening). When Apple announced eGPU support for macOS in 2017's [High Sierra release](https://web.archive.org/web/20170731114535/https://www.apple.com/macos/high-sierra-preview/), it was hard not to see the announcement as anything more than an admission that Apple's top-of-the-line desktops and notebooks shipped with subpar GPUs due to their severe thermal constraints. Of course,  because Apple has never considered AAA gaming to be an important function of its products, the Mac has always lagged behind Windows in GPU availability and support. But by 2017 (and until the new [Mac Pro](https://www.imore.com/mac-pro-2019-everything-you-need-know) tower releases this fall), the situation has been especially grim: even for workstation tasks like video encoding and 3D modeling, the internal GPUs Apple has been selling are so bad that they're driving a nontrivial number of creative professionals—a market Apple actually does care about—off its platform.

The world may be excited to close the door on the ill-conceived trash can Mac Pro, but if it hadn't been for its glaring design flaws, Apple and Intel probably wouldn't have prioritized the engineering needed to make running an eGPU over Thunderbolt 3 a commercial reality.

So, it's thanks to the trash can Mac Pro that in 2019, we can say: instead of putting a beefy graphics card _inside_ your computer, **you are now able to take a top-of-the-line gaming GPU, seat it inside an external box, plug that box into your computer, and—using a single high-bandwidth cable—push the necessary instructions to render 4K games at 60 frames per second on the card before (over the very same cable!) pushing those frames back to your notebook's built-in monitor without introducing any perceptible latency**. I've seen daily evidence of this for the last month and I gotta say: it's pretty freakin' cool.

The idea that you'd be able to connect a GPU over a 2-meter cable and get desktop-class gaming performance out of the current crop of MacBooks Pro seems far-fetched. Even to me, as I literally play games with one. When reasonable people encounter Apple's marketing about eGPUs—which is only focused on creative professional workflows like [_modeling_ VR experiences as opposed to _experiencing_ them](https://www.youtube.com/watch?v=S48T-cOG0ks)—it would be unreasonable to make the logical leap to say, "ah, yes, surely if I boot that computer into Windows, the eGPU enclosure would have the necessary drivers and the Thunderbolt 3 cable would have the necessary bandwidth to render games in real-time at an acceptable frame rate and input lag."

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

The eGPU ships with a hilariously short 1-foot cable, so you'll want to reach for an active 2 meter cable as soon as possible.

### Setting up macOS

This one's easy: update macOS to the current release version, which (as of this writing) is 10.14.5. If you're on that version or newer, just plug the eGPU enclosure into a power outlet and connect it to the computer, and you should immediately see it recognized in the "About This Mac" view:

![macOS About This System dialog, showing version 10.14.5](/uploads/Screen Shot 2019-06-12 at 9.55.41 PM.png)

And that's it. On macOS, this is all truly plug-and-play. If you have any games that run on macOS, they should be able to immediately take advantage of the eGPU.

If you have certain apps that need an extra push to use that GPU, you can tell macOS to present only that GPU to them by checking "Prefer external GPU" in the application's "Get Info" dialog in Finder:

![Dialog for "Prefer External GPU"](/uploads/Screen Shot 2019-06-30 at 9.40.00 AM.png)

And, while you can "hot plug" an eGPU into your machine at any time while running the computer, I think it'd be more fair to say you can merely "warm unplug" it. You're first supposed to tell macOS to force restart any apps that are currently depending on the eGPU via this menu bar option:

![Menubar option to disconnect eGPU](/uploads/Screen Shot 2019-06-30 at 9.44.18 AM.png)

If you fail to do this and yank the cable without first unmounting the eGPU, macOS will yell at you (before proceeding to force-restart most of the apps you were just running):

![macOS warning not to unplug the eGPU without unmounting it first](/uploads/Screen Shot 2019-06-30 at 9.48.27 AM.png)

And that's pretty much all there is to using an eGPU with macOS. The entire experience is so invisible and seamless that Apple's engineers deserve to be commended.

### Setting up Windows via Boot Camp

**Before you do anything else, disconnect your eGPU.** When it's safe to plug it in under Windows, I'll let you know!

This process hasn't changed much in the last 12 years. Start by [downloading Windows 10](https://www.microsoft.com/en-us/software-download/windows10).

As of mid-June 2019, the most recent downloadable version of the Windows 10 installer was the October 2018 release:

![Windows 10 download dialog](/uploads/Screen Shot 2019-06-14 at 7.25.16 PM.png)

Once downloaded, launch Boot Camp Assistant, which will download some support software, ask for the Windows image (which, if the download is complete, it may detect automatically), and prompt you to choose your partition size:

![Boot Camp assistant setup page](/uploads/Screen Shot 2019-06-14 at 7.49.01 PM.png)

Boot Camp Assistant is still finicky and on AFPS volumes will regularly report failure when attempting to partition the disk.

![boot camp partition failure](/uploads/Screen Shot 2019-06-14 at 8.25.33 PM.png)

When this happens, just quit the app, reboot, and try again. It has never not taken me at least two tries. Once it's working, you should be booted into the Windows installer:

![](/uploads/Image-1.jpeg)

The most important step is actually _not_ entering your product key (which can be done later), but ensuring you pick the edition of Windows for which you have (or want) a license. In my case, Windows 10 Pro:

![Windows Installer edition selection page](/uploads/Image 2.jpeg)

The next thing to look out for is that once Windows boots, an Apple-deployed script will run which _should_ launch the Boot Camp installer, which contains all of the drivers for your computer's various components and which you'll definitely want install immediately before rebooting:

![the Windows Boot Camp Support installer](/uploads/Image 3.jpeg)

Because each Windows release is dramatically improving its own eGPU support, before doing anything else you'll want to upgrade to the latest available stable release. For reference, I started at Windows 10 version 1809.

The most recent release at the time was 1903, but Windows 10 is especially precious about how it rolls out system updates over its install base, and actually does not expose a mechanism in the operating system to tell it "shut up, just give me the latest release". You can force-trigger a release by visiting a particular [Microsoft web page](https://microsoft.com/en-us/software-download/windows10?) and clicking "Update now", however:

![update windows 10 page](/uploads/1.jpg)

Weird.

Anyway, that'll take entirely too long to download, so go make a sandwich, I guess. I was too afraid of continuing with any configuration when those options were likely to have been affected by the latest release. So just wait for this to finish:

![windows 10 update app](/uploads/2.jpg)

Once Windows has updated itself and restarted, we want to create a System Restore Point, so that we can easily unwind any driver & configuration changes we make if we run into trouble. You can do this by hitting the windows key and searching "restore point" to open this dialog:

![Windows 10 System properties preferences](/uploads/3d.jpg)

Click "Configure" restore settings, and in the subsequent dialog box choose "Turn on system protection" (how is this not on by default?!):

![windows 10 system protection settings](/uploads/3.jpg)

Click OK, and in the previous pane, you should now be able to click "Create" a restore point:

![Windows 10 system properties after system protection has been enabled](/uploads/3e.jpg)

You'll be asked to name the restore point, and you can give it whatever name you want:

![Create a restore point dialog, named 1-initial-setup](/uploads/3f.jpg)

Next, because Windows 10's built-in attempt to locate and install GPU drivers will often interfere with the chipmakers' own software, prior to plugging in your eGPU or installing any AMD or Nvidia drivers, you actually want to _uninstall_ all GPU drivers and prevent Windows Update from attempting to install new ones. This can be done with a program called DDU which can be [downloaded here]() (I used [version 18.0.1.5]()). The website looks like every other website for software that runs on Windows:

![the DDU home page](/uploads/8.jpg)

Because the download link disappears every once few seconds on a timed carousel animation, just keep waiting until you time your click to successfully download it.

Once installed, run it and it'll complain that you're not in Windows Safe mode:

![DDU launcher](/uploads/7.jpg)

At the time of this writing and with this mix of hardware and software, it actually didn't appear to be possible to boot Windows 10 into Safe Mode under Boot Camp, so I just launched anyway.

Since I was going to install a Radeon card, I selected AMD from the dropdown box near the top-right of the UI, resulting in the app shading itself like this:

![The DDU UI after selecting AMD Radeon](/uploads/5.jpg)

From there, open the options and check the "Prevent downloads of drivers from 'Windows update'" box at the bottom of the page:

![DDU advanced options where you'll prevent downloads from Windows Update](/uploads/6.jpg)

This will prevent Windows Update from attempting to install any GPU drivers. Windows Update doesn't normally screw up GPU drivers once things are initially set up, but because you're likely going to be connecting and disconnecting a GPU with much greater regularity than you ever would on a traditional tower, and into any of 4 Thunderbolt 3 ports, the risk is much greater when working with an eGPU.

Okay, after checking "prevent downloads", close the options menu and then click "**Clean and restart**"in the top-left corner of DDU's interface. It will warn you again and you will ignore it, because you've been using Windows for two hours at this point and you've already dismissed twenty pointless warning dialogs:

![DDU warning you will ignore](/uploads/4.jpg)

When that's done, restart, hit the windows key and type "restore point" again to create a second restore point after you've run DDU but before you've downloaded your GPU's drivers:

![A second restore point named 2-post-ddu](/uploads/3b.jpg)

**Next up, you should finally plug in your eGPU!** Give Windows a minute as the eGPU warms up to detect the Thunderbolt controller. If you open Device Manager you should see a display adapter named "Microsoft Basic Display Adapter":

![Device manager](/uploads/a3.jpg)

If you check the properties of that (driverless) display adapter, they'll look like this;

![Display adapter properties](/uploads/a.jpg)

This is great! It means Windows is connecting to your eGPU enclosure's Thunderbolt 3 controller fine, and it can tell there's a GPU plugged into it.

Next, we'll want to install drivers.

* **AMD:** Go to the [downloads page](https://www.amd.com/en/support) and scroll down to download the "Auto-Detect and Install Radeon Graphics Drivers for Windows" installer
* **Nvidia:** [Download GeForce Experience](https://www.geforce.com/drivers) under "Automatic Driver Updates"

The installation process for both is dead simple and fully automated. Either will prompt you to restart Windows, but **don't click Restart**. Instead, shut down the computer entirely. Once it's off, unplug the eGPU, boot it up again, login, and plug the eGPU back in.

> **Why not restart with the eGPU connected?** The hand-wavy short version is that when Windows boots normally on a Mac with an eGPU connected, the device is initialized in such a way by the EFI boot loader so as to not work as expected. That means, by default, you'll probably need to plug in your eGPU on Windows only after each boot. (There is a way around this, but it's not pretty; I'll explain below when I talk about rEFInd.

Okay, so after you've