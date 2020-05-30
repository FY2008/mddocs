STM32 HAL 常用库函数



1. GPIO_PinState HAL_GPIO_ReadPin(GPIO_TypeDef *GPIOx, uint16_t GPIO_Pin)  // 读取 IO 状态
2. void HAL_GPIO_TogglePin(GPIO_TypeDef *GPIOx, uint16_t GPIO_Pin) // 翻转 IO 状态
3. HAL_StatusTypeDef HAL_GPIO_LockPin(GPIO_TypeDef *GPIOx, uint16_t GPIO_Pin)
4. void HAL_GPIO_EXTI_IRQHandler(uint16_t GPIO_Pin)
5. void HAL_GPIO_WritePin(GPIO_TypeDef *GPIOx, uint16_t GPIO_Pin, GPIO_PinState PinState) // 写 IO 状态
6. __weak void HAL_GPIO_EXTI_Callback(uint16_t GPIO_Pin)