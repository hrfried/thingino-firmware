Compilation
===========

Thingino is very easy to develop and compile on a local development machine.

To begin with the development, fork the main repository on GitHub:

https://github.com/themactep/thingino-firmware/fork

Then clone your fork locally.

```bash
git clone --recurse-submodules https://github.com/<username>/thingino-firmware
cd thingino-firmware
```

This method will allow you to store your changes in your own fork and create
pull requests to the upstream repository as the changes are ready for sharing.

To start a compilation process, just run the following commands:

```bash
make
```

You will be greeted with a list of cameras supported by Thingino. Select the
camera you are developing for and press Enter.

First compilation may take a significant time as you will need to download all
the necessary dependencies and compile the firmware. Subsequent compilations
will be much faster. We utilize the `ccache` utility to speed up the compilation
process.

For even faster compilation, you can run `make fast`, which will employ the
experimental multi-threaded compilation.

After the compilation is complete, you will find the firmware binary in the
`~/output/<cameraprofile>/images/` directory. The final firmware binary will be
named `thingino-<cameraprofile>.bin`.

Thingino firmware is designed to be flashed using the `sysupgrade` utility and
even has a special target in its Makefile for upgrading cameras with a network
access over the air: `make upgrade_ota IP=<cameraip>` for a full upgrade,
or `make update_ota IP=<cameraip>` for a partial upgrade.

If the camera you are working on is not accessible over the network, you can
flash the firmware to it using a programming clip, Cloner tool, SD card, TFTP
server, or any other method you prefer.
