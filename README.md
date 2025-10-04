# Temperature-control-device

# Temperature-Controlled Fan with AVR Microcontroller

This project implements a **temperature-controlled fan system** using an **AVR microcontroller**, an **LM35 temperature sensor**, **PWM**, **UART**, and an **ALCD** display. The system allows the user to set a target temperature (setpoint), and the fan speed is automatically adjusted based on the measured temperature with hysteresis control.

## Features

- User-defined setpoint for temperature control
- Automatic fan ON/OFF with **hysteresis** (prevents frequent switching)
- Multi-level fan speed control:
  - Fan speed increases as temperature rises above setpoints
  - Fan speed decreases gradually as temperature approaches setpoints
  - Fan stops when temperature falls below the first threshold
- Real-time temperature monitoring displayed on ALCD
- UART interface for debugging and monitoring

## Hysteresis Behavior

- Each setpoint has a **±2°C hysteresis**:
  - Fan turns **ON** when temperature rises **2°C above** the setpoint  
  - Fan turns **OFF** when temperature drops **2°C below** the setpoint  
- This prevents rapid ON/OFF switching and ensures smooth fan operation.

## Components

- **Microcontroller**: AVR family  
- **Sensor**: LM35 temperature sensor  
- **Display**: Alphanumeric LCD (ALCD)  
- **Control**: PWM for fan speed regulation  
- **Communication**: UART for monitoring temperature and fan status

## How It Works

1. The user sets a **temperature setpoint** via the interface or UART.  
2. The system continuously reads the temperature from the **LM35 sensor**.  
3. **Fan control logic with hysteresis**:
   - Temperature exceeds the first threshold → fan ON at low speed  
   - Temperature exceeds the second threshold → fan speed increases  
   - Temperature exceeds the third threshold → fan runs at maximum speed  
   - As temperature decreases and passes back through thresholds, fan speed gradually reduces  
   - Fan turns **OFF** only after temperature drops below setpoint minus 2°C  
4. Real-time temperature and fan speed are displayed on the **ALCD**. 
