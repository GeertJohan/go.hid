## go.hid
This [go](http://golang.org) package wraps the [signal11/hidapi](https://github.com/signal11/hidapi).

### Usage:
#### Installation:
To compile this project you need libudev.h on your system. Install this on debian/ubuntu with `sudo apt-get install libudev-dev`

When that is done: `go get github.com/GeertJohan/go.hid`

#### Example:
This is a simple example on how to use feature reports. For a working example view [GeertJohan/mgl](https://github.com/GeertJohan/mgl).
```go
package main

import(
	"log"
	"github.com/GeertJohan/go.hid"
)

func main() {
	// open the MSI GT leds device
	leds, err := hid.Open(0x1770, 0xff00, "")
	if err != nil {
		log.Fatalf("Could not open leds device: %s", err)
	}
	defer leds.Close()

	// create a feature report. This is always 8*n+1 bytes long, where n is >1.
	data := make([]byte, 9)
	data[0] = 0x01  // dummy data
	data[1] = 0x02  // dummy data
	data[2] = 0x03  // dummy data
	data[3] = 0x04  // dummy data
	data[4] = 0x05  // dummy data
	data[5] = 0x06  // dummy data
	data[6] = 0x07  // dummy data
	data[7] = 0x08  // dummy data
	data[8] = 0xec  // EOR

	_, err := leds.SendFeatureReport(data)
	if err != nil {
		log.Fatalf("Could not send feature report to do dummy action. %s\n", err)
	}
}
```

### TODO:
At this point, the package works for linux with hidraw.
hidapi itself is already cross-platform, so making this package work cross-platform shouldn't be a lot of work.
- Make this work cross-platform.
- Add tests (find if there is a usb-hid dummy device that has expected input/output and works consistently within an OS (we can write a test file for each OS seperated))
- Better example (preferably with a dummy test device)

### History:
I started this project to be able to communicate with the MSI leds device in the MSI GT780DX laptop. For more information about that project, visit [GeertJohan/mgl](https://github.com/GeertJohan/mgl).