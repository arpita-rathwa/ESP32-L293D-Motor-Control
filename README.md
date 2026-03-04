# ESP32 + L293D Dual DC Motor Control 🤖

A circuit simulation built in **Tinkercad** demonstrating how to control two DC motors using an Arduino Uno (ESP32-equivalent logic) and an L293D motor driver IC. The motors can run forward, reverse, and stop — with PWM speed control.

---

## 📋 Components Used

| Component | Quantity | Purpose |
|---|---|---|
| Arduino Uno (ESP32 logic equivalent) | 1 | Microcontroller |
| L293D Motor Driver IC | 1 | H-Bridge motor control |
| DC Motor | 2 | Output actuators |
| Jumper Wires | — | Connections |

---

## 🔌 Wiring Overview

### Power
| From | To |
|---|---|
| Arduino 5V | L293D Pin 16 (VCC1 - logic) |
| Arduino 5V | L293D Pin 8 (VCC2 - motor) |
| Arduino GND | L293D Pin 4, 5, 12, 13 (GND) |

### Signal Lines (Arduino → L293D)
| Arduino Pin | L293D Pin | Function |
|---|---|---|
| Pin 8 | Pin 2 (IN1) | Motor A direction |
| Pin 9 | Pin 7 (IN2) | Motor A direction |
| Pin 10 | Pin 10 (IN3) | Motor B direction |
| Pin 11 | Pin 15 (IN4) | Motor B direction |
| Pin 5 (~PWM) | Pin 1 (EN1) | Motor A speed |
| Pin 6 (~PWM) | Pin 9 (EN2) | Motor B speed |

### Motor Outputs (L293D → Motors)
| L293D Pin | Motor |
|---|---|
| Pin 3 (OUT1) | Motor A terminal 1 |
| Pin 6 (OUT2) | Motor A terminal 2 |
| Pin 11 (OUT3) | Motor B terminal 1 |
| Pin 14 (OUT4) | Motor B terminal 2 |

---

## 💻 Arduino Code

```cpp
#define IN1 8
#define IN2 9
#define IN3 10
#define IN4 11
#define ENA 5
#define ENB 6

void setup() {
  pinMode(IN1, OUTPUT);
  pinMode(IN2, OUTPUT);
  pinMode(IN3, OUTPUT);
  pinMode(IN4, OUTPUT);
  pinMode(ENA, OUTPUT);
  pinMode(ENB, OUTPUT);
}

void loop() {
  // Both motors forward at 75% speed
  analogWrite(ENA, 191);
  analogWrite(ENB, 191);
  digitalWrite(IN1, HIGH);
  digitalWrite(IN2, LOW);
  digitalWrite(IN3, HIGH);
  digitalWrite(IN4, LOW);
  delay(3000);

  // Both motors stop
  analogWrite(ENA, 0);
  analogWrite(ENB, 0);
  delay(1000);

  // Both motors reverse
  analogWrite(ENA, 191);
  analogWrite(ENB, 191);
  digitalWrite(IN1, LOW);
  digitalWrite(IN2, HIGH);
  digitalWrite(IN3, LOW);
  digitalWrite(IN4, HIGH);
  delay(3000);
}
```

---

## 🔁 How It Works

The **L293D** is a dual H-bridge IC. Each H-bridge controls one motor by switching the direction of current flow:

- `IN1=HIGH, IN2=LOW` → Motor A spins **forward**
- `IN1=LOW, IN2=HIGH` → Motor A spins **reverse**
- `IN1=LOW, IN2=LOW` → Motor A **stops**
- `analogWrite(ENA, 0–255)` → Controls **speed** via PWM

The same logic applies to Motor B using IN3, IN4, and ENB.

---

## 🧪 Simulation

This project was built and tested in **Tinkercad Circuits**.

> 🔗 [View the Tinkercad Simulation](#) ← *paste your Tinkercad share link here*

---

## 📝 Notes

- This simulation uses an **Arduino Uno** as a stand-in for the ESP32, since Tinkercad does not natively support ESP32. The logic and pin behavior are identical for this use case.
- For a real ESP32 build, replace `analogWrite()` with `ledcWrite()` using the LEDC PWM library.
- Motor direction can be reversed by swapping the OUT1/OUT2 (or OUT3/OUT4) wires physically.

---

## 📁 Files

| File | Description |
|---|---|
| `README.md` | Project documentation |
| `motor_control.ino` | Arduino sketch |
| `circuit.png` | Screenshot of Tinkercad circuit |

---

## 🛠️ Tools Used

- [Tinkercad Circuits](https://www.tinkercad.com) — Online circuit simulator
- Arduino IDE — Code editor and uploader# ESP32 + L293D Dual DC Motor Control 🤖

A circuit simulation built in **Tinkercad** demonstrating how to control two DC motors using an Arduino Uno (ESP32-equivalent logic) and an L293D motor driver IC. The motors can run forward, reverse, and stop — with PWM speed control.

---

## 📋 Components Used

| Component | Quantity | Purpose |
|---|---|---|
| Arduino Uno (ESP32 logic equivalent) | 1 | Microcontroller |
| L293D Motor Driver IC | 1 | H-Bridge motor control |
| DC Motor | 2 | Output actuators |
| Jumper Wires | — | Connections |

---

## 🔌 Wiring Overview

### Power
| From | To |
|---|---|
| Arduino 5V | L293D Pin 16 (VCC1 - logic) |
| Arduino 5V | L293D Pin 8 (VCC2 - motor) |
| Arduino GND | L293D Pin 4, 5, 12, 13 (GND) |

### Signal Lines (Arduino → L293D)
| Arduino Pin | L293D Pin | Function |
|---|---|---|
| Pin 8 | Pin 2 (IN1) | Motor A direction |
| Pin 9 | Pin 7 (IN2) | Motor A direction |
| Pin 10 | Pin 10 (IN3) | Motor B direction |
| Pin 11 | Pin 15 (IN4) | Motor B direction |
| Pin 5 (~PWM) | Pin 1 (EN1) | Motor A speed |
| Pin 6 (~PWM) | Pin 9 (EN2) | Motor B speed |

### Motor Outputs (L293D → Motors)
| L293D Pin | Motor |
|---|---|
| Pin 3 (OUT1) | Motor A terminal 1 |
| Pin 6 (OUT2) | Motor A terminal 2 |
| Pin 11 (OUT3) | Motor B terminal 1 |
| Pin 14 (OUT4) | Motor B terminal 2 |

---

## 💻 Arduino Code

```cpp
#define IN1 8
#define IN2 9
#define IN3 10
#define IN4 11
#define ENA 5
#define ENB 6

void setup() {
  pinMode(IN1, OUTPUT);
  pinMode(IN2, OUTPUT);
  pinMode(IN3, OUTPUT);
  pinMode(IN4, OUTPUT);
  pinMode(ENA, OUTPUT);
  pinMode(ENB, OUTPUT);
}

void loop() {
  // Both motors forward at 75% speed
  analogWrite(ENA, 191);
  analogWrite(ENB, 191);
  digitalWrite(IN1, HIGH);
  digitalWrite(IN2, LOW);
  digitalWrite(IN3, HIGH);
  digitalWrite(IN4, LOW);
  delay(3000);

  // Both motors stop
  analogWrite(ENA, 0);
  analogWrite(ENB, 0);
  delay(1000);

  // Both motors reverse
  analogWrite(ENA, 191);
  analogWrite(ENB, 191);
  digitalWrite(IN1, LOW);
  digitalWrite(IN2, HIGH);
  digitalWrite(IN3, LOW);
  digitalWrite(IN4, HIGH);
  delay(3000);
}
```

---

## 🔁 How It Works

The **L293D** is a dual H-bridge IC. Each H-bridge controls one motor by switching the direction of current flow:

- `IN1=HIGH, IN2=LOW` → Motor A spins **forward**
- `IN1=LOW, IN2=HIGH` → Motor A spins **reverse**
- `IN1=LOW, IN2=LOW` → Motor A **stops**
- `analogWrite(ENA, 0–255)` → Controls **speed** via PWM

The same logic applies to Motor B using IN3, IN4, and ENB.

---

## 🧪 Simulation

This project was built and tested in **Tinkercad Circuits**.

> 🔗 [View the Tinkercad Simulation](https://www.tinkercad.com/things/0rVM2rU9a04-esp32-l293d-motor-control) 

---

## 📝 Notes

- This simulation uses an **Arduino Uno** as a stand-in for the ESP32, since Tinkercad does not natively support ESP32. The logic and pin behavior are identical for this use case.
- For a real ESP32 build, replace `analogWrite()` with `ledcWrite()` using the LEDC PWM library.
- Motor direction can be reversed by swapping the OUT1/OUT2 (or OUT3/OUT4) wires physically.

---

## 📁 Files

| File | Description |
|---|---|
| `README.md` | Project documentation |
| `motor_control.ino` | Arduino sketch |
| `circuit.png` | Screenshot of Tinkercad circuit |

---

## 🛠️ Tools Used

- [Tinkercad Circuits](https://www.tinkercad.com) — Online circuit simulator
- Arduino IDE — Code editor and uploader
