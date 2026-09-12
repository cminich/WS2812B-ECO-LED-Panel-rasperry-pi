# Raspberry Pi NeoPixel LED Matrix Text Scroller

A Python script that scrolls text across a **32x8 NeoPixel LED matrix** using a Raspberry Pi. It uses the Python Imaging Library (PIL) to render text into memory and maps it dynamically to a vertical zigzag matrix layout.

## 🛠️ Hardware Requirements
* **Raspberry Pi** (e.g., Raspberry Pi 3, 4, or Zero)
* **32x8 NeoPixel LED Matrix** (WS2812B)
* **External 5V Power Supply** (NeoPixels pull too much power to run directly off the Pi's 5V pin!)
* Connecting wires (Data line connected to **GPIO 18**)

## 📐 Matrix Layout
This script assumes a **vertical zigzag layout** where:
* Even columns ($x = 0, 2, 4\dots$) code pixels from top to bottom.
* Odd columns ($x = 1, 3, 5\dots$) code pixels from bottom to top.

## 🚀 Installation & Setup

1. **Update your Raspberry Pi:**
   ```bash
   sudo apt update && sudo apt upgrade -y
   ```

2. **Install the required system and Python libraries:**
   ```bash
   sudo pip3 install rpi_ws281x adafruit-circuitpython-neopixel pillow --break-system-packages
   ```
   *(Note: Remove `--break-system-packages` if you are running in a Python virtual environment).*

## 🏃 How to Run

Because the `neopixel` library requires direct hardware access to the PWM/GPIO pins, you **must run the script with root privileges (`sudo`)**:

```bash
sudo python3 led_scroll.py
```

* To stop the scrolling script, press `Ctrl + C`.

## ⚙️ Customization
Open `led_scroll.py` and modify the variables at the top to change the behavior:
* `TEXT_TO_SHOW`: Change what message scrolls across the panel.
* `TEXT_COLOR`: Alter the RGB tuple values (e.g., `(0, 255, 0)` for green).
* `BRIGHTNESS`: Adjust between `0.0` and `1.0` (set to `0.15` by default to preserve power).
