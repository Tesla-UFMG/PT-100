# Max31865 library links:
1 - https://github.com/nimaltd/max31865 (use)
--------------------------------------------------------------------
This is the MAX31865 STM32 HAL Library
Based on https://github.com/adafruit/Adafruit_MAX31865

### How to use this Library:

- Select "General peripheral Initalizion as a pair of '.c/.h' file per peripheral" on project settings.
- Enable SPI and set clock below 2MHz,MSB,CPOL LOW,CPHA 2 Edge.
- Enable a gpio as Output for CS Pin.
- Include Header and source into your project.
- Config "Max31865Conf.h".
- Call Max31865_Init( .. .. .. ).
```c
#include "Max31865.h"
Max31865_t  pt100;
bool        pt100isOK;
float       pt100Temp;
int main()
{
  Max31865_init(&pt100,&hspi3,SENSOR_CS1_GPIO_Port,SENSOR_CS1_Pin,4,50);
  while(1)
  {
    float t;
    pt100isOK = Max31865_readTempC(&pt100,&t);
    pt100Temp = Max31865_Filter(t,pt100Temp,0.1);   //  << For Smoothing data  
    HAL_Delay(1000);
  }
}
```
--------------------------------------------------------------------

2 - https://github.com/4ilo/MAX31865-Stm32HAL
--------------------------------------------------------------------
MAX31865 temperature readout for stm32 using stm32-hal library's.

Library is developed and tested with Stm32F411-discovery.

Features:
- Pt100 support
- Software SPI
- 2, 3 and 4 wire temperature probe connection possible

### Example
```c
// Define SPI pinout
MAX31865_GPIO max_gpio;
max_gpio.MISO_PIN = MAX_MISO_Pin;
max_gpio.MISO_PORT = MAX_MISO_GPIO_Port;
max_gpio.MOSI_PIN = MAX_MOSI_Pin;
max_gpio.MOSI_PORT = MAX_MOSI_GPIO_Port;
max_gpio.CLK_PIN = MAX_CLK_Pin;
max_gpio.CLK_PORT = MAX_CLK_GPIO_Port;
max_gpio.CE_PIN = MAX_CE_Pin;
max_gpio.CE_PORT = MAX_CE_GPIO_Port;

// Initialize using the above pinout definition
// Use a 3 wire pt100
MAX31865_init(&max_gpio, 3);

// Perform a single shot conversion, and calculate the temperature
float temp = MAX31865_readTemp();
```
--------------------------------------------------------------------
