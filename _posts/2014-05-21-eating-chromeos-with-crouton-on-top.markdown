---
layout: post
title:  "Eating Chrome OS with Crouton on Top"
date:   2014-05-21
categories: dev-environment tweaks
---

I have loved my 17" MPB for many years, but it is not practical to lug everywhere you go in the summer if you value your spine. As luck would have it, I have recently come to posess a [ChromeBook Pixel][pixel]- a ridiculously pretty hunk of relatively decent hardware topped with a high-resolution capacitive touch display. 

![The Pixel is Very Pretty]({{site.url}}/assets/pixel_large.jpg)

There are a lot of [haters][hater]. The Chrome OS is a relatively young system, with an interface that is delightfully simple for non-technical folk and perhaps disturbingly simple and locked-down for the more tech-inclined. Personally, I would be fine using it primarily as a web app and general surfing machine, were it not for the fact that I am taking this Back End Web Development class. Thankfully, there are a few methods for running linux on a ChromeBook, most of them created by Google employees.

Because I'm a total noob, I opted for what most people online consider to be the simplest option: [Crouton][crouton]. Rather than having to contend with some dual-boot malarky, crouton takes an ubuntu distro and nestles it adorably on top of the Chrome OS kernel, allowing 1-second switching between each OS. 

Admittedly, it took nearly 6 hours for me to set up the damn thing to work with the Pixel's insanely high-res display, mostly due to me being new to ubuntu, but also because ubuntu support for high-res is spotty. I ended up going with this configuration:

* Distro: Trusty. At the time of this writing it is the latest distro that crouton supports
* Desktop environment: [KDE][kde-desktop]. This guy was the only one I could find that looks half-way decent on the Pixel.
* I had to create a startup script that sets the resolution to 1680x1120 because otherwise everything is far too tiny to see. This is actually courtesy of crouton:

{% highlight ruby %}
	setres 1680 1120
{% endhighlight %}

* Font DPI is set to 124, and all system font sizes to 8 or 9.

All in all its a little fiddly. Part of me is worried we will need to do something in class that is simply not supported in this kind of environment, but so far so good.

[pixel]: http://www.google.com/intl/en-US/chrome/devices/chromebook-pixel/
[hater]: http://gizmodo.com/5986031/every-reason-not-to-buy-the-google-chromebook-pixel
[crouton]: https://github.com/dnschneid/crouton
[kde-desktop]: http://www.kubuntu.org/