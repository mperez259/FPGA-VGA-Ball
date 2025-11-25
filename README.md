# FPGA VGA Graphics Engine – Bouncing Ball Demo (Nexys A7)

This project implements a real-time **640×480 VGA graphics pipeline** on the **Digilent Nexys A7** FPGA board.  
It includes:

- A fully functional **VGA timing generator**
- A **3×3 hardware ball** with pixel-accurate movement
- **Border collision detection**
- A **parameterized ball module** (easy to scale to 21×21 for “BigBall”)
- A **MATLAB software simulation** that reproduces the Verilog output frame-by-frame

<p align="center">
  <img src="sim/vga_ball.gif" width="600">
</p>

---

## Features

### ✔ VGA Timing Generator
Implements 640×480 @ 60 Hz with:
- 25 MHz pixel tick (from 100 MHz system clock)
- hcount / vcount counters
- hsync / vsync generation
- hblank / vblank detection

### ✔ Hardware Ball Renderer
- Uses `hcount/vcount` from VGA timing
- Renders a **square 3×3 ball** centered at `(xloc, yloc)`
- Movement and collision follow pure Verilog logic
- Parameterized for easy resizing

### ✔ Collision Detection
- Walls are drawn by checking pixel positions:
