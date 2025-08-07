STM32CubeMX is a graphical tool provided by STMicroelectronics that helps developers configure STM32 microcontrollers quickly and easily. It generates initialization C code for STM32 peripherals based on user-defined settings using a graphical interface.

### Steps to Create an LED Blink Project using STM32CubeMX

- **Select MCU and Create Project**
  - Launch STM32CubeMX and search for your target MCU (e.g., STM32F446RE).
  - Select the MCU and click `Start Project`.

<img width="1313" height="727" alt="image" src="https://github.com/user-attachments/assets/c96f2624-69aa-4275-8d7c-1373b35923b2" />

- **Select GPIO Mode**
  - Click on the desired GPIO pin (e.g., PA5) in the pinout view.
  - Set the mode to `GPIO_Output`.
  - GPIO speed and Open-Drain / Push-Pull mode can be configured from here.
 
- **Enable Debug Pins (SWDIO & SWCLK)**
  - Go to `System Core` → `SYS`.
  - Set `Debug` to `Serial Wire` to enable SWDIO and SWCLK.

 <img width="1920" height="1039" alt="image" src="https://github.com/user-attachments/assets/deda1df2-e357-48d5-adaf-9bfdab1eba56" />


- **Configure the Clock**
  - Open the `Clock Configuration` tab.
  - Set up the HCLK and SYSCLK as required.

- **Go to Project Manager**
  - Navigate to the `Project Manager` tab.
  - Enter a project name and location.
  - Select `MDK-ARM` as the toolchain.

- **Generate Code for Keil**
  - Click on `Generate Code`.
  - Open the generated `.uvprojx` file in Keil uVision to start development.
 
  ### Writing User Code

After generating the code from STM32CubeMX and opening the project in Keil:

- Open the `Src/main.c` file.
- Locate the `while (1)` loop inside the `main()` function.
- Write your LED control code **only inside the `/* USER CODE BEGIN` and `/* USER CODE END` blocks** to prevent it from being overwritten when regenerating code from CubeMX.

Example:
```c
/* USER CODE BEGIN WHILE */
while (1)
{
  HAL_GPIO_TogglePin(GPIOA, GPIO_PIN_5); // Toggle PA5
  HAL_Delay(500); // Delay 500 ms
}
/* USER CODE END WHILE */
```

