# Technical Notes & Knowledge Base (`tech-notes`)

A curated collection of technical documentation, architectural notes, code snippets, and reference guides focusing on **Linux Kernel Development**, **Device Drivers**, **Multimedia & Camera Capture Pipelines**, and **Embedded Systems Engineering**.

---

## 📌 Topics Covered

### 1. Linux Kernel & Device Drivers
- **V4L2 Framework & Camera Pipelines**: V4L2 sub-devices, media controller architecture, CSI-2 receiver drivers, and buffer queue (`videobuf2`) flows.
- **DMA-BUF & DMA Heaps**: Zero-copy memory sharing, contiguous memory allocation (`/dev/dma_heap/linux,cma`), and DMA buffer management across hardware blocks.
- **Hardware Bus & Interfaces**: I2C, SPI, MIPI CSI-2, LVDS, and BT.656 interfacing and debugging.
- **System Synchronization**: Multi-threading synchronization, non-blocking I/O (`epoll`, `poll`), lockless ring buffers, and concurrency primitives.

### 2. Embedded Systems & BSP
- **Yocto Project & Embedded Build Systems**: Recipe creation, BSP integration, custom image generation, and layer management.
- **System Bring-up & Debugging**: Device Tree (`.dts`/`.dtsi`) configuration, kernel logging (`printk`, dynamic debug), and low-level debugging techniques.
- **Android Camera HAL**: Camera HAL3 architecture, pipeline integration, and vendor extension interfaces.

---

