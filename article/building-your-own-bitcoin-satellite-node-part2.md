# Building Your Own Bitcoin Satellite Node: Part 2 — Software Installation

[![Go to the profile of grubles](https://cdn-images-1.medium.com/fit/c/50/50/1*HJnte-5kKYCBJwFE99iYYQ.jpeg)](https://medium.com/@notgrubles?source=post_header_lockup)

[grubles](https://medium.com/@notgrubles)

Aug 25, 2017

![](https://cdn-images-1.medium.com/max/1200/1*NWyyeO2M5WdR8OHspzW0_g.png)

*Note: While there is a*  [ *Part 1 — Hardware Assembly* ](https://medium.com/@notgrubles/building-your-own-bitcoin-satellite-node-6061d3c93e7) *, it is not required for Part 2 — Software Installation. You can skip over Part 1 if you are waiting for your parts to arrive.*

### Software requirements:

* Fedora 26  `.iso`  image
* [GNURadio](https://www.gnuradio.org/) version 3.7.10+ (Fedora 26 has 3.7.11 in its software repository)
* [gr-osmosdr](https://github.com/osmocom/gr-osmosdr) (available in Fedora repo)
* [Bitcoin FIBRE](http://bitcoinfibre.org/) (we will build this ourselves)
* Miscellaneous dependencies (available in Fedora repo)

#### Other requirements:

* Ability to follow instructions / will to learn
* Moderate Linux command line utility knowledge

### Installing Fedora 26:

Since the Fedora Project already has very nice installation documentation, I will link to that versus recreating it here:

[ **5.4. Installing in the Graphical User Interface**
*The graphical installation interface is the preferred method of manually installing Fedora. It allows you full control…* docs.fedoraproject.org](https://docs.fedoraproject.org/en-US/Fedora/26/html/Installation_Guide/sect-installation-graphical-mode.html)

***Note: Make sure to mark yourself as “Administrator” during the install.***

**You will need the**  `.iso`  **in order to install Fedora. It is located here:**

https://getfedora.org/en/workstation/download/

**To transfer the**  `.iso`  **to a USB drive, you can use Unetbootin if you are using Windows:**

http://unetbootin.github.io/

### Updating Fedora:

Since we will be using the terminal to run commands, now is a good time to find and open the terminal application. Click on “Activities” located on the top left of your screen, type “terminal”, and click on the terminal icon:

![](https://cdn-images-1.medium.com/max/800/1*j4kKFjRy1Cw0bYoZQvMjaA.png)

#### Using  `dnf`  to update your install:

Once you have a terminal open, type in  `sudo dnf update`  and input the password you provided during the Fedora installation. You will be presented with a list of packages to update and a  `Is this ok [y/N]:`  prompt. Type in  `y`  .  *Note: This step should take a few minutes.*

![](https://cdn-images-1.medium.com/max/800/1*YmbA2MPi0hY07Svl3K6nTA.png)

Once the update is finished, go ahead and reboot.

### Installing GNUradio, gr-osmosdr, and their dependencies:

Thankfully,  `gr-osmosdr`  and a version of  `gnuradio`  that we can use (3.7.11) are easily installed with Fedora’s package manager  `dnf`  .

In your terminal, type:

`$ sudo dnf install gnuradio gnuradio-devel gr-osmosdr`

And input  `y`  when prompted with  `Is this ok [y/N]:`

![](https://cdn-images-1.medium.com/max/800/1*L7aVr_d4a0yPPEYnIyzUoQ.png)

Once that is finished, we can move on to cloning the Blockstream Satellite Github repository onto our local machine and building the project.

### Building Blockstream Satellite Receiver:

At this point, we want to start installing the software we need to build Blockstream Satellite Receiver:

`$ sudo dnf groupinstall "C Development Tools and Libraries"`

`$ sudo dnf install cppunit-devel swig`

Once you’ve installed those packages, you can clone the Github repository:

`$ git clone https://github.com/Blockstream/satellite`

Move to the cloned repo:

`$ cd satellite/`

Now we should have all the dependencies we need to successfully build the gr-framers GNUradio modules. Start the build by executing the install script:

`$ ./install_gr_framers.sh`

Input your password when prompted:

![](https://cdn-images-1.medium.com/max/800/1*saVCzQb0l2dyZmv3PEZ45A.png)

Building gr-framers

Congrats. You’ve built the gr-framers GNUradio modules!

Now, execute the Blockstream GNUradio module install script:

`$ ./install_mods.sh`

![](https://cdn-images-1.medium.com/max/800/1*76SzkHsNj4kBxH_SMuxpWw.png)

Building Blockstream modules

Once that is finished, you have built the Blockstream modules successfully.

We need to now set our PYTHONPATH and LD_LIBRARY_PATH in order for the Receiver to work properly:

`$ echo "export PYTHONPATH=/usr/local/lib64/python2.7/site-packages" >> ~/.profile`

`$ echo "export LD_LIBRARY_PATH=/usr/local/lib64" >> ~/.profile`

`$ source ~/.profile`

Ok, great! Everything for GNUradio should be properly setup at this point.

### Building Bitcoin FIBRE:

Let’s install the dependencies for building FIBRE:

`$ sudo dnf install openssl-devel libevent-devel libdb4-devel libdb4-cxx-devel`

![](https://cdn-images-1.medium.com/max/800/1*2LCOFERILShdJa6l3O5_gw.png)

Installing remaining dependencies for building FIBRE

Now, clone the FIBRE repo:

`$ git clone https://github.com/bitcoinfibre/bitcoinfibre`

Move into the repo’s directory:

`$ cd bitcoinfibre/`

Begin the build process:

`$ ./autogen.sh`

`$ ./configure`

Now, build FIBRE:

`$ make`

*(you can add*  `-jn`  *here to speed up compilation.*  `n`  *being the number of cores your processor has. For example, if you have a quad-core processor the command would be*  `make -j4` *)*

![](https://cdn-images-1.medium.com/max/800/1*3o-H6pSuizHfbBhmlhJTvg.png)

Hurray! It built.

Once that is finished (it should take a few minutes), you can install it:

`$ sudo make install`

![](https://cdn-images-1.medium.com/max/800/1*_53t1YR4fMIw4j_Md7PM3Q.png)

FIBRE is now installed!

FIBRE is now installed! You can now fire up  `bitcoind`  and start syncing, or copy over the blockchain from a node that is already synced.

At this point we should have everything we need to start aligning our dish to the satellite appropriate for our geolocation. If you skipped over [Part 1 — Hardware Assembly](https://medium.com/@notgrubles/building-your-own-bitcoin-satellite-node-6061d3c93e7) because your parts have not arrived, you should take a moment to read it.

This concludes Part 2 — Software Installation. [Part 3 consists of using Gnuradio to align your dish and start receiving blocks from a Blockstream Satellite!](https://hackernoon.com/building-your-own-bitcoin-satellite-node-part-3-dish-alignment-1306b4c21326)

A special thanks to Chris Cook at Blockstream for walking me through setting my sat node up, and also to Greg Maxwell for informing me of such a cool and exciting application of technology.

For a more in-depth guide visit: https://github.com/Blockstream/satellite

Thanks for reading!

-grubles