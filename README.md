# HabitatCAN Dev Board (ESP32)

A development board designed for HabitatCAN home automation applications, featuring an ESP32-C3-MINI-1 microcontroller with integrated CAN bus transceiver and comprehensive I/O capabilities.

## Overview

The HabitatCAN Dev Board is a development platform for building HabitatCAN-compatible devices. HabitatCAN is an open standard for home automation built on the Controller Area Network (CAN) bus, providing reliable, low-latency communication between sensors, switches, actuators, and controllers in residential and light commercial environments.

Unlike proprietary systems (Control4, KNX, Zigbee), HabitatCAN is designed to be open, inexpensive, and implementable on common microcontrollers. It leverages structured cabling (Ethernet Cat5e/Cat6) for wiring but uses CAN signaling rather than Ethernet, allowing for robust operation in electrically noisy environments and over long distances.

## What is HabitatCAN?

HabitatCAN is a local-first home automation standard that provides:

- **Reliable Communication**: CAN bus ensures robust, real-time communication over structured cabling
- **Local-First Design**: Homes continue to function without Internet or cloud connectivity
- **Fault Isolation**: Failures are isolated and recovered automatically
- **Simple Devices**: Minimal logic in devices, complexity handled by controllers
- **Extensibility**: New device types and commands can be added without breaking older firmware

### Key Features of HabitatCAN:
- **500 kbit/s CAN bus** over Cat5e/Cat6 cabling (~100m reach)
- **24V courtesy power** distributed over structured cabling
- **Hierarchical addressing**: NetworkID (16-bit) + RoomID (8-bit) + NodeID (8-bit)
- **Automatic device discovery** and commissioning
- **Group and scene support** for complex automation
- **Fault tolerance** with backup controllers and local autonomy

## Board Images

![HabitatCAN Dev Board - Side 1](pic/HabitatCAN%20Dev%20Board%20(ESP32)%20-%20Image%20-%20Side%201.png)

![HabitatCAN Dev Board - Front](pic/HabitatCAN%20Dev%20Board%20(ESP32)%20-%20Image%20-%20Front.png)

![HabitatCAN Dev Board - Back](pic/HabitatCAN%20Dev%20Board%20(ESP32)%20-%20Image%20-%20Back.png)

## Key Features

### Microcontroller
- **ESP32-C3-MINI-1**: Ultra-low-power MCU with 2.4 GHz Wi-Fi and Bluetooth Low Energy
- **RISC-V 32-bit single-core processor**
- **400 KB SRAM, 384 KB ROM**
- **Built-in Wi-Fi and Bluetooth connectivity**

### CAN Bus Interface
- **TJA1051T CAN Transceiver**: High-speed CAN transceiver with silent mode
- **RJ45 Connector**: Standard Ethernet-style connector for HabitatCAN network connection
- **HabitatCAN Compliant**: Follows HabitatCAN specification for structured cabling

### Power Management
- **USB-C Power Input**: 5V input via USB-C connector
- **24V Input Support**: Optional 24V input with step-down conversion

### I/O Capabilities
- **18-pin GPIO Header**: All ESP32-C3 GPIO pins accessible
- **Serial Communication**: UART0 (TX/RX) pins available
- **ADC Channels**: Multiple analog input channels
- **Boot/Reset Controls**: Dedicated boot and reset buttons
- **Status LED**: Built-in status indicator
- **USB-C Programming**: Direct programming via USB-C


## Pinout

### GPIO Header (J1)
| Pin | Function | Description |
|-----|----------|-------------|
| 1   | GND      | Ground      |
| 2   | 3V3      | 3.3V Power  |
| 3   | GPIO0    | GPIO0 / Boot |
| 4   | GPIO1    | GPIO1 |
| 5   | GPIO2    | GPIO2 |
| 6   | GPIO3    | GPIO3 |
| 7   | GPIO4    | GPIO4 / CAN RX |
| 8   | GPIO5    | GPIO5 / CAN TX |
| 9   | GPIO6    | GPIO6 |
| 10  | GPIO7    | GPIO7 |
| 11  | GPIO8    | GPIO8 / Status LED |
| 12  | GPIO9    | GPIO9 |
| 13  | GPIO10   | GPIO10 |
| 14  | S_TX     | Serial TX |
| 15  | S_RX     | Serial RX |
| 16  | EN       | Enable / Reset |
| 17  | 5V       | 5V Power |
| 18  | GND      | Ground |

### CAN Bus Connector (J3) - HabitatCAN Compliant
| Pin | Function | Description |
|-----|----------|-------------|
| 1   | GND      | Ground |
| 2   | GND      | Ground |
| 3   | CAN_H    | CAN High |
| 4   | +24V     | 24V Courtesy Power |
| 5   | +24V     | 24V Courtesy Power |
| 6   | CAN_L    | CAN Low |
| 7   | Reserved | Reserved for future use |
| 8   | Reserved | Reserved for future use |

### I2C Connector (J6) - QWIIC Compliant
| Pin | Function | Description |
|-----|----------|-------------|
| 1   | GND      | Ground |
| 1   | 3V3      | 3.3V Power |
| 1   | SDA      | Serial Data |
| 1   | SCL      | Serial Clock |

## HabitatCAN Development

### Device Types
This development board can be used to create various HabitatCAN device types:

**Sensors:**
- Door/Window sensors
- Motion sensors  
- Temperature sensors
- CO₂ sensors
- Humidity sensors
- Light sensors

**Switches:**
- Light switches
- Scene switches
- Dimmer controls

**Actuators:**
- Relay/Outlet controllers
- Dimmer controllers
- Blind controllers
- RGB/CCT lighting controllers

### HabitatCAN Protocol
The board implements the HabitatCAN protocol with:
- **Device Discovery**: Automatic UID-based device identification
- **Address Assignment**: RoomID/NodeID assignment by Room Controllers
- **Message Types**: FAULT, DISCOVER, ASSIGN, HEARTBEAT, COMMAND, GROUP, TELEMETRY
- **Security**: HMAC authentication for critical frames
- **Group/Scene Support**: Integration with HabitatCAN automation

## Getting Started

### Prerequisites
- Arduino IDE with ESP32 board support, or
- PlatformIO, or
- ESP-IDF development framework
- USB-C cable for programming and power
- HabitatCAN network infrastructure (Room Controller, Main Controller)

### Programming
1. Connect the board to your computer via USB-C
2. Install the ESP32 board package in your development environment
3. Select the ESP32-C3 board variant
4. Upload your HabitatCAN-compatible firmware

### HabitatCAN Network Setup
1. Connect the RJ45 connector to your HabitatCAN network
2. Ensure proper termination (automatic if used as end device)
3. The device will automatically discover and request address assignment
4. Configure device type and capabilities in your firmware

## Hardware Design

### Schematic
The board design is available in KiCad format in the `cad/` directory:
- Main schematic: `HabitatCAN Dev Board (ESP32).kicad_sch`
- PCB layout: `HabitatCAN Dev Board (ESP32).kicad_pcb`

### Manufacturing Files
Gerber files for PCB manufacturing are available in the `cad/Gerber/` directory:
- Copper layers (F_Cu, B_Cu)
- Solder mask (F_Mask, B_Mask)
- Silkscreen (F_Silkscreen, B_Silkscreen)
- Solder paste (F_Paste, B_Paste)
- Drill files (PTH.drl, NPTH.drl)

### Panel Design
A panelized version is available for batch manufacturing in the `cad/Panel/` directory.

## Revision History

- **Rev 4 (2025-09-15)**: Added QWIIC interface
- **Rev 3 (2025-09-14)**: Cleaned up bugs and silkscreen layer (archived in `cad/Rev3/`)
- **Rev 2**: Previous revision (archived in `cad/Rev2/`)
- **Rev 1**: Initial design

## License

This project is licensed under the Creative Commons Attribution-ShareAlike 4.0 International License. See `LICENSE.md` for details.

## Contributing

Contributions are welcome! Please feel free to submit issues, feature requests, or pull requests.

## Support

For questions and support, please open an issue in this repository.

---

*This development board is designed for HabitatCAN home automation development. Always follow proper safety guidelines when working with electrical circuits and home automation systems.*
