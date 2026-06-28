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
## The Game showcased in the VGA playground ( As of writing the project is incomplete. This image is from my current version. The current version outputs a sprite on the screen that can be moved up/down/left/right but I'll expand this to be a snake replica more or less. This will be updated when I have fully finished it).

<img width="959" height="501" alt="image" src="https://github.com/user-attachments/assets/fbfb1d69-64a0-47c6-9042-931455836cc2" />

As you can see there's a sprite in the middle of the screen that can be moved up/down/left/right by pressing the corresponding keys.

## 📖 Development Story (Before synthesis).

### Understanding the Bitmap ROM

<img width="477" height="426" alt="image" src="https://github.com/user-attachments/assets/981fbce9-836c-47e9-86d2-38de30d5c01d" />

This is what the example VGA playground project "Logo" looks like. It's a Tiny Tapeout logo displayed on the screen that bounces around the borders of the screen. You can change the colour of it and do other things by changing the input pins but we'll ignore that feature.

<img width="182" height="146" alt="image" src="https://github.com/user-attachments/assets/471fa533-8c93-4a1d-9b11-de76a7386cea" />

This comes from the "Bitmap_rom.v" module. The module makes a Rom that has 2048 memory addresses where each address stores one byte of data that is the equivallent of 8 pixels. The rom stores a 128x128 frame. Each bit that's a "1" is a pixel of colour (white,blue,red,ect...) and a "0" is a pixel that matches the background colour of your screen (black in the "LOGO" example) to give the illusion that it doesn't exist when it does. Remember, the VGA electron beam goes from the top left of the screen to bottom right so your very first bit will be top left of the frame and your very last bit will be the bottom right of the frame.

#### How do we get sophisticated bitmap images ? Mess around with the bits (pixels) and hope for the best ?

Using this 128x128 bitmap rom system, we simply take an image (the sprite you have made) put it into a software that converts the image into an array of bites and put it back into the rom module. Simple !

I reccomend the website: https://javl.github.io/image2cpp/

