# stm32_hal_ssd1306


__SSD1306, I2C, STM32 HAL__


## 0. Development environment  
* MCU : [STM32F411CEU6 (WeAct Black Pill V3.0)](https://github.com/WeActTC/MiniF4-STM32F4x1)
* IDE : [STM32CubeIDE](https://www.st.com/en/development-tools/stm32cubeide)
* SSD1306 Module : [Geekcreit® 0.96 Inch 4Pin White IIC I2C OLED Display Module 128x64](https://www.banggood.com/Geekcreit-0_96-Inch-4Pin-White-IIC-I2C-OLED-Display-Module-12864-LED-Geekcreit-for-Arduino-products-that-work-with-official-Arduino-boards-p-958196.html?akmClientCountry=Korea&p=DQ30066511122014069J&utm_campaign=educ8stv&utm_content=huangwenjie&cur_warehouse=CN)
    - Enable Charge Pump
    - RESET pin remains HIGH

<img src = "https://user-images.githubusercontent.com/48342925/124864408-cfb93300-dff3-11eb-8da6-ae32e6b231c3.png" width = "300" height = "300"><img src = "https://user-images.githubusercontent.com/48342925/124864222-82d55c80-dff3-11eb-9da4-c6ef6848ad6f.jpg" width = "300" height = "300">


## 1. Feature

- Use I2C interface
- Write string on the screen
- SSD1306 commands are defined as functions


## 2. User Configuration

- I2C1

### STM32CubeMx Configuration
![image](https://user-images.githubusercontent.com/48342925/125417497-32ca3cef-f010-490c-8961-9f549cfa895d.png)


### ssd1306.h
```c
/* SSD1306 Interface */ 
#define SSD1306_I2C                     (&hi2c1)
```

## 3. main.c 

__stm32f411_fw_ssd1306/Core/Src/main.c__

```c
#include "ssd1306.h"

int main(void)
{
    ssd1306_init();

    ssd1306_write_string(font6x8, "ABC");
    ssd1306_enter();

    ssd1306_write_string(font7x10, "ABC");
    ssd1306_enter();

    ssd1306_write_string(font11x18, "ABC");
    ssd1306_enter();

    ssd1306_write_string(font16x26, "ABC");
    ssd1306_enter();

    ssd1306_update_screen();
}

```

<img src = "https://user-images.githubusercontent.com/48342925/125418758-c149c2b7-1df2-4a42-a911-758acb94bcdf.jpg" width = "50%">


## Reference
https://github.com/afiskon/stm32-ssd1306