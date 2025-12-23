# DeMoDical
**High-Speed One-Way Optical Communication Bus**  
© 2025 DeMoD LLC. All rights reserved.

![DeMoDical Logo Concept](https://via.placeholder.com/800x400?text=DeMoDical+High-Speed+Unidirectional+Optical+Link)  
*The DeMoDical is a proprietary, affordable, high-performance unidirectional optical data link capable of 40–100+ Gbps. It features a custom programmable digital modulator implemented on FPGA hardware.*

## Overview
The **DeMoDical** (Derived from **De**modulator-**Mo**dulator **Di**gital **Cal**iber) is a cutting-edge one-way communication bus designed for secure, high-speed data transfer applications such as data diodes, industrial sensing, high-frequency trading, or proprietary streaming systems.

Key highlights:
- **Bandwidth**: Up to 100 Gbps raw (4x25 Gbps lanes), 80–95 Gbps effective payload.
- **Unidirectional**: Physically enforced one-way transmission for maximum security.
- **Custom Modulator**: Proprietary FPGA-based logic for flexible encoding, scrambling, FEC, and carrier emulation.
- **Medium**: Multimode fiber via QSFP28 Active Optical Cables (AOCs).
- **Cost-Effective**: Prototype setup under $3,500 using commodity hardware.
- **Low Latency**: <100 ns end-to-end.

This repository provides high-level documentation, illustrative images, hardware recommendations, and conceptual guidance. Core HDL implementations and detailed proprietary designs remain confidential property of DeMoD LLC.

## Illustrative Hardware Components

### Compatible FPGA Development Boards (UltraScale+ with QSFP28)

![XpressVUP-LP9PI FPGA Board](https://www.reflexces.com/wp-content/uploads/2024/07/XpressVUP-LP9PI-top-bot.png)

![BittWare XUPP3R FPGA Board](https://www.skyblue.de/uploads/images/Produktfotos/bittware_xupp3r_xilinx_ultrascale_4x_qsfp_512_gb_sep_to_sep.jpg)

![XUP-VV4 PCIe Card](https://www.bittware.com/files/XUP-VV4-angle-800px.svg)

![Another BittWare XUPP3R View](https://www.zerif.co.uk/uploads/images/Produktfotos/bittware_xupp3r_xilinx_ultrascale_4x_qsfp_512_gb_sep_to_pcie.jpg)

![Powerful FPGA Board Example](https://www.fpgakey.com/uploads/images/editor/20210906/161251RTG4.png)

![Low-Profile Virtex UltraScale+ Board](https://www.mouser.com/Images/reflexces/lrg/XpressVUP-LP5PT2_DSL.jpg)

### QSFP28 Active Optical Cables (AOCs)

![Dell Compatible 100G QSFP28 AOC](https://cdn11.bigcommerce.com/s-ajtn6/images/stencil/1280x1280/products/2703/17359/QSFP28_100G_AOC_Active_Optical_Cable__32156__77763__84168.1724727927.jpg?c=2)

![Finisar/Quadwire 100G QSFP28 AOC](https://www.epsglobal.com/Media-Library/EPSGlobal/Products/files/finisar/transceivers/FCBN425QE1Cxx.jpg?ext=.jpg&maxsidesize=300)

![OptiWorks 100G QSFP28 AOC](https://www.optiworks.com/uploads/images/2906ff9eca17ad7dceb9991db018ea11.jpg)

![QSFP28 to 4xSFP28 Breakout AOC](https://theuncgroup.com/wp-content/uploads/2020/12/qsfp-4sfp-aoc1.png)

## System Architecture & Block Diagrams

![High-Speed Serial Optical Link Block Diagram](https://www.researchgate.net/publication/3244232/figure/fig8/AS:668475534086148@1536388395185/Top-level-transmitter-design-showing-clock-sources-FPGA-microwave-and-optical.png)

![Transmitter and Receiver Architecture](https://www.researchgate.net/publication/224110152/figure/fig3/AS:302712513155090@1449183695998/Architecture-of-transmitter-top-and-the-receiver-bottom-inside-a-transceiver.png)

![GBT-SerDes Block Diagram](https://www.researchgate.net/publication/231077429/figure/fig2/AS:300434943168526@1448640680995/GBT-SerDes-block-diagram.png)

## Unidirectional Enforcement (Optical Data Diode Concepts)

![Data Diode Installation Graphic](https://www.packetpower.com/hs-fs/hubfs/Data%20Diode%20installation%20graphic_HiRes.png?width=2877&height=1875&name=Data%20Diode%20installation%20graphic_HiRes.png)

![Bidirectional vs Unidirectional Comparison](https://www.patton.com/catimg/Bilateral_Bidirectional-Transfers.jpg)

![Data Availability with Diode](https://www.patton.com/catimg/Data-Availability1.jpg)

## Performance
- **Raw Line Rate**: 100 Gbps (4 lanes @ 25.78125 Gbps)
- **BER**: Target <10⁻¹² with proprietary error correction
- **Power**: ~15–25W per node
- **Distance**: Up to 100m (MMF AOC)

## Intellectual Property
© 2025 DeMoD LLC. This project and all associated designs, concepts, and implementations are proprietary. Unauthorized use, reproduction, or distribution is prohibited.

For licensing, partnerships, or custom development inquiries, please contact DeMoD LLC.

## Roadmap
- Commercial prototype kits
- Extended reach variants (SMF)
- Integrated security features

Thank you for your interest in the DeMoDical project!  
— DeMoD LLC Team  
December 23, 2025

**Note**: All images in this README are illustrative examples sourced from public websites for reference purposes. They depict similar hardware and concepts used in the DeMoDical design. Actual implementation may vary.
