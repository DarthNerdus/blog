---
layout: text
title: "VPS Showdown"
date: 2009-09-22
---

*Updated 2009/09/22.*

A while back on the [macsb][macsb] mailing list there was some discussion about hosting and which VPS provider was the best for a developer's typical needs. The two competitors that rose out of the discussion were [Linode][linode] and [Slicehost][slicehost]. I've used both and decided it would be good of me to post a more comprehensive guide, this is the result.

In essence, the difference between these two companies is their *feel*.

**If you like to tinker, Linode gives you everything you need.
If you rather a defined, slick experience, Slicehost is for you.**

## Location

Server location doesn't matter as much as it used to, at least when you're discussing US-based traffic. So while this is a largely unnecessary area of their services, it does matter to some and for that reason I've included it.

Slicehost | Linode
:-:|:-:
Dallas, TX | Dallas, TX
St. Louis, MO | --
-- | Atlanta, GA
-- | Newark, NJ
-- | Fremont, CA

From what I saw, Slicehost provides no way to choose where your Slice (that is, the VPS) is provisioned. Linode, on the other hand, let's you choose when first setting up the Node (that's what Linode calls them). Linode also lists their current availability on their [website][avail].

Both companies will move your VPS via a support request.

## Distributions

Almost all VPS hosts provide a variety of Linux distributions to choose from, it's just a matter of selection.

Distribution | Slicehost | Linode
-|:-:|:-:
Arch Linux 2009.02 | Yes | Yes
CentOS 5.3 | Yes | Yes
CentOS 5.2 | Yes | Yes
Debian 5.0 | Yes | Yes
Debian 4.0 | -- | Yes
Fedora 11 | Yes | Yes
Fedora 10 | Yes | --
Fedora 9 | -- | Yes
Gentoo 2008.0 | Yes | Yes
Gentoo 2007.0 | -- | Yes
OpenSUSE 11.0 | -- | Yes
Slackware 12.2 | -- | Yes
Ubuntu 9.04 | Yes | Yes
Ubuntu 8.10 | Yes | Yes
Ubuntu 8.04.2 LTS | Yes | Yes

Slicehost now offers RedHat EL (currently 5.3) for a monthly charge. This is a *huge* step-up over Linode for users who require RH Enterprise Support.

Linode also allows you to (somewhat) easily install any [custom][customhowto] system, that is really powerful.

**[Addendum]** -- Something I forgot to put in here, but I noticed when Slicehost announced it. Both providers offer kernel select from within their respective managers.

## 32 or 64-bit? Does it matter?

On the same track as distributions, I should point out that Linode offers both i386 (32-bit) and x86_64 (64-bit) versions of their distributions while Slicehost only offers the latter. This doesn't make much of a difference, but on a smaller VPS setup (with less RAM), it could be an issue. For the fully skinny on how this might affect you, check out this [awesome article][davidnwelton] by David Welton.

## Bandwidth, IP addresses, and High-Availability

Bandwidth obviously varies by pricing plan, which will be looked at later. But generally speaking, when comparing Slicehost and Linode plans side-by-side, Linode offers more bandwidth of Slicehost at equivalent pricing tiers.

Both Linode and Slicehost give 1 dedicated IP address for each VPS, with more purchasable. (You must provide proper justification when applicable.)

Both parties offer private IP addresses for unmetered bandwidth (in the same data-center). Linode offers this immediately upon setting up your Node, Slicehost will accommodate you receiving a support request.

Both companies offer in-depth guides to achieving high-availability / IP-failover.

## Want to grow?

Growth typically leads to one of two desires when dealing with a VPS. Either make more of them or make it bigger.

Both providers offer a service where you just "click a button" and their systems will take your VPS down, make a larger one, and copy it over in the same exact state. You simply have to pay the higher price.

Both services providers allow you to "clone" existing systems to create additional copies.

## Mission Control

Linode has a rather [advanced][linodepanel] control panel compared to Slicehost's [SliceManager][slicemanager]. It just comes down to how fine-tuned you want your setup to be.

With Slicehost, you are given a premade box with a swap, a disk (based on plan), and the OS installed and setup.

Linode takes a more technical approach. While they do provide a [wizard][linodewizard] that will automate the deployment process, you actually can make multiple boot profiles, and cut up and setup your disk space into however many images you like. This can be quite powerful and even allows you to install a custom OS if you want to get your hands dirty.

## Lish

Linode also offers another method on control.

Lish is a shell that you can SSH into that gives you complete control over your server. It's primary tool is to give you console access to your node (rather than an Ajax page)... but you can do much, much more. It can essentially give you all the essential tools that you normally have to go to the web panel for, in one concise tool.

To really realize how handy this is, you should just view the [documentation][lish].

## Rescue 911!

We've all reached that point where we realize we shouldn't have entered that command, or changed that network configuration, or done whatever it was that crashed your box. The point is, it happens. Being able to recover from such a situation is what matters.

Linode has this nice little shutdown "watchdog" named Lassie (Linode Autonomous System Shutdown Intelligent rEbooter) who will automatically reboot your server if it died unexpectedly (that is, you don't set a proper shutdown via Lish or the control panel). This could make or break your day (or night) while you're away from your computer.

Both companies offer recovery consoles to allow you to control the server directly in case of emergency.

## Price point

For some people, it really comes down to this... a pricing comparison. I should point out that Linode has many more pricing tiers, but Slicehost has larger options.

VPS | Price (Mo) | RAM | Disk Space | Bandwidth
-|:-:|:-:|:-:|:-:
Linode 360 | $19.95 | 360MB | 16GB | 200GB
256 Slice | $20.00 | 256MB | 10GB | 100GB
Linode 540 | $29.95 | 540MB | 24GB | 300GB
512 Slice | $38.00 | 512MB | 20GB | 200GB
Linode 720 | $39.95 | 720MB | 32GB | 400GB
Linode 1080 | $59.95 | 1080MB | 48GB | 600GB
1GB Slice | $70.00 | 1024MB | 40GB | 400GB
Linode 1440 | $79.95 | 1440 MB | 64GB | 800GB
2GB Slice | $130.00 | 2048MB | 80GB | 800GB
Linode 2880 | $159.95 | 2880MB | 128GB | 1600GB
4GB Slice | $250.00 | 4096MB | 160GB | 1600GB
8GB Slice | $450.00 | 8192MB | 320GB | 2000GB
15.5GB Slice | $800.00 | 15872MB | 620GB | 2000GB

As you can see, Linode typically gives you more for your money - though I am unable to gain concrete information regarding their private "high-end" dealings.

## And finally...

*The Community.*

Both companies having thriving communities surrounding them, though Linode is generally less mainstream and therefore less known.

Slicehost has a nice-sized IRC channel as well as a Campfire [chat room][slicechat]. You can hear people discussing Slicehost on Twitter often enough and many well known services run off Slicehost.

Linode is more tight-knit in my experience. They have an IRC channel hosted on OFTC which is lively throughout the day. There are a lot of regulars there that will help anyone who has a problem, or just geek out with you.

## In Summary

It all comes back to the feel. Linode can offer you more if you like to pull the levers and push the buttons, but Slicehost will offer you a more controlled experience, which is quite enjoyable. In the end, I'd say it's mostly a matter of preference.

[macsb]: http://tech.dir.groups.yahoo.com/group/macsb/message/14097
[linode]: http://www.linode.com/?r=298003406fff3692808e3e90f40f71256b02eb49
[slicehost]: http://slicehost.com/
[avail]: https://www.linode.com/avail.cfm
[linodepanel]: https://www.linode.com/features.cfm
[slicemanager]: http://articles.slicehost.com/2007/10/30/slice-management
[linodewizard]: https://www.linode.com/images/sshots/distrowiz.png
[customhowto]: http://thegrebs.com/docs/linode_distro.html
[pvgrub]: http://www.linode.com/wiki/index.php/PV-GRUB
[camp]: http://campfirenow.com/
[slicechat]: http://chat.slicehost.com/
[lish]: https://www.linode.com/wiki/index.php/Lish
[davidnwelton]: http://journal.dedasys.com/2008/11/24/