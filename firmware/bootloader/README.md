iBee ATMega32u4 bootload
==========================

### Upload Tools

Using a FT232RL USB to UART board


### Connections

* 32U4_MISO -> FT232_CTS (Green)
* 32U4_SCK -> FT232_DSR  (Yellow)
* 32U4_MOSI -> FT232_DCD (Blue)
* 32U4_RESET -> FT232_RI (Orange)


### Build avrdude-serjtag


```bash
$ git clone git://github.com/laclefyoshi/avrdude-serjtag.git avrdude
$ cd avrdude
$ tar zxvf bin/avrdude-5.11.1.tar.gz
$ cd avrdude-5.11.1
$ (linux optional) patch -p1 < ../src/avrdude-5.8-baud.patch
$ patch -p1 < ../src/avrdude-5.10-serjtag.patch
$ patch -p1 < ../src/avrdude-5.11-serjtag.patch
$ patch -p1 < ../src/avrdude-5.8-ft245r.patch
$ patch -p1 < ../src/avrdude-5.11-ft245r.patch
$ patch -p1 < ../src/avrdude-5.8-confu2.patch
```

Installing libftd2xx drivers: http://www.ftdichip.com/Drivers/D2XX.htm

```bash
$ sudo apt-get install libusb-1.0.0-dev libusb-dev
$ ./configure CFLAGS="-g -O2 -DSUPPORT_FT245R" LIBS="-lftd2xx" --prefix=/usr/local
$ make
$ sudo make install
```


### Flash bootloader

```bash
$ make flash
```
