# Project Docs
Basic info on design, system layout, and communication for Hi8 video capture.

---

## 1. Design Notes
- Bare-metal
- UART polling now, DMA/FreeRTOS planned  
- Low-res grayscale for RAM and bandwidth limits  
- Modular to allow upgrades later  
### Analog Signal Considerations
- Composite video = noisy, timing signals (HSYNC, VSYNC)  
- ADV7180 decodes analog to digital  
- Timing and buffering critical to avoid frame drops  
- Trade-offs: resolution, frame rate, MCU limits  

---

## 2. System Overview

`Hi8 Camcorder → ADV7182A → STM32F407 → UART → PC`

- ADV7182A outputs 8-bit grayscale video  
- STM32 captures data via GPIO sync signals  
- Buffer frames in RAM, stream over UART  
- Phase 1 uses simulated frames to implement basic project structure

### Diagram
> TODO data flow diagram here

---

## 3. UART Protocol
- Raw pixel bytes streamed over UART  
- Frame header marks start of frame  
- PC reads stream, reconstructs frames  
- No error correction  

---

## 4. Roadmap

- I2C driver + ADV7182 setup  
- Capture real frames via GPIO  
- DMA/interrupt UART transfer  
- FreeRTOS tasks  
- Color + USB streaming  

---

## 5. Testing Notes 
> TBD

---

## 6. References
- Datasheets
- Documents
