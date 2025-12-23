# DeMoDiCaL (WIP)
**High-Speed One-Way Optical Communication Bus**  
© 2025 DeMoD LLC. All rights reserved.

![DeMoDical Conceptual Logo](https://via.placeholder.com/800x400?text=DeMoDical+High-Speed+Unidirectional+Optical+Link)  
*The DeMoDical represents a proprietary advancement in secure, high-performance data transmission, leveraging FPGA technology for custom modulation in unidirectional optical links.*

## Table of Contents
- [Overview](#overview)
- [Key Features](#key-features)
- [Educational Background](#educational-background)
- [System Architecture](#system-architecture)
- [Hardware Requirements](#hardware-requirements)
- [Software and FPGA Implementation](#software-and-fpga-implementation)
- [Installation and Setup](#installation-and-setup)
- [Usage Guide](#usage-guide)
- [Performance Metrics](#performance-metrics)
- [Troubleshooting](#troubleshooting)
- [Intellectual Property and Licensing](#intellectual-property-and-licensing)
- [Roadmap](#roadmap)
- [Contact and Support](#contact-and-support)
- [References and Further Reading](#references-and-further-reading)

## Overview
The **DeMoDical** (an acronym derived from **De**modulator-**Mo**dulator **Di**gital **Cal**iber) is a proprietary, state-of-the-art one-way communication bus engineered by DeMoD LLC for applications demanding ultra-high-speed, secure data transfer. This system excels in scenarios where unidirectional communication is critical, such as in secure network gateways (data diodes), real-time data streaming in industrial environments, high-frequency trading platforms, or proprietary sensor networks.

At its core, the DeMoDical utilizes field-programmable gate array (FPGA) technology to implement a custom digital modulator, enabling flexible data encoding and transmission over optical fibers. Unlike bidirectional protocols like Ethernet or USB, the DeMoDical enforces strict one-way flow, preventing any reverse data leakage and enhancing security in sensitive operations.

This repository serves as a high-level resource hub, offering detailed documentation, conceptual diagrams, and educational insights into the underlying technologies. While the core hardware description language (HDL) code and proprietary implementations remain confidential to protect DeMoD LLC's intellectual property, the materials here aim to educate users on the principles of high-speed optical communication and inspire innovation in similar domains.

## Key Features
- **Ultra-High Bandwidth**: Supports up to 100 Gbps raw throughput (configurable from 40 Gbps), achieved through multi-lane serialization/deserialization (SerDes) technology, with effective payload rates of 80–95 Gbps after accounting for overhead.
- **Strict Unidirectionality**: Physically enforced one-way data flow using transmit-only (TX) optics on the sender and receive-only (RX) on the recipient, ideal for compliance with security standards like those in cybersecurity frameworks (e.g., NIST SP 800-53 for data diodes).
- **Custom Programmable Modulator**: Proprietary FPGA-based logic allows for tailored encoding schemes, including scrambling for data randomization, forward error correction (FEC) for reliability, and modulation formats like on-off keying (OOK) or pulse-amplitude modulation (PAM4).
- **Carrier Signal Emulation**: Embedded clock recovery with optional continuous pseudo-random binary sequence (PRBS) or pilot tones to mimic a carrier signal, ensuring robust synchronization without dedicated hardware.
- **Optical Medium**: Utilizes multimode fiber (MMF) via QSFP28 Active Optical Cables (AOCs) for low-loss, noise-immune transmission over distances up to 100 meters.
- **Cost-Effectiveness**: Leverages commodity FPGA boards and optics, keeping prototype costs under $3,500 while delivering enterprise-grade performance.
- **Low Latency**: End-to-end delays under 100 nanoseconds, suitable for time-sensitive applications.
- **Robustness**: High bit error rate (BER) tolerance (<10⁻¹²) through proprietary error correction, with support for environmental operation from 0–70°C.

## Educational Background
To provide a professional and educational foundation, this section explains key concepts underpinning the DeMoDical design. These explanations are intended for engineers, students, and professionals new to high-speed digital communication.

### What is a Unidirectional Communication Bus?
A unidirectional bus, often implemented as a "data diode," allows data to flow in only one direction. This prevents backflow, making it invaluable for secure systems where information must exit a high-security network without risking ingress (e.g., from a classified to an unclassified zone). Unlike bidirectional links, it uses physical separation—such as TX-only optics—to enforce this, reducing cyber risks.

### FPGA and SerDes Technology
Field-Programmable Gate Arrays (FPGAs) are reconfigurable integrated circuits that allow custom digital logic implementation via HDL like Verilog or VHDL. In the DeMoDical, FPGAs handle the "custom modulator" by processing data streams in parallel and serializing them at gigabit speeds.

Serialization/Deserialization (SerDes) transceivers are high-speed interfaces within FPGAs that convert parallel data (e.g., from memory) into serial streams for transmission. Operating at rates like 25 Gbps per lane, they embed clock signals into the data (using encodings like 64B/66B) to eliminate the need for separate clock lines, improving efficiency and reducing jitter.

### Optical Transmission Basics
Optical links use light (typically infrared lasers) to transmit data over fiber optics, offering advantages over copper: higher bandwidth, lower attenuation, and electromagnetic interference (EMI) immunity. QSFP28 modules (Quad Small Form-factor Pluggable 28) support 100 Gbps by aggregating four 25 Gbps lanes, often via Active Optical Cables (AOCs) that integrate transceivers for plug-and-play use.

### Modulation and Encoding
Modulation alters a carrier signal to encode data. In digital systems like DeMoDical, techniques like PAM4 (four amplitude levels per symbol) double the data rate compared to binary NRZ (non-return-to-zero). Encoding adds redundancy (e.g., FEC) to correct errors caused by noise or dispersion in the fiber.

For further learning, refer to resources like the IEEE 802.3 standards for Ethernet optics or Xilinx/AMD documentation on UltraScale+ transceivers.

## System Architecture
The DeMoDical architecture comprises two primary nodes connected via an optical medium:

- **Transmitter Node**: 
  - Data ingestion from sources like PCIe or internal generators.
  - Proprietary modulation and encoding in FPGA fabric.
  - Serialization via high-speed transceivers.
  - Optical output through QSFP28 TX lanes.

- **Receiver Node**:
  - Optical input via QSFP28 RX lanes.
  - Deserialization and clock recovery.
  - Proprietary decoding and error checking.
  - Data output to host systems.

![High-Speed Serial Optical Link Block Diagram](https://www.researchgate.net/publication/3244232/figure/fig8/AS:668475534086148@1536388395185/Top-level-transmitter-design-showing-clock-sources-FPGA-microwave-and-optical.png)

![Transmitter and Receiver Architecture](https://www.researchgate.net/publication/224110152/figure/fig3/AS:302712513155090@1449183695998/Architecture-of-transmitter-top-and-the-receiver-bottom-inside-a-transceiver.png)

Unidirectionality is enforced at the hardware level, as illustrated below:

![Data Diode Installation Graphic](https://www.packetpower.com/hs-fs/hubfs/Data%20Diode%20installation%20graphic_HiRes.png?width=2877&height=1875&name=Data%20Diode%20installation%20graphic_HiRes.png)

## Hardware Requirements
To replicate a DeMoDical prototype, the following components are recommended:

- **FPGA Development Boards** (One for Transmitter, One for Receiver):
  - AMD/Xilinx Kintex or Virtex UltraScale+ series with at least four 25–28 Gbps transceivers and a QSFP28 cage.
  - Examples:
    - BittWare XUPP3R or similar PCIe cards.
    - Alinx AXVU series evaluation kits.
  - Ensure Vivado compatibility for development.

![XpressVUP-LP9PI FPGA Board](https://www.reflexces.com/wp-content/uploads/2024/07/XpressVUP-LP9PI-top-bot.png)

![BittWare XUPP3R FPGA Board](https://www.skyblue.de/uploads/images/Produktfotos/bittware_xupp3r_xilinx_ultrascale_4x_qsfp_512_gb_sep_to_sep.jpg)

- **Optical Interconnect**:
  - 100G QSFP28 Active Optical Cable (AOC) for MMF, lengths 5–30 meters.
  - For unidirectionality: Use breakout cables (QSFP28 to 4xSFP28) and connect only TX lanes.

![Dell Compatible 100G QSFP28 AOC](https://cdn11.bigcommerce.com/s-ajtn6/images/stencil/1280x1280/products/2703/17359/QSFP28_100G_AOC_Active_Optical_Cable__32156__77763__84168.1724727927.jpg?c=2)

- **Additional Accessories**:
  - Power supplies (board-specific).
  - Host PC with PCIe slots for data interfacing.

Estimated Cost: $2,100–3,600 for a complete prototype pair (2025 pricing).

## Software and FPGA Implementation
Development relies on the AMD Vivado Design Suite for FPGA configuration. The proprietary custom modulator core adapts standards like Aurora 64B/66B for point-to-point links, incorporating:

- Data scrambling to prevent long runs of identical bits.
- FEC for error resilience.
- Lane configuration: 4 lanes at 25.78125 Gbps.
- Validation tools: Integrated Bit Error Rate Tester (IBERT) for signal integrity.

While HDL sources are proprietary, conceptual implementations draw from public frameworks like Corundum (an open-source 100G NIC).

## Installation and Setup
1. **Acquire Hardware**: Purchase recommended FPGA boards and AOCs from vendors like Digi-Key or FS.com.
2. **Install Software**: Download AMD Vivado (free WebPACK edition for supported devices).
3. **Configure FPGA**: Load proprietary bitstreams (available via licensing from DeMoD LLC).
4. **Connect Optics**: Plug QSFP28 AOC between TX (transmitter) and RX (receiver) ports; ensure unidirectional setup by disabling RX on transmitter.
5. **Power On and Test**: Use host software to stream test data and verify link via FPGA debug tools.

Detailed setup diagrams and scripts are provided upon licensing.

## Usage Guide
- **Basic Operation**: Stream data from transmitter host to receiver; monitor via FPGA LEDs or serial console.
- **Advanced Customization**: License holders can modify modulation parameters for specific applications (e.g., adding encryption layers).
- **Example Scenario**: In a data diode setup, connect transmitter to a secure network output and receiver to an external analyzer.

## Performance Metrics
- **Raw Line Rate**: 100 Gbps.
- **Effective Throughput**: 80–95 Gbps.
- **Latency**: <100 ns.
- **BER**: <10⁻¹².
- **Power Consumption**: 15–25W per node.
- **Distance**: Up to 100m with MMF AOCs; extendable with single-mode fiber (SMF) variants.

## Troubleshooting
- **No Link Established**: Check AOC connections, power cycles, and transceiver configurations in Vivado.
- **High BER**: Verify fiber integrity; enable FEC and adjust equalization settings.
- **Overheating**: Ensure adequate cooling for FPGA boards during high-throughput operation.
- For proprietary issues, contact DeMoD LLC support.

## Intellectual Property and Licensing
© 2025 DeMoD LLC. All designs, concepts, and implementations in this repository are proprietary. Reproduction or derivative works require explicit permission. Licensing options are available for commercial use, research, or custom integrations.

## Roadmap
- Q1 2026: Release of commercial prototype kits.
- Q2 2026: SMF extensions for longer distances (up to 10km).
- Q3 2026: Enhanced security features, including hardware encryption modules.

## Contact and Support
For inquiries, licensing, or technical support, please email info@demod.ltd or visit our website at demod.ltd

## References and Further Reading
- AMD/Xilinx UltraScale+ Documentation: [AMD Resources](https://www.amd.com/en/products/adaptive-socs-fpgas.html)
- Optical Networking Standards: IEEE 802.3
- Data Diode Concepts: NIST Guidelines on Secure Data Transfer
- Educational FPGA Tutorials: Xilinx Vitis Tutorials on GitHub

Thank you for exploring the DeMoDical project. We at DeMoD LLC are committed to advancing secure communication technologies.

— DeMoD LLC Team  
December 23, 2025

**Note**: All images are illustrative examples from public sources, depicting similar hardware and concepts. Actual DeMoDical implementations may differ.
