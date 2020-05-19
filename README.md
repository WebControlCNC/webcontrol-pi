WebControl Raspberry Pi image
=============================

## Downloading

Download the current version [HERE](https://github.com/WebControlCNC/webcontrol-pi/releases/download/0.1.1/2020-02-13-webcontrolcnc-buster-lite-0.1.1.zip).

## Usage

1. Unzip the image and install it to an sd card [like any other Raspberry Pi image](https://www.raspberrypi.org/documentation/installation/installing-images/README.md)

2. Configure your WiFi by editing webcontrolcnc-wpa-supplicant.txt on the root of the flashed card when using it like a thumb drive

3. Boot the Pi from the card

If your network is in range, the Pi will connect to it, and WebControl will be available at http://\<ip address\>:5000. Look in your router's settings for the IP address.

If your network isn't in range, the Pi will create its own, named "webcontrolcnc", with the password "raspberry". WebControl will be available at http://192.168.50.1:5000/

## Building an image yourself

The build uses Docker to create the image. **Docker itself isn't used in the final image.**

Setup:

```
# Clone the build repositories
git clone https://github.com/guysoft/CustomPiOS.git
git clone https://github.com/emilecantin/webcontrol-pi.git

# Download the official base raspbian image
cd webcontrol-pi/src/image
wget -c --trust-server-names 'https://downloads.raspberrypi.org/raspbian_lite_latest'
cd ..

# Link the 2 build repositories
../../CustomPiOS/src/update-custompios-paths
```

Building (from the `src` directory):

```
docker-compose up -d
docker exec -it mydistro_builder build
```

Your built image will be in `src/workspace`.
