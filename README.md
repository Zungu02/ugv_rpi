![GitHub top language](https://img.shields.io/github/languages/top/effectsmachine/ugv_rpi) ![GitHub language count](https://img.shields.io/github/languages/count/effectsmachine/ugv_rpi)
![GitHub code size in bytes](https://img.shields.io/github/languages/code-size/effectsmachine/ugv_rpi)
![GitHub repo size](https://img.shields.io/github/repo-size/effectsmachine/ugv_rpi) ![GitHub](https://img.shields.io/github/license/effectsmachine/ugv_rpi) ![GitHub last commit](https://img.shields.io/github/last-commit/effectsmachine/ugv_rpi)

# A Laser Defense system prototype
This is a Raspberry Pi example for the 360° Omnidirectional High-Torque 2-Axis Expandable Pan-Tilt Camera Module, Driven By Serial Bus Servos, Based On General Driver Board For Robots

![2-Axis Pan-Tilt Module](https://www.waveshare.com/media/catalog/product/cache/1/image/560x560/9df78eab33525d08d6e5fb8d27136e95/2/-/2-axis-pan-tilt-camera-module-3.jpg)

## Basic Description
The project incorporates a developed motion-targeting defense system using a Raspberry Pi and real-time video detection,and an integrated servo-controlled laser aiming system with OpenCV for object tracking

The upper computer communicates with the lower computer (the robot's driver based on ESP32) by sending JSON commands via GPIO UART. The host controller, which employs a Raspberry Pi, handles AI vision and strategy planning, while the sub-controller, utilizing an ESP32, manages motion control and sensor data processing. This setup ensures efficient collaboration and enhanced performance.

## Features
- Real-time video based on WebRTC
- Interactive tutorial based on JupyterLab
- Pan-tilt camera control
- Robotic arm control
- Cross-platform web application base on Flask
- Auto targeting (OpenCV)
- Object Recognition (OpenCV)
- Gesture Recognition (MediaPipe)
- Face detection (OpenCV & MediaPipe)
- Motion detection (OpenCV)
- Line tracking base on vision (OpenCV)
- Color Recognition (OpenCV)
- Multi-threaded CV processing
- Audio interactive
- Shortcut key control
- Photo taking
- Video Recording

## Quick Install
Begin by installing Raspberry Pi OS 64-bit (Lite or Desktop) using the Raspberry Pi Imager.  

create your virtual environment with access to system packages
This will allow your environment to see system-wide libraries like libcamera while still using the virtual environment for project-specific packages. 
   
    python3 -m venv ugv-env --system-site-packages
    source ugv-env/bin/activate


Update the system using 

    sudo apt update && sudo apt full-upgrade -y.  

Install necessary dependencies like pip, opencv-python, numpy, flask, and other required packages using pip. You can also install OpenCV-related system libraries.

    pip install flask flask_socketio mediapipe imageio pyserial

    sudo apt-get update && sudo apt-get upgrade
    time sudo apt install -y build-essential cmake pkg-config libjpeg-dev libtiff5-dev libpng-dev libavcodec-dev libavformat-dev libswscale-dev libv4l-dev libxvidcore-dev libx264-dev libfontconfig1-dev libcairo2-dev libgdk-pixbuf2.0-dev libpango1.0-dev libgtk2.0-dev libgtk-3-dev libatlas-base-dev gfortran libhdf5-dev libhdf5-serial-dev libhdf5-103 libqt5gui5 libqt5webkit5 libqt5test5 python3-pyqt5 python3-dev

If you're using a PiCamera run:
    
    pip install "picamera[array]"
### Download the repo from github

You can clone this repository from Waveshare's GitHub to your local machine.

    git clone https://github.com/waveshareteam/ugv_rpi.git

### After unzipping, install the software
 enter "ugv_rpi" 

    cd ugv_rpi

install  pip dependencies

    pip install --upgrade pip setuptools wheel
   
Install system-level dependencies, These pull in Python dev headers, SDL2 (for pygame), D-Bus bindings, OpenCV requirements, and other low-level libs:

    sudo apt update
    
    sudo apt install -y \
    python3-pip python3-venv python3-dev \
    libatlas-base-dev libopenblas-dev \
    libhdf5-dev libjpeg-dev libtiff5-dev libpng-dev \
    libgtk-3-dev libcanberra-gtk* \
    libsdl2-dev libsdl2-image-dev libsdl2-mixer-dev libsdl2-ttf-dev \
    libportmidi-dev libfreetype6-dev libxcursor-dev libxrandr-dev \
    libxinerama-dev libsmpeg-dev libavformat-dev libswscale-dev \
    libudev-dev \
    libdbus-1-dev libdbus-glib-1-dev python3-dbus

Install PyQt5 via APT

    sudo apt update
    sudo apt install -y python3-pyqt5 python3-pyqt5.qtwebsockets python3-pyqt5.qtwebkit

Install the Samba client dev files

    sudo apt update
    sudo apt install libsmbclient-dev python3-smbc

(Optional) Install minimal Jupyter via APT
If you still need a notebook interface for quick tests, grab the Debian-packaged version (much smaller overall):

    sudo apt install -y python3-notebook python3-jupyter-core python3-ipykernel
    
 Install the system package

    sudo apt install -y python3-apt

Install the Debian package

    sudo apt install -y python3-prctl

Install the Debian-packaged python3-pgzero via APT

    sudo apt install -y python3-pgzero

Install the missing SDL1.2 dev libs, then build from pip

    sudo apt update
    sudo apt install -y \
    libsdl1.2-dev \
    libsdl-image1.2-dev \
    libsdl-mixer1.2-dev \
    libsdl-ttf2.0-dev \
    libsmpeg-dev \
    libportmidi-dev \
    libfreetype6-dev \
    libjpeg-dev \
    libpng-dev

Install the distro packages that satisfy python-prctl

    sudo apt install -y python3-prctl libcap-dev

##### strip out all the known problematic or system-only packages from your requirements.txt
Backup first

     cp requirements.txt requirements.txt.bak

Then remove non-PyPI or ARM-incompatible entries

     sed -i \
       -e '/^arandr==/d' \
       -e '/^cupshelpers==/d' \
       -e '/^dbus-python==/d' \
       -e '/^python-apt==/d' \
       -e '/^pysmbc==/d' \
       -e '/^python-prctl==/d' \
       -e '/^pygame==/d' \
       -e '/^pgzero==/d' \
       -e '/^PyQt5==/d' \
       -e '/^PyQt5-sip==/d' \
       -e '/^jupyterlab==/d' \
       -e '/^jupyter-server==/d' \
       -e '/^notebook==/d' \
       -e '/^ipywidgets==/d' \
       -e '/^ipywidgets==/d' \
       -e '/^widgetsnbextension==/d' \
       -e '/^matplotlib==/d' \
       -e '/^matplotlib-inline==/d' \
       -e '/^opencv-contrib-python==/d' \
       -e '/^opencv-python-headless==/d' \
       -e '/^torch==/d' \
       -e '/^torchvision==/d' \
       -e '/^torchaudio==/d' \
       -e '/^mediapipe==/d' \
       -e '/^depthai/d' \
       -e '/^types-/d' \
       requirements.txt

       sed -i '/^importlib-metadata==/d' requirements.txt
       sed -i -e '/^pgzero==/d' -e '/^pygame</d' requirements.txt
       sed -i '/types-typing-extensions/d' requirements.txt
       sed -i '/numpy==1.21/d' requirements.txt
       sed -i '/python-apt/d' requirements.txt
       sed -i '/pysmbc/d' requirements.txt
       sed -i '/python-prctl/d' requirements.txt
       sed -i '/pygame<2.0,>=1.9.2/d' requirements.txt

remove jupyterlab and its widget deps

      sed -i -e '/^jupyterlab==/d' \
             -e '/^jupyter-server==/d' \
             -e '/^jupyterlab-pygments==/d' \
             -e '/^jupyterlab-widgets==/d' \
             -e '/^notebook==/d' \
             -e '/^ipywidgets==/d' \
            requirements.txt

##### Install those via APT

      sudo apt update
      sudo apt install -y \
      python3-dbus \
      python3-prctl \
      python3-pygame \
      python3-pgzero \
      python3-pyqt5 \
      python3-pyqt5.qtwebsockets \
      python3-pyqt5.qtwebkit \
      python3-opencv \
      python3-numpy \
      python3-scipy \
      python3-matplotlib \
      python3-picamera2 \
      libatlas-base-dev \
      libopenblas-dev \
      libhdf5-dev \
      libsdl2-dev libsdl2-image-dev libsdl2-mixer-dev libsdl2-ttf-dev \
      libdbus-1-dev libdbus-glib-1-dev \
      libsmbclient-dev

##### Extras
 install picamera2

     sudo apt install -y python3-picamera2

     pip install imageio
    
install mediapipe

     pip install mediapipe --extra-index-url https://www.piwheels.org/simple

     pip install pyserial

     pip install PyGObject

     sudo apt install -y libgirepository1.0-dev gir1.2-glib-2.0

 Install extra system dependencies

     sudo apt update && sudo apt install -y \
   portaudio19-dev \
   libcups2-dev \
   libgirepository1.0-dev \
   libglib2.0-dev \
   libffi-dev \
   libboost-all-dev \
   libi2c-dev \
   python3-dev \
   python3-gi \
   python3-cairo

Then run the following:

    pip install PyAudio pycups PyGObject RTIMULib


### Grant execution permission to the installation script
    cd ugv_rpi/
    sudo chmod +x setup.sh
    sudo chmod +x autorun.sh
### Install app (it'll take a while before finish)
    sudo ./setup.sh
### Autorun setup
    ./autorun.sh
### AccessPopup installation
    cd AccessPopup
    sudo chmod +x installconfig.sh
    sudo ./installconfig.sh
    *Input 1: Install AccessPopup
    *Press any key to exit
    *Input 9: Exit installconfig.sh
### Reboot Device
    sudo reboot

After powering on the robot, the Raspberry Pi will automatically establish a hotspot, and the LED screen will display a series of system initialization messages:  

![](./media/RaspRover-LED-screen.png)
- The first line `E` displays the IP address of the Ethernet port, which allows remote access to the Raspberry Pi. If it shows No Ethernet, it indicates that the Raspberry Pi is not connected to an Ethernet cable.
- The second line `W` indicates the robot's wireless mode. In Access Point (AP) mode, the robot automatically sets up a hotspot with the default IP address `192.168.50.5`. In Station (STA) mode, the Raspberry Pi connects to a known WiFi network and displays the IP address for remote access.
- The third line `F/J` specifies the Ethernet port numbers. Port `5000` provides access to the robot control Web UI, while port `8888` grants access to the JupyterLab interface.
- The fourth line `STA` indicates that the WiFi is in Station (STA) mode. The time value represents the duration of robot usage. The dBm value indicates the signal strength RSSI in STA mode.  


You can access the robot web app using a mobile phone or PC. Simply open your browser and enter `[IP]:5000` (for example, `192.168.10.50:5000`) in the URL bar to control the robot.  

To access JupyterLab, use `[IP]:8888` (for example, `192.168.10.50:8888`).  

If the robot is not connected to a known WiFi network, it will automatically set up a hotspot named "`AccessPopup`" with the password `1234567890`. You can then use a mobile phone or PC to connect to this hotspot. Once connected, open your browser and enter `192.168.50.5:5000` in the URL bar to control the robot.  

To ensure compatibility with various types of robots running on Raspberry Pi, we utilize a config.yaml file to specify the particular robot being used. You can configure the robot by entering the following command:

    s 22

In this command, the s directive denotes a robot-type setting. The first digit, `2`, signifies that the robot is a `UGV Rover`, with `1` representing `RaspRover` and `3` indicating `UGV Beast`. The second digit, also `2`, specifies the module as `Camera PT`, where `0` denotes `Nothing` and `1` signifies `RoArm-M2`.  

### Reboot Device
If the program fails to run and encounters errors related to v4l2.py during runtime, you need to delete v4l2.py from both the Python virtual environment and the user environment. This will allow the program to automatically use the system-wide v4l2.py.  

    cd ugv_rpi/  
    sudo rm ugv-env/lib/python3.11/site-packages/v4l2.py  
    sudo rm /home/[your_user_name]/.local/lib/python3.11/site-packages/v4l2.py  

Now you can restart the main program app.py.

# License
ugv_rpi for the Raspberry Pi: an open source robotics platform for the Raspberry Pi.
Copyright (C) 2024 [Waveshare](https://www.waveshare.com/)

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/gpl-3.0.txt>.
