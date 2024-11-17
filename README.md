# Humanoid Detection Using Mouse Cursor Movements

## 📋 Introduction

This project aims to detect whether the movement of a computer mouse cursor is controlled by a human or an automated bot. By analyzing patterns in cursor movements over time, the program can classify behavior as either human-like or bot-like based on features such as direction changes, velocity variance, and straight-line movements.

The project consists of:
1. **Mouse Movement Detection (`mouse.c`)**: Tracks and analyzes mouse cursor movements for detection.
2. **Mouse Bot Simulation (`mouse_bot.c`)**: Simulates automated mouse movements to test the detection system.

## 📂 Files

- **`mouse.c`**: The main detection program using the X11 library.
- **`mouse_bot.c`**: A bot script to simulate automated cursor movements.
- **`runboth.sh`**: Shell script to run both programs for testing.

## 🛠️ Prerequisites

Ensure that the following libraries are installed:

- **X11 Library**: The code uses the X11 library for mouse event capture. Install it using:
  ```bash
  sudo apt install libx11-dev

- **POSIX Threads (pthread)**: The project employs multithreading using the pthread library.

## Code Overview
**`mouse.c` - Mouse Movement Detection**

The mouse.c program continuously tracks the mouse cursor position and analyzes the movement data to identify patterns that are characteristic of automated scripts (bots). Key features include:

**1. Mouse Tracking**: Uses the X11 library to capture the current mouse cursor position at regular intervals (100 milliseconds).

**2. Velocity Calculation**: Computes the velocity of the cursor based on the distance traveled over time.

**3. Direction Analysis**: Determines the direction of movement and checks for sudden changes.

**4. Bot Detection Algorithm**:

**a) Straight-Line Movement**: Counts the number of intervals where the movement direction remains constant (indicating a straight line).

**b) Velocity Variance**: Calculates the variance of cursor speed. Human movements tend to have a high variance due to natural hand jitter, while bots usually exhibit low variance.

**c) Detection Criteria**: If the straight-line count exceeds a certain threshold and the velocity variance is below a defined limit, the movement is classified as bot-like.


**5. Multithreading**: The bot detection algorithm runs in a separate thread, allowing concurrent data analysis without blocking the main thread.


**`mouse_bot.c` - Mouse Bot Simulation**

The mouse_bot.c script simulates automated cursor movements in a square pattern. This mimics typical non-human-like behavior:

**Movement Patterns**: Moves the cursor in a fixed direction (right, down, left, up) and changes direction every 5 steps.

**Fixed Step Size**: Uses a constant step size for each movement, unlike human movements, which are more variable.

**Time-Based Execution**: Runs for a fixed duration of 10 seconds.

**`runboth.sh` - Execution Script**

The shell script launches the bot simulation in the background and then starts the detection program. This setup allows you to test the effectiveness of the detection algorithm.
