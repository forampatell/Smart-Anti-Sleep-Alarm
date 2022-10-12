
# Smart Anti-Sleep Alarm









## Description

This project is based on drowsiness detection system. When a person will be detected feeling drowsy or sleepy it will create an alarm or a beep sound using a buzzer connected to Jetson Nano to warn the person. 

As we know, a countless number of people drive on highway day and night. Taxi drivers, bus/truck drivers or people traveling long-distance suffer lack of sleep. Due to which many a times they starts feeling sleepy which is dangerous.To avoid such situations, a safety alarm type detector is created to make the drivers alert when they feel sleepy/drowsy.
Drowsiness detection is a safety technology that can prevent accidents that are caused by drivers who fell asleep while driving by making a beep sound.

## Dependencies

It is a computer vision project built using-
- OpenCV
- dilib
- imutils
- numpy
- Jetson.GPIO (Jetson nano library - general pupose input output)
It includes 68 face landmark detection file.(.dat)

Hardware part consists of NVIDIA Jetson Nano, a buzzer, dongle, cables, jumper wires and an adapter.
## Implementation

![App Screenshot](jetson-nano%20setup.jpeg)

- As seen from the image, the buzzer is placed on a breadboard.The positive terminal and negative terminal of the buzzer are connected to the pin and ground on the Jetson-Nano Board respectively with the help of jumper wires.
- Install NVIDIA Jetson-Nano on Ubuntu and further install Jetson.GPIO library in it.  
 Connect Jetson-Nano -
- To the adapter to supply power with B-type cable .
- To the Monitor with HDMI-cable.
- To the keyboard with USB cable.
- To the wi-fi and mouse with dongles. 
- Finally you're done with the hardware connections







## Libraries Installation

#### Jetson-Nano Libraries installation-

The ```bash lib/python/ ``` subdirectory contains the Python modules that implement all library functionality. The gpio.py module is the main component that will be imported into an application and provides the needed APIs. The ```bash gpio_event.py ``` and ```bash gpio_pin_data.py ``` modules are used by the ```bash gpio.py ``` module and must not be imported directly in to an application.

- install using pip
```bash
  sudo pip install Jetson.GPIO
```

- In order to use the Jetson GPIO Library, the correct user permissions/groups must be set first.

- Create a new gpio user group. Then add your user to the newly created group.
```bash
  sudo groupadd -f -r gpio
  sudo usermod -a -G gpio your_user_name
```
- Install custom udev rules by copying the 99-gpio.rules file into the rules.d directory.
```bash
  sudo cp lib/python/Jetson/GPIO/99-gpio.rules /etc/udev/rules.d/
```
#### Pyhton Libraries Installation-

- Open the commandprompt to install opencv-
```bash
  pip install opencv-python

```
- Next, install dilib on your system-
```bash
  pip install dlib

```
- To install imultis and numpy-
```bash
  pip install imutils
  pip install numpy

```

Now you're good to go to run the code.
## Library API of Jetson-Nano

The Jetson GPIO library provides all public APIs provided by the RPi.GPIO library. The following discusses the use of each API:

- Importing the libary.To import the Jetson.GPIO module use:
```bash
  import Jetson.GPIO as GPIO
```
- Pin numbering
The Jetson GPIO library provides four ways of numbering the I/O pins. The first two correspond to the modes provided by the RPi.GPIO library, i.e BOARD and BCM which refer to the pin number of the 40 pin GPIO header and the Broadcom SoC GPIO numbers respectively. The remaining two modes, CVM and TEGRA_SOC use strings instead of numbers which correspond to signal names on the CVM/CVB connector and the Tegra SoC respectively.

To specify which mode you are using , use the following function call:
```bash
  GPIO.setmode(GPIO.BOARD)
```
- Warnings
It is possible that the GPIO you are trying to use is already being used external to the current application. In such a condition, the Jetson GPIO library will warn you if the GPIO being used is configured to anything but the default direction (input). It will also warn you if you try cleaning up before setting up the mode and channels. To disable warnings, call:
```bash
  GPIO.setwarnings(False)
```
- Set up a channel
The GPIO channel must be set up before use as input or output. 
```bash
  GPIO.setup(channel, GPIO.OUT, initial=GPIO.LOW)
```

## How to Run

Save the .dat file in the same folder you saved your .py file to excute the code. Link to .dat file(68 face landmarks)-

- https://drive.google.com/file/d/1DkjrepOF7uCobJLAT7v4jgRsTLoXQpJY/view?usp=sharing

Image of the 68 face landmarks -
- https://www.researchgate.net/publication/329392737/figure/fig2/AS:731613625335813@1551441689799/The-68-landmarks-detected-by-dlib-library-This-image-was-created-by-Brandon-Amos-of-CMU.ppm


Now open the commandprompt and give the following commands-
- Copy the folder location
```bash
  cd project_folder/   
  python face_detect_buzz.py

```

Press esc key to close the camera window.


## Features

Makes a beeping sound when the driver feel sleepy to avoid dangerous situations.
