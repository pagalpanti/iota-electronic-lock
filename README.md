# iota-electronic-lock
A electronic lock POC(Proof of Concept) powered by IOTA

## Hardware requirements
* Raspberry Pi 3 (Model B)
* microSDHC 32 GB

## Installation

#### Installng operating system images into Raspberry Pi

* Get Rasbian stretch lite [image](https://downloads.raspberrypi.org/raspbian_lite_latest)
* Copy operating system image into microSDHC
  * `sudo unzip -p 2018-03-13-raspbian-stretch-lite.zip | sudo dd of=/dev/mmcblk0 bs=4M conv=fsync`

#### Set wifi on Raspberry Pi
* Mount the **boot** partition
  * touch ssh /mount_point/boot/
  * vim /mount_point/boot/wpa_supplicant.conf
    
    ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev

    update_config=1

    country=<your_ISO-3166-1_two-letter_country_code>
    
    network={
        ssid="<your_SSID>"
        psk="<your_PSK>"
        key_mgmt=WPA-PSK
    }
    

#### Login
* Default account/password
  * pi/raspberry

#### Installing swarm-like node
* Update apt list:
  * `$ sudo apt-get update`

* Pre-Installation:
  * `sudo apt-get install git`
  * `sudo apt-get install python-pip python-setuptools python-dev python3-dev build-essential libssl-dev libffi-dev`

* Official Python library for the IOTA Core:
  * `$ pip install pyota`
    * Know issue: [TypeError: unsupported operand type(s) for -=: 'Retry' and 'int'](https://stackoverflow.com/questions/37495375/python-pip-install-throws-typeerror-unsupported-operand-types-for-retry)

* IOTA transaction POW utilities:
  * `$ git clone https://github.com/chenweiii/dcurl.git`
  * `$ cd dcurl/`
  * `$ make check (https://github.com/chenwei-tw/dcurl/issues/40)`

* Install iota-swarm-like-node:
  * `$ pip2.7 install cryptography==2.1.4`
  * `$ git clone https://github.com/yillkid/iota_swarm_like_node.git`
  * `$ cd iota_swarm_like_node/`
  * `$ python server.py`

#### TODO:
* https://github.com/chenwei-tw/dcurl/issues/40
* Electronic lock POC 

Follow the link [INSTALLING OPERATING SYSTEM IMAGES ON LINUX](https://www.raspberrypi.org/documentation/installation/installing-images/linux.md) on RaspberryPi official website for detail.
