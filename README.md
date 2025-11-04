# RP2040-Dmx
Project RP2040 Dmx using PIO. 
Open in Visual Studio Code. 
thanks to library jostlowe/Pico-DMX.

#include "stdio.h"
...
#include "DmxOutput.cpp"

#define D_ENABLE1 7
DmxOutput dmxOutputs;
...
#define UNIVERSE_LENGTH 512
uint8_t universe[UNIVERSE_LENGTH + 1];
...
int main()
{
    gpio_init(D_ENABLE1);
    gpio_set_dir(D_ENABLE1, GPIO_OUT);
    gpio_put(D_ENABLE1, true);
    ...
    dmxOutputs.begin(0, pio0);
    ...
    while (true) {
        dmxOutputs.write(universe, UNIVERSE_LENGTH + 1);
        while (dmxOutputs.busy());
    }
}
