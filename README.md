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

## 📝 How to Create and Run the File on Your Pi

Follow these steps directly inside your Raspberry Pi terminal to get the code running.

### Step 1: Create the Python file
Open a new file named `led_scroll.py` using the Nano text editor:
```bash
nano led_scroll.py
```

### Step 2: Add the code
1. Copy the Python code provided in this repository.
2. Paste it into your terminal window (if using a mouse, right-click and select **Paste**).
3. Press `Ctrl + O` then hit `Enter` to save the file.
4. Press `Ctrl + X` to exit the text editor.

### Step 3: Run the script
Because the NeoPixel library requires direct hardware access to the Pi's GPIO pins, you **must** run the script with root privileges (`sudo`):
```bash
sudo python3 led_scroll.py
```

*To stop the scrolling text at any time, press `Ctrl + C` in your terminal.*

## ⚙️ Customization
Open `led_scroll.py` and modify the variables at the top to change the behavior:
* `TEXT_TO_SHOW`: Change what message scrolls across the panel.
* `TEXT_COLOR`: Alter the RGB tuple values (e.g., `(0, 255, 0)` for green).
* `BRIGHTNESS`: Adjust between `0.0` and `1.0` (set to `0.15` by default to preserve power).
