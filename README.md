# ESP32 + L293D Dual DC Motor Control

A Tinkercad circuit simulation controlling two DC motors with an Arduino Uno (ESP32 logic) and L293D motor driver. Motors run forward, reverse, and stop with PWM speed control.

🔗 [View Tinkercad Simulation](https://www.tinkercad.com/things/0rVM2rU9a04-esp32-l293d-motor-control)

---

## Components
- Arduino Uno (ESP32 equivalent)
- L293D Motor Driver IC
- 2× DC Motor

## Pin Wiring

| Arduino | L293D | Function |
|---|---|---|
| Pin 8 / 9 | IN1 / IN2 | Motor A direction |
| Pin 10 / 11 | IN3 / IN4 | Motor B direction |
| Pin 5 (~) | EN1 | Motor A speed (PWM) |
| Pin 6 (~) | EN2 | Motor B speed (PWM) |
| 5V | Pin 8, 16 | Power |
| GND | Pin 4, 5, 12, 13 | Ground |

## How It Works
- `IN1=HIGH, IN2=LOW` → Motor forward
- `IN1=LOW, IN2=HIGH` → Motor reverse
- `analogWrite(ENA, 0–255)` → Speed control

## Tools
- [Tinkercad Circuits](https://www.tinkercad.com)
- Arduino IDE
