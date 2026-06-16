# 🤖 Arduino Obstacle Avoiding Robot

<img width="608" height="386" alt="Screenshot 2026-06-16 194846" src="https://github.com/user-attachments/assets/e8ae2092-14bf-4bdc-9e7a-ce704b064bc9" />


> An autonomous robot that detects and avoids obstacles in real-time using an ultrasonic sensor and Arduino UNO.

---

## 📖 Overview

This project demonstrates a self-navigating robot that moves forward autonomously. When it detects an obstacle ahead, it:

1. **Stops** immediately
2. **Reverses** for a short duration
3. **Turns** to a new direction
4. **Continues** forward — repeating the loop

It serves as a foundational concept for advanced systems like **self-driving cars**, **manufacturing robots**, and even **Mars rovers**.

---

## 🧰 Components

| Component | Description |
|---|---|
| Arduino UNO | Microcontroller brain of the robot |
| 2-Wheel Drive Chassis | The physical frame of the robot |
| 2× DC BO Motors | Powers left and right wheels |
| L293 Motor Driver | Sends commands to the motors |
| HC-SR04 Ultrasonic Sensor | Detects obstacles |
| 9V Battery + Connector | Powers the robot |
| Switch | ON/OFF control |
| Caster Wheel | Front support wheel |
| Jumper Wires | Connections between components |
| Nut-Bolts & Spacers | Mechanical assembly |

---

## ⚙️ How It Works

### 🔊 Ultrasonic Sensor (HC-SR04)
The sensor emits an ultrasonic wave forward. When the wave hits an obstacle, it reflects back to the receiver. The distance is calculated from the **time taken** for the round trip:

```
Distance = (Time × Speed of Sound) / 2
```

### 🧠 Arduino Logic
A condition is set in the code:
- If `distance < threshold` → stop, reverse, turn
- Else → move forward

### ⚡ Motor Driver (L293)
The L293 receives signals from Arduino and drives both DC motors independently — allowing forward, backward, and turning motions.

---

## 🔌 Wiring Connections

### Motor Driver (L293)
```
Vin        →  9V Battery (+)
GND        →  9V Battery (-)
M1         →  Left Motor
M2         →  Right Motor
IN1 & IN2  →  Arduino pins 4 & 5
IN3 & IN4  →  Arduino pins 6 & 7
```
> ⚠️ If a motor runs in the wrong direction, swap its IN connections.

### Ultrasonic Sensor (HC-SR04)
```
VCC   →  Arduino 5V
GND   →  Arduino GND
Trig  →  Arduino A1
Echo  →  Arduino A2
```

---

## 🚀 Getting Started

### 1. Install Arduino IDE
Download from [arduino.cc/en/software](https://www.arduino.cc/en/software)

### 2. Install NewPing Library
Download the **NewPing** library and place it in your Arduino libraries folder:
```
C:\Arduino\libraries\NewPing
```

### 3. Upload the Code
- Connect Arduino UNO to your PC via USB
- Open the `.ino` sketch in Arduino IDE
- Select the correct **Board** and **COM Port**
- Click **Upload**

### 4. Power the Robot
- Disconnect USB
- Insert 9V batteries
- Flip the switch — the robot starts moving!

---

## 🔁 Robot Behavior Flow

```
         ┌─────────────┐
         │  Move Forward│
         └──────┬──────┘
                │
         ┌──────▼──────┐
         │ Obstacle     │
         │ Detected?    │
         └──────┬──────┘
         No ↙       ↘ Yes
    (continue)   ┌──────▼──────┐
                 │    Stop      │
                 └──────┬──────┘
                        │
                 ┌──────▼──────┐
                 │   Reverse    │
                 └──────┬──────┘
                        │
                 ┌──────▼──────┐
                 │    Turn      │
                 └──────┬──────┘
                        │
                  (loop back)
```

---

## 📦 Project Structure

```
obstacle-avoiding-robot/
│
├── obstacle_avoiding_robot.ino   # Main Arduino sketch
├── README.md                     # Project documentation
└── circuit_diagram.png           # Wiring diagram (add your own)
```

---

## 🌍 Real-World Applications

- 🚗 Autonomous / Self-Driving Cars
- 🏭 Manufacturing Factory Robots
- 🛸 Spacecraft & Mars Rover Navigation
- 🏠 Home Cleaning Robots (like Roomba)

---

## 📜 License

This project is open-source and available under the [MIT License](LICENSE).

---

## 🙌 Acknowledgements

- [Arduino](https://www.arduino.cc/) — open-source hardware & software platform
- [NewPing Library](https://bitbucket.org/teckel12/arduino-new-ping/wiki/Home) — ultrasonic sensor support
