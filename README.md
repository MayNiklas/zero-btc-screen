# Zero BTC Screen
Bitcoin stock price for your RPi Zero

![display](display.jpg)

## Hardware
* Raspberry Pi Zero W (or any other RPi)
* Waveshare 2.13" eInk display

## Installation
1. Turn on SPI via `sudo raspi-config`
    ```
    Interfacing Options -> SPI
   ```
2. Installing dependencies via apt
    ```
    sudo apt update
    sudo apt install -y libopenjp2-7 libopenjp2-7 libatlas-base-dev
    ```
3. Install eInk display drivers
    ```
    git clone https://github.com/waveshare/e-Paper.git ~/e-Paper
    pip3 install image numpy ~/e-Paper/RaspberryPi_JetsonNano/python/
    ```
    for more information refer to: https://www.waveshare.com/wiki/2.13inch_e-Paper_HAT
4. Download Zero BTC Screen
    ```
    cd ~
    git clone https://github.com/dr-mod/zero-btc-screen.git
    ```
5. Run it 
    ```
    cd zero-btc-screen
    python3 main.py
    ```
6. To make it run on startup
    1. `nano /etc/rc.local` 
    2. Add one the following before `exit 0`
    ```
    /usr/bin/python3 /home/pi/zero-btc-screen/main.py&
    ```
    conversely, you can run in `screen`
    ```
    su - pi -c "/usr/bin/screen -dm sh -c 'cd /home/pi/zero-btc-screen/ && /usr/bin/python3 /home/pi/zero-btc-screen/main.py'"
    ```