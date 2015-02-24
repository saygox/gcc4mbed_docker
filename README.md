# gcc4mbed: gcc for mbed compileation on the docker

[adamgreen's gcc4mbed](https://github.com/adamgreen/gcc4mbed) is easy to make a mbed-image over the local pc.
It is easy to install to Windows, Linux and Mac. but I want to use Docker.

## current version
adamgreen/gcc4mbed: commit 73e1ae96cf on 6 Dec 2014
GCC Version: GCC ARM Embedded 4.8-2014-q1-update
mbed SDK Version: Revision 92

## how to use

1. make working directory(work) under the current.
2. put in a makefile and source code on the working directory.

``` makefile
PROJECT         := HelloWorld
DEVICES         := LPC1768 LPC11U24 KL25Z NRF51822
NO_FLOAT_SCANF  := 1
NO_FLOAT_PRINTF := 1

include $(GCC4MBED_DIR)/build/gcc4mbed.mk
```

``` main.cpp
#include "mbed.h"

DigitalOut myled(LED1);

int main()
{
    while(1)
    {
        myled = 1;
        wait(0.2);
        myled = 0;
        wait(0.2);
    }
}
```

3. command as bellow

```
docker run -v \`pwd\`/work:/tmp saygox/gcc4mbed
```

4. install the program
 move *.bin in the working directory to the embed.
 restart the embed
