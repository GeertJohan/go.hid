
This project wraps the [signal11/hidapi](https://github.com/signal11/hidapi) in [go](http://golang.org).

**This project is under development.** A lot of features are working, but proper tests have to be added.
If you want to use this package, please read the source code and be aware that it's not finished yet.

At this point, development is done with linux/hidraw, although I'll probably make this package cross-platform compatible (just like hidapi is).

To compile this project you need libudev.h on your system.
Install this on debian/ubuntu with `sudo aptitude install libudev-dev`

I started this project to be able to communicate with the MSI leds device in the MSI GT780DX laptop. For more information about that project, visit https://github.com/GeertJohan/mgl