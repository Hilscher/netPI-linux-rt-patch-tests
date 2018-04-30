## Linux RT patch tests

Made for [netPI](https://www.netiot.com/netpi/), the Open Edge Connectivity Ecosystem

### Debian Stretch with Linux real-time kernel patch tests

The image provided hereunder deploys a container with installed Debian Stretch, SSH server and Linux RT patch tests. All netPI kernels are patches with real time features ([RT-patch](https://wiki.linuxfoundation.org/realtime/start)). It is possible to use all these RTOS extending functions also within this container. Read the original RT documentations [here](https://wiki.linuxfoundation.org/realtime/documentation/technical_basics/start) for more informations about the RT capabilities.

Base of this image builds a tagged version of [debian:stretch](https://hub.docker.com/r/resin/armv7hf-debian/tags/) with enabled [SSH](https://en.wikipedia.org/wiki/Secure_Shell) and created user 'root' and [RT-Tests](https://wiki.linuxfoundation.org/realtime/documentation/howto/tools/rt-tests#compile-and-install). 

#### Container prerequisites

##### Port mapping

For remote login to the container across SSH the container's SSH port `22` needs to be mapped to any free netPI host port.

#### Getting started

STEP 1. Open netPI's landing page under `https://<netpi's ip address>`.

STEP 2. Click the Docker tile to open the [Portainer.io](http://portainer.io/) Docker management user interface.

STEP 3. Enter the following parameters under **Containers > Add Container**

* **Image**: `hilschernetpi/netpi-linux-rt-patch-tests`

* **Port mapping**: `Host "22" (any unused one) -> Container "22"` 

* **Restart policy"** : `always`

STEP 4. Press the button **Actions > Start container**

Pulling the image from Docker Hub may take up to 5 minutes.

#### Accessing

The container starts the SSH service automatically. The RT tests are precompiled and ready for a manual test in the console.

Login to it with an SSH client such as [putty](http://www.putty.org/) using netPI's IP address at your mapped port. Use the credentials `root` as user and `root` as password when asked and you are logged in as root user `root`.

As example use the command [cyclictest](https://wiki.linuxfoundation.org/realtime/documentation/howto/tools/cyclictest) starting a measure of a high resultion timer and its latency. See in the last row of its output a latency time of 100usec in maximum, independent of what is running on netPI in other containers. So applications needing an accurate timer of below 500usec should be safe.

#### Tags

* **hilscher/netPI-linux-rt-patch-tests** - non-versioned latest development output of the master branch. Can run on any netPI system software version.

#### GitHub sources
The image is built from the GitHub project [netPI-linux-rt-patch-tests](https://github.com/Hilscher/netPI-linux-rt-patch-tests). It complies with the [Dockerfile](https://docs.docker.com/engine/reference/builder/) method to build a Docker image [automated](https://docs.docker.com/docker-hub/builds/).

View the license information for the software in the Github project. As with all Docker images, these likely also contain other software which may be under other licenses (such as Bash, etc from the base distribution, along with any direct or indirect dependencies of the primary software being contained).
As for any pre-built image usage, it is the image user's responsibility to ensure that any use of this image complies with any relevant licenses for all software contained within.

To build the container for an ARM CPU on [Docker Hub](https://hub.docker.com/)(x86 based) the Dockerfile uses the method described here [resin.io](https://resin.io/blog/building-arm-containers-on-any-x86-machine-even-dockerhub/).

[![N|Solid](http://www.hilscher.com/fileadmin/templates/doctima_2013/resources/Images/logo_hilscher.png)](http://www.hilscher.com)  Hilscher Gesellschaft fuer Systemautomation mbH  www.hilscher.com
