---
title: Installing a Content Blocker on iOS 9 Public Beta
description: >-
  After spending 3 weeks abroad, literally afraid of opening anything resembling
  an article in Safari, I was eager to come home, install a…
date: '2015-08-08T21:36:17.571Z'
categories: []
keywords: []
slug: /@searls/installing-a-content-blocker-on-ios-9-public-beta-a25b2b83848f
---

After spending 3 weeks abroad, literally afraid of opening anything resembling an article in Safari, I was eager to come home, install a beta operating system, and take advantage of iOS 9's now-famous content blocking API. There are a few projects on GitHub that do this, but the most evolved seems to be [Block Party](https://github.com/krishkumar/BlockParty).

Let’s try out installing a content blocker on an iPhone for ourselves. The instructions below are mostly complete and a bit inane, so it’s up to you whether you’re better off just waiting the 4–6 weeks until iOS 9 is released to the public.

First, there are some pre-requisites:

*   Install iOS 9 beta; I’m using Public Beta 3 from [beta.apple.com](https://beta.apple.com/sp/betaprogram/redemption#ios)
*   Install [Xcode 7](https://developer.apple.com/xcode/downloads/) onto a Mac (requires dev account)
*   Clone or [download a ZIP](https://github.com/krishkumar/BlockParty/archive/master.zip) of the BlockParty [repo](https://github.com/krishkumar/BlockParty)

With these in place, it’s time to open BlockParty.xcodeproj

![](https://cdn-images-1.medium.com/max/800/1*Qtay-KEjtm4ObOi-w45-fA.png)

If this is your first time launching Xcode, you’ll need to first let it install additional components, then switch the target from an iPhone 6 simulator (the default) to an iOS device, like so:

![](https://cdn-images-1.medium.com/max/800/1*FadvailpPrgwAoKAqX6mEA.gif)

After this, plug in your iPhone and its name and model icon should replace the generic “iOS Device” label:

![](https://cdn-images-1.medium.com/max/800/1*K5yc5fUzfkYrontoedI4jg.png)

Next, press Run (the familiar “Play” icon at the top-left) and you’ll be prompted whether or not you’d like to enable Developer Mode on the Mac (it’s up to you, and shouldn’t be necessary for the purpose of this task).

You’ll probably be greeted with an error that your phone is still processing symbol files, as shown below. Just wait it out until it’s completed:

![](https://cdn-images-1.medium.com/max/800/1*DLFQglTtMWrRDMeCPE-UPg.png)

When it’s finally ready, click Run again to see the next error:

![](https://cdn-images-1.medium.com/max/800/1*NsVD9RAOqmFXvPlbNqpbiQ.png)

To resolve this, first click “Fix Issue”, which will prompt you to log in to your Apple ID (you no longer need to be a member of a paid developer account, but you do need to be logged in to generate the necessary provisioning profile).

If you try again, you’ll get a similar error because these App IDs are reserved by the author of the repo. You’ll need to set your own; to do so, start by clicking the project in the left and change the bundle IDs of both targets “BlockParty” and “RediffBlock” to something unique. Here I just replaced his domain name with “com.github.searls”

![](https://cdn-images-1.medium.com/max/800/1*t-3O9JlZjPKB06iQFE4zaw.png)

Each Bundle ID you enter needs to be registered with Apple, which Xcode can do for you by pressing the “Fix Issue” button in the same editor pane:

![](https://cdn-images-1.medium.com/max/800/1*324IyWER6lgHhuMgodqIkA.png)

Now, when you click Run, you should get all the way through installing the app. The failure you see next will be a generic failure with only the message “Security”. This is because iOS 9 requires user input on the device to explicitly trust each developer that’s loaded apps onto the it.

Next, on the phone, jump into Settings -> General -> Profiles and select your Apple ID under “Developer Profiles”, then tap the “Trust” link and subsequent confirmation dialog.

Next, launch the “BlockParty” app from your home screen so that it can register itself to iOS as providing a content blocker.

Finally, in Settings -> Safari -> Content Blockers, you’ll see:

![](https://cdn-images-1.medium.com/max/800/1*AdxRFxfODcYSsX3TKkAXKQ.png)

Enable it, and you should be able to test in Safari by seeing fewer popover ads appear at a site like [iMore](http://imore.com) or [The Verge](http://theverge.com).

See, wasn’t that simple!