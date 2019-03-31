# Building Your Own Bitcoin Satellite Node: Part 1 — Hardware Assembly

[![Go to the profile of grubles](https://cdn-images-1.medium.com/fit/c/50/50/1*HJnte-5kKYCBJwFE99iYYQ.jpeg)](https://hackernoon.com/@notgrubles?source=post_header_lockup)

[grubles](https://hackernoon.com/@notgrubles)

Aug 23, 2017

![](https://cdn-images-1.medium.com/max/1200/1*gN909Ok7Ei98Fdl-Zx94NQ.png)

My mobile Bitcoin satellite downlink full node!

### Hardware requirements:

*Note: The Amazon affiliate links are just to show what parts to get. You can undoubtedly find the parts on eBay if you want to. I realize some of the parts may be sold out on Amazon at this time. This guide was written for the parts on this list.*

1. A computer with Linux installed. This guide, and my Sat Node, use [Fedora 26](https://getfedora.org/). I went with Fedora because it is free, it is compatible with the software required, and because it has a large user base. Make sure to have an i5 or a similarly performant processor: [https://amzn.to/2x6G86r](http://amzn.to/2x6G86r)
2. Ample storage space (roughly 3GB for a pruned node, 150GB+ for non-pruned)
3. *At least*  a 46cm (18") satellite dish: [https://amzn.to/2wBtPzK](http://amzn.to/2wBtPzK)
4. Software Defined Radio Interface: [https://amzn.to/2g8Nu2O](http://amzn.to/2g8Nu2O)
5. Linear Polarization PLL LNB: [https://amzn.to/2w0Zk4C](http://amzn.to/2w0Zk4C)
6. LNB Mounting Bracket: [https://amzn.to/2xgotXU](http://amzn.to/2xgotXU)
7. LNB Power Supply: https://amzn.to/2KUGouq
8. Coax Cable: [https://amzn.to/2w7N4xQ](http://amzn.to/2w7N4xQ)
9. F Connector to SMA Coax Adapter: [https://amzn.to/2gajpAh](http://amzn.to/2gajpAh)
10. Screwdriver and pliers (or similar tool) for adjusting fittings
11. *(Optional. My node uses this, but a roof mount is a better permanent option)* 3 Ft Satellite Tripod: [https://amzn.to/2w81RZm](http://amzn.to/2w81RZm)

### Other requirements:

1. Smartphone satellite alignment app and/or compass
2. Patience, some elbow grease, and the will to learn!

### Hardware assembly:

*Note: Before you mount the dish assembly to the tripod, make absolutely sure the tripod is level. If the tripod is not level, you will run into difficulties when aligning the dish.*

This image should give you a pretty good idea of how the assembly goes, sans the LNB part. We have a different LNB and LNB mounting bracket which is mounted slightly different than pictured here. The tripod requires no assembly and simply unfolds.

![](https://cdn-images-1.medium.com/max/800/1*0vsWGWSbcA4nPxH5CCb4JQ.jpeg)

#### Adjusting the tripod’s mast mount fittings:

You can fine-tune the tripod and mast’s level with the six screws pictured here (the two not-visible fittings are on the opposite side). Mine came with a bubble-level that fits on the top of the mast. A smartphone app might also work.

![](https://cdn-images-1.medium.com/max/800/1*Q2jt9PfBh5OuQnmOyxDUnw.png)

#### Fit the dish assembly to the tripod mast:

There are two bolts used to secure the dish assembly to the tripod mast, and two bolts (one shown, one on other side) used to secure the dish assembly’s elevation. Tighten all of the bolts enough to hold their position, but be able to be adjusted with a fair amount of physical effort in order for you to fine-tune the dish assembly’s azimuth and elevation.

![](https://cdn-images-1.medium.com/max/800/1*A3e_plFSwpleHCQn-Xxp9g.png)

#### Mounting the LNB bracket to the LNB support arm:

Mount the bracket on the top of the support arm and make sure it is center-aligned and not skewed left or right. Mount the LNB onto the LNB bracket as shown, but keep the screws semi-loose to allow you to adjust the LNB’s polarity while aligning. You can go ahead and connect the coax cable to the LNB at this point if you want.

![](https://cdn-images-1.medium.com/max/800/1*cZsLH4krsgeU8oBTabvjQQ.png)

### If assembled correctly, your dish antenna should look nearly identical to this!

![](https://cdn-images-1.medium.com/max/800/1*lr1M_rh5qy1zFa2FqEgnRw.jpeg)

It looks like a Lunar Module or something, right? :)

#### Connecting the cabling:

Refer to my attempt at a simple cabling chart to help you connect the SDR to the LNB power supply using the SMA to F adapter cable, and the LNB to the LNB power supply with the coaxial cable. Your power supply may have different labeling for the connections. ***If you attach the SDR to the wrong connection, you may damage the SDR. Make sure to research your own LNB power supply to know for sure where to connect everything.***

![](https://cdn-images-1.medium.com/max/1200/1*ckjJ2LstRfnoWTlu2DYTZw.png)

What a colorful mess.

This concludes Part 1 — Hardware Assembly. [Part 2 will focus on installing the necessary software to receive blocks from Blockstream Satellites.](https://medium.com/@notgrubles/building-your-own-bitcoin-satellite-node-part-2-software-installation-a94a0b85d089) Part 3 will consist of using Gnuradio to align your dish and start receiving blocks!

A special thanks to Chris Cook at Blockstream for walking me through setting my sat node up, and also to Greg Maxwell for informing me of such a cool and exciting application of technology.

For a more in-depth guide visit: https://github.com/Blockstream/satellite

If you found this guide helpful you can toss tips to

37apsFv8YTPXxc38jsXNm7hn5FUMKoggWC

(which will be beamed up to the Blockstream Satellite and down to my Sat Node)

Thanks for reading!

-grubles