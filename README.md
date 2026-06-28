# 🐍 VGA Game & HDL Graphics Project

> A Snake-inspired, **hardware-based game** written in Verilog that processes inputs from a game controller and outputs graphics on a **VGA display** — built using VGA Playground.

This repository is for anyone interested in how the VGA system works, verilog and chip design.

I'll walk through how I built this project as a **tutorial** for those who want to make their own VGA game! 🎮

---

## 📦 Resources Used

| Resource | Description |
|---|---|
| [VGA Playground](https://vga-playground.com/) | Tiny Tapeout emulator used to test the project before synthesis |
| `hsync_generator.v` | Open-source sync module from the playground |
| `bitmap_rom.v` | Bitmap ROM module, modified for this project |
| `gamepad_pmod` | Gamepad input module, modified for this project |

---

## 📚 Pre-requisite Knowledge

> Before diving in, make sure you're comfortable with the following:

- 🖥️ **VGA Physics** — Understanding the VGA input/output signals and the timings.
- ⚙️ **Verilog HDL** — An intermediate level.
- 🎮 **VGA Playground Modules** — Open the VGA Playground **"Logo"** project and familiarise yourself with the `hsync` module:
  - How is the Verilog in this module **driving the VGA monitor**?
  - How is it **manipulating the VGA signals**?
  
  > ⚠️ This module is the **most important one** to understand before proceeding.
## The Game showcased in the VGA playground ( As of writing the project is incomplete. This image is from my current version. This will be updated when I have fully finished it).

<img width="959" height="501" alt="image" src="https://github.com/user-attachments/assets/fbfb1d69-64a0-47c6-9042-931455836cc2" />

As you can see there's a sprite in the middle of the screen that can be moved up/down/left/right by pressing the corresponding keys.

## 📖 Development Story (Before synthesis).

### Understanding the Bitmap ROM

<img width="477" height="426" alt="image" src="https://github.com/user-attachments/assets/981fbce9-836c-47e9-86d2-38de30d5c01d" />

This is what the example VGA playground project "Logo" looks like. It's a Tiny Tapeout logo displayed in the screen that bounces around the borders of the screen. You can change the colour of it and do other things by changing the input pins but we'll ignore that feature.

