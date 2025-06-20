# AstralCNC

A Replacement board for the Larken **StarCNC** controller. Built around the RPI Pico, this board is designed with safety and flexibility in mind, allowing for easy integration with external stepper drivers and digital inputs.

Powered by the Raspberry Pi Pico and GRBL-HAL.

Made to referbrish a Larken 24/24 router at my school that is over 25 years old.

# Features
- Supports up to 8 external stepper drivers (5v IO, Step/Dir)
- Supports up to 8 external digital inputs (3.3v IO)
- 5v IO can be switched to 3.3v IO
- 3.3v IO can be switched to 5v IO (for external stepper drivers)
- Built-in 12v regulator for powering all components
- Hardware level emergency stop
  - Emergency stop is not relient on software, ensuring that it works even if the software crashes as the stepper drivers put out a good ammount of EMI
- Hardware level reset button
  - Reset after an emergency stop is not relient on software, ensuring that the machine will remain stopped until it is manually reset
- 4 Analog inputs (ADC)
- All IO is PWM capable

# Images
![Larken StarCNC](https://hc-cdn.hel1.your-objectstorage.com/s/v3/94a4b2611dd05d7d1520e87d839704c9ca4bf86c_image.png)
![Schematic](https://hc-cdn.hel1.your-objectstorage.com/s/v3/663f6ed5d0925f178e119bd20d2991c114a9e5e1_image.png)
![PCB](https://hc-cdn.hel1.your-objectstorage.com/s/v3/96e08dfd8bd8cfe5c2162619ebf2a184466401bd_screenshot_2025-06-19_225025.png)


# BOM

| Name                                           | Quantity | Single Unit Price | Total Price | URL/LCSC                                   | FALSE | Vendor (LCSC unless otheriwse indicated) |
|------------------------------------------------|----------|-------------------|-------------|--------------------------------------------|-------|------------------------------------------|
| Electronics                                    |          |                   |             |                                            | FALSE |                                          |
| 47pF                                           | 1        | N/A               | $0.29       | C105622                                    | FALSE |                                          |
| 0.1uF                                          | 1        | N/A               |             |                                            | FALSE | With My other two projects               |
| 22uF                                           | 2        | N/A               | $0.17       | C59461                                     | FALSE |                                          |
| 4.7uF                                          | 2        | N/A               | $0.15       | C69335                                     | FALSE |                                          |
| Molex_KK-254_AE-6410-02A_1x02_P2.54mm_Vertical | 1        | N/A               | $0.40       | C5447965                                   | FALSE |                                          |
| Molex_KK-254_AE-6410-10A_1x10_P2.54mm_Vertical | 1        | N/A               | $0.39       | C30169                                     | FALSE |                                          |
| PinHeader_2x04_P2.54mm_Vertical                | 1        | N/A               | $0.39       | C2829882                                   | FALSE |                                          |
| PinHeader_1x04_P2.54mm_Vertical                | 7        | N/A               | $0.42       | C2935910                                   | FALSE |                                          |
| Molex_KK-254_AE-6410-03A_1x03_P2.54mm_Vertical | 4        | N/A               | $0.71       | C29275                                     | FALSE |                                          |
| 6.8UH                                          | 1        | N/A               | $1.18       | C5296375                                   | FALSE |                                          |
| BC847                                          | 3        | N/A               | $0.46       | C57668                                     | FALSE |                                          |
| 220k                                           | 1        | N/A               | $0.10       | C22961                                     | FALSE |                                          |
| 41.2k                                          | 1        | N/A               | $0.10       | C2930101                                   | FALSE |                                          |
| 93.1k                                          | 1        | N/A               | $0.10       | C2933266                                   | FALSE |                                          |
| 22k                                            | 1        | N/A               | $0.09       | C2907015                                   | FALSE |                                          |
| 10k                                            | 6        | N/A               |             |                                            | FALSE | With My other two projects               |
| AP63357                                        | 1        | N/A               | $0.52       | C2158014                                   | FALSE |                                          |
| 74HC244                                        | 2        | N/A               | $0.77       | C5623                                      | FALSE |                                          |
| RP2350_Stamp                                   | 1        | N/A               | $12.05      | https://lectronz.com/products/rp2350-stamp | FALSE |                                          |
| TXS0108EPW                                     | 2        | N/A               | $1.12       | C17206                                     | FALSE |                                          |
| MOLEX 22013037                                 | 4        |                   | $0.27       | C22451182                                  | FALSE |                                          |
| Molex 2759 seris                               | 12       |                   | $0.24       | C22451180                                  | FALSE |                                          |
| PCB - JLC                                      |          |                   | $9.00       |                                            |       |                                          |
| LCSC - Shipping and handling                   |          |                   | $17.16      |                                            |       |                                          |
| lectronz                                       |          |                   | $17.79      |                                            |       |                                          |
| JLC - Shipping                                 |          |                   | $8.23       |                                            |       |                                          |
|                                                |          |                   |             |                                            |       |                                          |
|                                                |          |                   |             |                                            |       |                                          |
|                                                |          |                   |             |                                            |       |                                          |
|                                                |          |                   |             |                                            |       |                                          |
|                                                |          |                   |             |                                            |       |                                          |
|                                                |          |                   |             |                                            |       |                                          |
|                                                |          |                   |             |                                            |       |                                          |
|                                                |          |                   |             | CAD                                        |       |                                          |
|                                                |          |                   | $72.10      | USD                                        |       |                                          |
|                                                |          |                   | $72.10      | Total - USD                                |       |                                          |

Why is shipping so expensive? 😭