# Hi8 Video Capture
A DIY embedded project that captures low-res grayscale video from a Hi8 camcorder using a STM32F407G microcontroller + video decoder and stream to PC via UART 

Developed as a way to bypass unreliable capture cards and lack of analog-to-digital tools, aiming to build a flexible, low-level video pipeline from scratch.

## Purpose & Design Goals
- Build a modular embedded system from scratch that can scale to real inputs and RTOS
- Develop better intuition for real-time constraints: UART bandwidth, memory limits, timing
- Enable future support for real hardware video input and advanced streaming
- Refresh memory and rediscover joy from my Image Processing class
- Move data from tape to computer 

## Project Scope
This project is a bare-metal pipeline for getting video off a Hi8 camcorder and onto a PC. It’s structured around building from the ground up. Right now, it runs a demo that streams simulated grayscale frames over UART. It will eventually:
* Integrate a video decoder over I2C to digitize composite video
* Capture 8-bit grayscale video via GPIO input
* Buffer frames and stream them over UART using DMA
* Use FreeRTOS for clean task separation
* Keep the whole thing modular and flexible for future upgrades
This is built from scratch to explore hands-on how analog signals get converted and streamed, how data flows and bottlenecks happen, and also keeping a transparent, hackable video capture system.

## Constraints and Tradeoffs
- Grayscale, low-res to reduce data size of each frame (3D yCbCr array to 1D)
- Simulated video used initially for early development and debugging to speed up development and implementation
- UART polling for simplicity now; planned move to DMA/interrupts to increase throughput
- Modular drivers for I2C, GPIO, and external decoder 
- Designed to be RTOS-compatible for better task separation

## Hardware & Tools
- MCU: STM32F407G Discvoery Board
- Video Source: Generated / Hi8 camcorder with composite output
- **Decoder: TBD**
- UART to USB adapter

## Quick Start 
> TBD

## Tasks
[] Simulate grayscale video data and stream it over UART
[] Interface with a read video decoder over I2C (driver development + configuration)
[] Switch UART to DMA/interrupt mode
[] Add FreeRTOS task-based architeture 
[] Explore full-res/USB by looking into better MCU and refactor

## About This Project
I work with analog video but lack reliable capture hardware or a CRT setup. Commercial capture cards don’t integrate well, and professional digitization is costly.

This project is my DIY alternative — a low-level, modular pipeline for analog-to-digital video that I can build, understand, and extend. Hopefully, it’ll be useful for other artists and makers working with vintage video formats or at the very least, a love letter to a medium I love.

