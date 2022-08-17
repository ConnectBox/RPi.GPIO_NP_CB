This is a fork of the RPi.GPIO_NP from friendlyArm.com (https://github.com/friendlyarm/RPi.GPIO_NP).
(The orignial of their README.md is reproduced below.) Changes have been made to 4 of the "C" code
modules to allow it to work with armbian fusion. Additionally, errors were corrected in the event_gpio.c module
to fix failing function calls due to undersized char arrarys leading to truncation of filenames. Follow 
the Installation instructions from the original READ.me to compile and install.   Additionally errors in compilation
have been fixed by multiple definitions of variables.

### Changed modules are:

  boardtype_friendlyelec.c   
  boardtype_friendlyelec.h  
  c_gpio.c    
  py_gpio.c  
  event_gpio.c
  common.c  

(Note that these revisions have only been tested with a NanoPi NEO.)


----- Original READ.me from https://github.com/friendlyarm/RPi.GPIO_NP  -----

This is a modified version RPi.GPIO for NanoPi NEO/NEO2. We call it RPi.GPIO_NP.
It is based on the original [RPi.GPIO](https://pypi.python.org/pypi/RPi.GPIO).
The RPi.GPIO_NP API usage are the same to the original RPi.GPIO.
You can donwload the RPi.GPIO_NP from:
https://github.com/friendlyarm/RPi.GPIO_NP

## Currently supported boards (Allwinner H3/H5)
NanoPi Neo  
NanoPi Neo Air  
NanoPi Duo  
NanoPi Duo2  
NanoPi NEO2  
NanoPi NEO Plus2  
NanoPi M1  
NanoPi M1 Plus  
NanoPi NEO Core  
NanoPi NEO Core2  
NanoPi K1 Plus  

## Installation
Log into your nano board via SSH, open a terminal and install the WiringNP library by running the following commands:
```
sudo apt-get update
sudo apt-get install python-dev
git clone https://github.com/friendlyarm/RPi.GPIO_NP
cd RPi.GPIO_NP
python setup.py install                 
sudo python setup.py install
```
    
Please be attention that you need use both python and sudo python to make the RPi.GPIO_NP work well.

## Code Sample
connect a LED module to a NanoPi (Pin7), Create a source file in Python:
```
vi led.py
```
Type the following lines:
```
#!/usr/bin/env python
import RPi.GPIO as GPIO
import time
PIN_NUM = 7
 
GPIO.setmode(GPIO.BOARD)
GPIO.setup(PIN_NUM,GPIO.OUT)
while True:
        GPIO.output(PIN_NUM,True)
        time.sleep(1)
        GPIO.output(PIN_NUM,False)
        time.sleep(1)
```
Run led.py:
```
chmod +x led.py
sudo ./led.py
```
You can see the LED is blinking.

## Document
You can go to FriendlyELEC wiki to see the basic examples: http://wiki.friendlyarm.com/wiki/index.php/RPi.GPIO_NP:_RPi.GPIO_for_NanoPi_NEO/NEO2
And the source directory test also has many demo.


