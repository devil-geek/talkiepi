# talkiepi

talkiepi is a fork of [barnard](https://github.com/layeh/barnard) for the Raspberry Pi.  It is a headless capable Mumble client written in Go, adapted for walkie talkie style use on the Pi using GPIO pins for input and LED display.

You can edit your pin assignments in `talkiepi.go`
```go
const (
	OnlineLEDPin       uint = 18
	ParticipantsLEDPin uint = 23
	TransmitLEDPin     uint = 24
	ButtonPin          uint = 25
)
```

## 3D Print the enclosure
In the stl directory are the stl files for the enclosure I have designed specifically for the Raspberry Pi B+ board layout and the PCB+Components from the [US Robotics USB Speakerphone](https://www.amazon.com/USRobotics-USB-Internet-Speakerphone-USR9610/dp/B000E6IL10/ref=sr_1_1?ie=UTF8&qid=1472691020&sr=8-1&keywords=us+robotics+speakerphone).
I will be posting a blog post shortly with a full component list and build guide.


## Requirements
Ensure you have the development packages for openal and libopus installed. On debian/raspbian you can do the following
```
apt-get install libopenal-dev libopus-dev
```

- [gumble](https://github.com/dchote/gumble)
- [gopus](https://github.com/layeh/gopus)
- [termbox-go](https://github.com/nsf/termbox-go)
- [gpio](https://github.com/dchote/gpio)
- [go-rpio](github.com/stianeikeland/go-rpio)

## Using talkiepi
I am using a cheap USB speakerphone (US Robotics). If you are using a USB speakerphone device, be sure to update your alsa config so that your system uses that instead of the built in audio on the raspberry pi. You can list your audio devices by running `aplay -l`, find the index of the device (likely 1) and then edit the alsa config (`/usr/share/alsa/alsa.conf`), changing the following:
```
defaults.ctl.card 1
defaults.pcm.card 1
```
_1 being the index of your device_

If you are not familiar with golang, please follow the instructions over on my blog [projectable.me](http://projectable.me/building-an-internet-walkie-talkie-using-a-raspberry-pi-v3/)

## License

MPL 2.0

## Author

- Barnard Author - Tim Cooper (<tim.cooper@layeh.com>)
- talkiepi Adaption - [Daniel Chote](https://github.com/dchote)
