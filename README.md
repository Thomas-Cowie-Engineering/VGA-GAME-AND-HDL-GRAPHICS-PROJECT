# 🐍 VGA Game & HDL Graphics Project

> A Snake-inspired, **hardware-based game** written in Verilog that processes inputs from a game controller and outputs graphics on a **VGA display** — built using VGA Playground.

This repository is for anyone interested in how graphic systems work at the **low-level**: chip design and microelectronics.

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

## 📖 Development Story

### Understanding How VGA Works
