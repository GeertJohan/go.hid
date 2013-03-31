
This project wraps the signal11/hidapi in [http://golang.org](go).
At this point, development is done for linux/hidraw, although I'll try to keep options open to make this package cross-platform compatible (just like hidapi is).

To compile this project you need libudev.h on your system.
Install this on debian/ubuntu with `sudo aptitude install libudev-dev`

I started this project to be able to communicate with the MSI leds device in the MSI GT780DX laptop. For more information about that project, visit https://github.com/GeertJohan/mgl