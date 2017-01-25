MCU=m32u4
CC=avr-gcc
OBJCOPY=avr-objcopy
CFLAGS=-g -mmcu=$(MCU) -O1

flash:
	sudo modprobe -r ftdi_sio
	# (SCK) -> DSR, (MISO) -> CTS, (MOSI) -> DCD, (RESET) -> RI
	sudo avrdude -p m32u4 -c ft232r1 -P ft0 -B 230400 -Uefuse:w:0xcb:m -Uhfuse:w:0xd8:m -Ulfuse:w:0xff:m 
	sudo avrdude -p m32u4 -c ft232r1 -P ft0 -B 230400 -e -u -Ulock:w:0x3f:m -U flash:w:Caterina-Leonardo.hex -Ulock:w:0x2f:m

test:
	sudo modprobe -r ftdi_sio
	sudo avrdude -cft232r1 -p $(MCU) -P ft0 -U hfuse:r:-:h -B 1
