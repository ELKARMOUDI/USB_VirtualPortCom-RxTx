# STM32 USB Virtual COM Port Echo with RealTerm

![STM32](https://img.shields.io/badge/STM32F411-Discovery-03234B?logo=stmicroelectronics&logoColor=white)
![USB](https://img.shields.io/badge/USB-CDC_ECHO-2496ED?logo=usb&logoColor=white)
![Terminal](https://img.shields.io/badge/Tested-RealTerm-success)

![F3E4AB9B-1FB9-433C-B0FD-C6A92EA97154](https://github.com/user-attachments/assets/2d138b79-f13e-4cae-ab53-4161180acded)

## Features
- 🔄 **Bidirectional USB CDC Communication**
- 📤 **Automatic Data Echo** - All received data is transmitted back
- 💡 **Visual Feedback** - Onboard LED (PD12) toggles on each received packet
- ⏱️ **96MHz System Clock** via 8MHz HSE + PLL
- 🔋 **Power Efficient** - 500ms main loop delay

## Hardware Setup
| Component | Connection |
|-----------|------------|
| STM32F411 Discovery | CN5 USB port |
| Green LED (PD12) | N/A (onboard) |

## Code Architecture
```c
// Data Flow:
PC -> [USB RX] -> CDC_Receive_FS() 
      -> CDC_ReceiveCallBack() 
      -> CDC_Transmit_FS() (echo)
      -> HAL_GPIO_TogglePin() (LED)
