# Ingredients

* 1x Raspberry Pi 3 B+
* 1x [32x4 WS2812B RBG LED matrix](https://www.amazon.com/dp/B01DC0IPVU)
* Wires n stuff to connect to pins

# Usage

## Wire up

 * GPIO18 (PWM0) to DIN
 * 5V to 5V
 * GND to GND

## Download and setup `rpi_ws281x` repo

```bash
git clone https://github.com/jgarff/rpi_ws281x
```

Some guides, including the README for the rpi_ws281x repo, include instructions that I found unnecessary. Reproduced below are all the steps I actually needed.

## Install packages

```bash
# verified that these are required
sudo apt install gcc  make build-essential python-dev git scons swig
```

## Setup

```bash
cd rpi_ws281x
scons
```

## Test

```bash
sudo ./test -c
```

## Config

Edit `main.c` to change config. For this particular LED matrix, change `HEIGHT` to `32` (leave `WIDTH` at `8`). You also will probably want to change `.brightness` to something <`100` so you don't blind yourself.

Run the following after every change:

```bash
scons && sudo ./test -c
```

## Not working?

If these steps don't work, you may need to follow other instructions included in the [rpi_ws281x repo](https://github.com/jgarff/rpi_ws281x) or [these other instructions](https://tutorials-raspberrypi.com/connect-control-raspberry-pi-ws2812-rgb-led-strips/) I found (such as disabling the audio).

# Things that don't work

[Johnny Five](https://github.com/rwaldron/johnny-five/) doesn't seem to have any WS281x support. At least it's not in the docs anywhere or in the code from what I can tell.
