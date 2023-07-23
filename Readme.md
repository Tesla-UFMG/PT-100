# MAX31865

Leitura do Pt100 max31865 através de um stm32f103c8t6 usando a biblioteca HAL.

O max31865 utiliza como protocolo de comunicação o SPI. Além disso, essa comunicação pode ser feita com 2, 3 ou 4 fios.

## Example
```c
#include "Max31865.h"

int main(void)
{
  // Definição dos pinos do SPI
  // SPI1 do stm com o pino de ativação A0
  MAX31865_GPIO sensor;
	sensor.MISO_PIN = GPIO_PIN_6;
	sensor.MISO_PORT = GPIOA;
	sensor.MOSI_PIN = GPIO_PIN_7;
	sensor.MOSI_PORT = GPIOA;
	sensor.CLK_PIN = GPIO_PIN_5;
	sensor.CLK_PORT = GPIOA;
	sensor.CE_PIN = GPIO_PIN_0;
	sensor.CE_PORT = GPIOB;
  
  // Inicialização usando a definição de pinos anteriormente
  // 2 fios para o Pt100 do Tesla
  MAX31865_init(&sensor, 2);

  while (1)
  {
    // Perform a single shot conversion, and calculate the temperature
    float temp = MAX31865_readTemp();
    HAL_Delay(500);
  }
}
```
Reference:
- https://github.com/4ilo/MAX31865-Stm32HAL
