# Rock64-I2C-LCD-Stats
This is a project to create a python script that will work with infomration from RPi-Monitor to display the real time stats to a I2C LCD screen connected to a Rock64. This is currently being used with a 16x2 I2C LCD.

## Stats and Metrics that can be displayed
The following list is of all the stats that RPi-Monitor collects for the Rock64. These stats are part of the python script that can be configured to display then accordingly. 

* UPTIME
* TEMP
* CPU
* CPU COUNT
* 1 MIN
* 5 MIN
* 15 MIN
* UPGRADABLE PACKAGES
* SD USED
* SWAP USED
* MEM AVAIL
* MEM FREE
* TIME
* SD TOTAL
* MEM TOTAL
* SWAP TOTAL


## Setup Instructions
Follow the below sections to learn how to setup a I2C 16x2 LCD display on the Rock64 to display system stats. (I used [DietPi](https://www.dietpi.com) for this) 

### Hardware
* Rock64 (with [DietPi](https://www.dietpi.com) installed and configured)
* I2C LCD
* Case [Optional] 

### Prerequiests
* Rock64 with an OS installed and booted and updated.
* Installed packages 
  * RPi-Monitor (instructions [here](https://xavierberger.github.io/RPi-Monitor-docs/11_installation.html))
* Following Software also
> sudo apt-get install python3
> 
> sudo apt-get install python-pip
> 
> sudo apt-get install python3-smbus
> 
> sudo apt-get install i2c-tools
>
> sudo pat install git


### Install
Follow the below instruction to clone this repo and install
 
> chown -R USER: /opt
> cd /opt/
>
> git clone https://github.com/kdjstudios/Rock64-I2C-LCD-Stats
>
> cd Rock64-I2C-LCD-Stats
> 
> wget http://tutorials-raspberrypi.de/wp-content/uploads/scripts/hd44780_i2c.zip
>
> unzip hd44780_i2c.zip
>
> rm hd44780_i2c.zip

Use the following to find the Address of your LCD

> i2cdetect -y 1

Edit and update the address line in ""; replacing with the address foudn from the above line.

> ADDRESS = 0x3f

### Start
Follow the below instruction to start the script
 
> cd /opt/Rock64-I2C-LCD-Stats
>
> sudo python stats.py

### Setup Auto Run at Boot
Follow the below instructions to setup a Cronjob to auto start this at boot. Note we will have it on a delay start since we need to wait until RPi-Monitor to also start running too.

@reboot sh /opt/Rock64-I2C-LCD-Stats/start.sh >/opt/logs/log 2>&1


# Issues
Check out the wiki [] to see about troubleshooting. 

