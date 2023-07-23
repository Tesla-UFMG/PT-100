# MAX31865

Leitura do Pt100 max31865 através de um stm32f103c8t6 usando a biblioteca HAL.

O max31865 utiliza como protocolo de comunicação o SPI. Além disso, essa comunicação pode ser feita com 2, 3 ou 4 fios.

## Example
```c
#include "Max31865.h"

int main(void)
{
  // Definição dos pinos do SPI
  // SPI1 do stm com o pino de ativação B0
  MAX31865_GPIO sensor2;
  	sensor1.MISO_PIN = GPIO_PIN_6;
  	sensor1.MISO_PORT = GPIOA;
  	sensor1.MOSI_PIN = GPIO_PIN_7;
  	sensor1.MOSI_PORT = GPIOA;
  	sensor1.CLK_PIN = GPIO_PIN_5;
  	sensor1.CLK_PORT = GPIOA;
  	sensor1.CE_PIN = GPIO_PIN_0;
  	sensor1.CE_PORT = GPIOB;

  // SPI1 do stm com o pino de ativação A4
	MAX31865_GPIO sensor2;
  	sensor2.MISO_PIN = GPIO_PIN_6;
  	sensor2.MISO_PORT = GPIOA;
  	sensor2.MOSI_PIN = GPIO_PIN_7;
  	sensor2.MOSI_PORT = GPIOA;
  	sensor2.CLK_PIN = GPIO_PIN_5;
  	sensor2.CLK_PORT = GPIOA;
  	sensor2.CE_PIN = GPIO_PIN_4;
  	sensor2.CE_PORT = GPIOA;

  // SPI1 do stm com o pino de ativação A3
  MAX31865_GPIO sensor3;
  	sensor3.MISO_PIN = GPIO_PIN_6;
  	sensor3.MISO_PORT = GPIOA;
  	sensor3.MOSI_PIN = GPIO_PIN_7;
  	sensor3.MOSI_PORT = GPIOA;
  	sensor3.CLK_PIN = GPIO_PIN_5;
  	sensor3.CLK_PORT = GPIOA;
  	sensor3.CE_PIN = GPIO_PIN_3;
  	sensor3.CE_PORT = GPIOA;

  // Pode colocar mais sensores, apenas continuar com a lista de definição
  
  // Inicialização usando a definição de pinos anteriormente
  // 2 fios para o Pt100 do Tesla
  MAX31865_init(&sensor1, 2);
  MAX31865_init(&sensor2, 2);
  MAX31865_init(&sensor3, 2);

  while (1)
  {
    // Retorna a temperatura de cada ponteiro
    float temp1 = MAX31865_readTemp(&sensor1);
    float temp2 = MAX31865_readTemp(&sensor2);
    float temp3 = MAX31865_readTemp(&sensor3);

    HAL_Delay(500);
  }
}
```
Reference:
- https://github.com/4ilo/MAX31865-Stm32HAL
