# STM32 常用代码

## 呼吸灯代码1

```c
uint16_t t = 1;

typedef enum {
  LED_UP,
  LED_DOWN
} LED_MODE;

LED_MODE led_mode_flag = LED_UP;

while (1)
{
    /* USER CODE END WHILE */
    if (led_mode_flag == LED_UP){
        for (int i=0; i<10; i++){
            HAL_GPIO_WritePin(LED_GPIO_Port, LED_Pin, GPIO_PIN_RESET);  // LED 亮
            delay_us(t);  // 亮 t us
            HAL_GPIO_WritePin(LED_GPIO_Port, LED_Pin, GPIO_PIN_SET);  // LED 灭
            delay_us(501-t);
        }
        t++;
        if(t==500){
            led_mode_flag = LED_DOWN;
        }
    }
    if (led_mode_flag == LED_DOWN){
        for (int i=0; i<10; i++){
            HAL_GPIO_WritePin(LED_GPIO_Port, LED_Pin, GPIO_PIN_RESET);
            delay_us(t);
            HAL_GPIO_WritePin(LED_GPIO_Port, LED_Pin, GPIO_PIN_SET);
            delay_us(501-t);
        }
        t--;
        if(t==1){
            led_mode_flag = LED_UP;
        }
    }
    /* USER CODE BEGIN 3 */
}
```

