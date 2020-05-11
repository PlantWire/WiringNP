# WiringNP
This is a GPIO access library for NanoPi_Neo. It is based on [WiringNP](https://github.com/friendlyarm/WiringNP) which is based on the WiringOP for Orange PI which is based on original WiringPi for Raspberry Pi.

The WiringPi version was adjusted so that only static library building is supported. Also the only supported board by this fork is the "NanoPi Neo". This fork supports the newer "Buster"-images based on [Armbian](https://www.armbian.com/) which the original does not support.

# Installation

## Install WiringNP 
Log into your nano board via SSH, open a terminal and install the WiringNP library by running the following commands:
```
git clone https://github.com/friendlyarm/WiringNP
cd WiringNP/wiringPi
make static
sudo make install-static
```

# Code Sample with WiringNP
connect a LED module to a NanoPi (Pin7), Make a C source file:
```
vi test.c
```
Type the following lines:
```
#include <wiringPi.h>
int main(void)
{
  wiringPiSetup() ;
  pinMode (7, OUTPUT) ;
  for(;;)
  {
    digitalWrite(7, HIGH) ;
    delay (500) ;
    digitalWrite(7,  LOW) ;
    delay (500) ;
  }
}
```
Compile and run "test.c":
```
gcc -Wall -o test test.c -lwiringPi -lpthread
sudo ./test
```
You can see the LED is blinking.