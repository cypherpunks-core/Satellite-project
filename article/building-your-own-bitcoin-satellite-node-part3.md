# Building Your Own Bitcoin Satellite Node: Part 3 — Dish Alignment

[![Go to the profile of grubles](https://cdn-images-1.medium.com/fit/c/50/50/1*HJnte-5kKYCBJwFE99iYYQ.jpeg)](https://hackernoon.com/@notgrubles?source=post_header_lockup)

[grubles](https://hackernoon.com/@notgrubles)

Sep 18, 2017

![](https://cdn-images-1.medium.com/max/800/1*4thvtylgOoJVdkVpr0paUg.jpeg)

\o/

At this point you should have your dish assembled and the required software installed. You can, and should, copy over an already-synced Bitcoin blockchain to your Sat Node. Blockstream Satellites rebroadcast the last 24 hours of blocks, so don’t worry about having to hurry. Time to align your dish!

### Requirements:

* An assembled dish and correctly connected cabling as per [Part 1](https://medium.com/@notgrubles/building-your-own-bitcoin-satellite-node-6061d3c93e7)
* Requisite software installed as per [Part 2](https://medium.com/@notgrubles/building-your-own-bitcoin-satellite-node-part-2-software-installation-a94a0b85d089)
* Clear line-of-sight to the satellite
* Your LNB’s LO frequency (mine was printed on the box the LNB arrived in)
* (Optional) Smartphone dish alignment app

*For reference, here are the previous parts of this guide:*

[ **Building Your Own Bitcoin Satellite Node**
*A layman’s guide* medium.com](https://medium.com/@notgrubles/building-your-own-bitcoin-satellite-node-6061d3c93e7)

[ **Building Your Own Bitcoin Satellite Node: Part 2 — Software Installation**
*Note: While there is a Part 1 — Hardware Assembly, it is not required for Part 2 — Software Installation. You can skip…* medium.com](https://medium.com/@notgrubles/building-your-own-bitcoin-satellite-node-part-2-software-installation-a94a0b85d089)

### Determining the proper satellite to align to

*Note: For this guide we will use Galaxy 18.*

Blockstream currently has four satellites broadcasting Bitcoin blocks to North and South America, Africa, and Europe. To determine which satellite provides the best coverage for your area, refer to the Network Status page here:

https://blockstream.com/satellite/#satellite_network-coverage

There is also a Dish Alignment Tool you can use to input your address and receive what elevation, azimuth, and polarity you need to receive data from the satellite.

https://blockstream.com/satellite/#satellite-resources

### Attaining line-of-sight

To get a rough visualization of my line-of-sight to Galaxy 18, I used the [SatellitePointer iOS app](https://itunes.apple.com/us/app/satellite-pointer-align-your-dish/id994565490?mt=8).

Make sure you have no buildings, trees, or structures within 30 degrees of your line-of-sight. An example of a good line-of-sight:

![](https://cdn-images-1.medium.com/max/800/1*IMsWsqIv3iqWNpbfK_kELg.png)

The better and less-obstructed line-of-sight you have, the better your signal will be:

![](https://cdn-images-1.medium.com/max/800/1*BMcGVwWidPr6JBXPudgJxg.jpeg)

### Setting your dish’s azimuth and elevation

Once you have determined an area with good line-of-sight, you can begin setting the azimuth (side-to-side movement) and elevation (up and down angle) of your dish. The dish used in this guide is known as an “[offset](https://en.wikipedia.org/wiki/Offset_dish_antenna)” dish. What that means to us is to use the dish’s own angle measurement to set the elevation versus relying on a protractor or smartphone app.

![](https://cdn-images-1.medium.com/max/800/1*zpi9MlO_LJnx_hWCcy1tNw.jpeg)

The quality of signal you will receive is very sensitive to the angle of elevation, so make sure you are setting it as accurately as possible.

Once you believe you have accurately set the dish’s elevation, move on to setting the LNB polarity.

### Setting the LNB’s polarity

Setting the polarity of the LNB is a little tricky. I used the SatellitePointer iOS app to help with this. I fit the top of my smartphone under the flat part of the LNB (painted red) and then tried to get an accurate reading from the app:

![](https://cdn-images-1.medium.com/max/800/1*3aygedg9M8Daq1tqbt_7Fw.jpeg)

![](https://cdn-images-1.medium.com/max/800/1*yL_dqQgaCeItFaFDVx4Xcg.png)

close!

There are also degree markings on the top of the LNB, but I found using the smartphone app was easier.

### Using the Blockstream Satellite Receiver to fine-tune alignment

A prerequisite of launching the Receiver is to determine what frequency to pass to  `rx_gui.py`  . You should have figured out the frequency of the satellite you want to receive from previously in this guide. Galaxy 18’s frequency is 12022.85 MHz.

To calculate the frequency to pass to  `rx_gui.py`  , you subtract your  *LNB’s LO frequency*  from the satellite frequency. The LNB used in this guide has an LO frequency of 10750 MHz. Thus, the result is 1272.85 MHz.

`rx_gui.py`  accepts frequency in Hz (instead of MHz), so the result is 1272850000 Hz.

Now, you can pass the frequency and gain (40 is fine) to  `rx_gui.py`  and run it:

`python rx_gui.py --freq 1272850000 --gain 40`

`rx_gui.py`  is located in the  `satellite/grc`  directory we cloned from the Blockstream Satellite repository in Part 2 of this guide. Mine is located at:  `/home/grubles/satellite/grc/`

#### Working with the Receiver GUI

When you start  `rx_gui.py`  a window will pop up with numerous tabs. What we want to do is use the  `FFL In` tab:

![](https://cdn-images-1.medium.com/max/800/1*2R4ODdqRMDNW-gNRQNkFVw.png)

no signal yet!

This graph is very noisey and updates quickly. To help with this you can set the graph to average its updates to get a clearer visualization of the quality of your signal:

![](https://cdn-images-1.medium.com/max/800/1*CzhMMXvWHVfOsJxyeCRYxw.png)

15 should do the trick

### Sweeping and setting the dish’s azimuth

At this point your graph will be more or less flat. Now we can focus on setting the azimuth correctly. Slowly sweep left to right and back while watching the  `FFL In` tab. I used the previously mentioned iOS app to help with setting the azimuth:

![](https://cdn-images-1.medium.com/max/800/1*h0WjzbkGLN1b6hKdEdgnsw.png)

close!

![](https://cdn-images-1.medium.com/max/800/1*FWOKWJnIaVzmBAKQKi93ZQ.jpeg)

If you are successful, you will see a lump in the graph similar to this but not necessarily as clear:

![](https://cdn-images-1.medium.com/max/800/1*hv5_MGQ8NtmLDuiKwGcA7w.png)

Nice! Now you can adjust the azimuth (side to side), elevation (up/down), and polarity of your LNB to get a bigger “lump”, and therefore a better signal.

The objective is to have a clear lump similar to this:

![](https://cdn-images-1.medium.com/max/800/1*h6GhQYzNLIL3lTBWRRWsBA.png)

To confirm your signal is good, you can click on the  `Abs PMF Out`  tab and see a single large peak:

![](https://cdn-images-1.medium.com/max/800/1*ePbEE3VbVPOK7-3e9j1tcQ.png)

You can also click over to the  `Costas Sym Out`  tab and see four groupings of dots:

![](https://cdn-images-1.medium.com/max/800/1*6SzHaJmdYBKwH70DgGV5vA.png)

Finally, the terminal where you are running  `rx_gui.py`  will print out:

`#### Frame synchronization acquired ####`

Congrats! You’ve successfully aligned your dish to the Blockstream Satellite!

![](https://cdn-images-1.medium.com/max/800/1*0J0Um2L0VmKzM44j7n3s9Q.gif)

time to uncork that 50 pound champagne bottle you’ve been storing for years

### Starting FIBRE (  `bitcoind`  )

Now that we are successfully aligned to the satellite, we can start  `bitcoind` and receive blocks from the Blockstream Satellite!

`$ bitcoind -fecreaddevice=/tmp/async_rx`

You can now follow the  `debug.log`  to see if you’re receiving blocks successfully. If you see something similar to:

2017–09–17 20:41:39 UDP: Got full header and shorttxids from [::]:2 2017–09–17 20:41:42 UDP: Initialized block 0000000000000000008961eb7ce04e56c0d6dec5b6e92a3e4298b7614d762f83 with 0/867 mempool-provided chunks (or more)

…then you are all set! Congratulations!

![](https://cdn-images-1.medium.com/max/800/1*_hohBwLSywFiAPcxopuWUg.gif)

actual footage of me when I got all this working for the first time

Now, you can turn off (or keep turned off) networking to your device and only receive blocks from the satellite or you can stay networked. It’s up to you!

This concludes Part 3 of the Building Your Own Bitcoin Satellite Node guide. A special thanks to Chris Cook at Blockstream for walking me through setting my sat node up, and also to Greg Maxwell for informing me of such a cool and exciting application of technology.

For a more in-depth guide visit: https://github.com/Blockstream/satellite

If you found this guide helpful you can spend tips to `3KQFQptqczxfXfWKwTxDw7iwifrf96axuG`

Thanks for reading!

-grubles