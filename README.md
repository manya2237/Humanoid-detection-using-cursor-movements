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

- ⚙️ Compilation
Compile the programs using gcc:
gcc mouse.c -o mouse -lX11 -lm -lpthread
gcc mouse_bot.c -o mouse_bot -lX11

