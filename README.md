# 🚧 Smart Gate System with Ultrasonic Sensor, Servo, LED, and Buzzer

## 📜 Description

This Arduino project controls a **servo-powered gate** that opens when an object (like a person or vehicle) is detected within a certain distance using an **ultrasonic sensor**. It uses **LED indicators** to show gate status (open/closed) and a **buzzer** to emit warning sounds while the gate is open.

---

## 🔧 Components Used

| Component         | Description                        | Pin Connection |
|------------------|------------------------------------|----------------|
| Ultrasonic Sensor| HC-SR04                            | Trig - D2, Echo - D3 |
| Servo Motor      | Controls the gate arm              | D6 (PWM)       |
| Red LED          | Indicates gate is closed           | D4             |
| Blue LED         | Indicates gate is open             | D5             |
| Piezo Buzzer     | Emits beeping sound when gate is open | D12         |
| Arduino UNO/Nano | Microcontroller                    | —              |
| Additional GND   | Extra GND pins using digital pins  | D7, D8 (set LOW) |

---

## ⚙️ How It Works

1. **Distance Measurement**  
   The ultrasonic sensor continuously measures the distance in front of the gate.

2. **Gate Control**  
   - If an object is detected within **15 cm**, the gate opens to **80°** using the servo.
   - The red LED turns off and the blue LED lights up to indicate the gate is open.
   - A **buzzer starts ticking** with variable ON/OFF intervals to warn nearby people.

3. **Auto-Close Mechanism**  
   After **5 seconds**, the gate automatically closes:
   - The servo resets to **0°**.
   - The red LED is turned back on.
   - The buzzer is deactivated.

4. **Buzzer Logic**  
   - The buzzer toggles every 200ms.
   - ON time: 800ms  
   - OFF time: 400ms

---

## 🖼️ State Indicators

| Condition         | Red LED | Blue LED | Buzzer | Servo |
|------------------|---------|----------|--------|--------|
| Idle / No object | ON      | OFF      | OFF    | Closed (0°) |
| Object Detected  | OFF     | ON       | Beeping | Open (80°) |
| After 5 seconds  | ON      | OFF      | OFF    | Closed (0°) |

---

## 📝 Notes

- The `delay()` calls for buzzer control introduce blocking; consider using **non-blocking code** (`millis()`) for smoother performance in future upgrades.
- Pins D7 and D8 are used as **pseudo-GNDs** to make breadboarding easier. Ensure they are connected to ground rails.

---

## 📷 Future Enhancements

- Using an **IR sensor or RFID** for more reliable detection.
- Adding an **LCD/OLED display** to show real-time status.
- Implementing **non-blocking buzzer timing** for better performance.
- Adding **manual override buttons** for gate control.

---

## 🚀 Getting Started

1. Upload the code to your Arduino board.
2. Connect all components as per the pin definitions.
3. Power the board.
4. Place an object within 15 cm of the sensor to test the system.
