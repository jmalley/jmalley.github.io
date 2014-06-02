---
layout: post
title:  "Barely Avoiding Disaster"
date:   2014-06-02 10:39
categories: crouton chromebook
---

Improving your computer skills these days is generally a safe proposition. Despite understandable hesitation to meddle by the non-computer-savvy, the walled gardens of modern operating systems allow us to tinker and play, without much fear of blowing up our computers. Things do get pretty dicey, however, when you make your first foray into tweaking permissions for a drive or partition. Such was the risk when I attempted to set up nano (a command line text editor), in chromeos, and pretty much converted my chromebook into a gorgeous brick.
<!--more-->
Thankfully, my setup is very forgiving as far as horrible disasters go. Just an hour before my blunder I had moved my ubuntu install to an SD card (thank the lord). And as for the rest of the machine, a quick powerwash did the trick. As uncomfortable as we all are with the idea of an OS that lives primarily in the cloud, it makes restoring your device a lot easier. 

If I hadn't moved the ubuntu chroot off the internal SSD, then I would have had a real problem. Here's what I had to do to set up crouton on the SD card. This assumes you already have a working ubuntu chroot on your internal SSD.
<ol>
<li> Insert the SD card while in chromeos. Unmount it by clicking on the little 'eject' symbol. </li>
<li> Enter your chroot and open the partition manager (I use the KDE equivalent). Format the SD card in ext4.</li>
<li> Close your chroot and remount the SD card.</li>
<li> Move your chroot. It's important that it goes in a new "chroots" dir.
 {% highlight bash %}
 sudo edit-chroot chrootname -m /media/removable/SD-Card/chroots/
 {% endhighlight %}</li>
<li> Download crouton, and let it know where the chroots are by default
 {% highlight bash %}
 sudo sh -e ~/Downloads/crouton -p /media/removable/SD-Card -u
 {% endhighlight %}</li>
<li> Start chroot with
 {% highlight bash %}
 sudo sh /media/removable/SD-Card/bin/startkde
 {% endhighlight %}</li>
 </ol>

It is [much easier][cookbook] to start from scratch with an SD, rather than move an existing chroot onto it. 

[cookbook]: http://tomwwolf.com/chromebook-14-compedium/chromebook-crouton-cookbook/