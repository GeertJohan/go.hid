
This project is an attempt to wrap the signal11/hidapi in go.
At this point, development is done for linux/hidraw, although I'll try to keep options open to make this package cross-platform compatible (just like hidapi is).

**This project is not nearly finished.**

To compile this project you need libudev.h on your system.
Install this on debian/ubuntu with `sudo aptitude install libudev-dev`