# Justification for Consumables and Accessories

This document provides a detailed, item-wise justification for the consumables and accessories budget requested under the Multi-Level Optimization (MLO) framework project for intelligent robotic assistance to mobility-impaired and dependent individuals. Consumables are recurring, expendable items essential for the experimental, computational, and integration activities described in WP1–WP5 and are distinct from the permanent equipment listed separately in the budget.

---

## Indian Team — Consumables and Accessories (Total: ₹7.00 Lakhs over 3 years)

### Year 1: ₹2.00 Lakhs

| Item | Estimated Cost (₹) | Justification |
|------|--------------------:|---------------|
| Replacement IMU sensor straps, mounting brackets, and elastic body harnesses | 30,000 | Twelve Xsens DOT IMU units are deployed on participants during multi-condition gait recording (WP1.2, WP1.3). The neoprene straps, Velcro mounting brackets, and elastic harnesses that secure the IMUs to the lower limbs and trunk are subject to continuous wear from repeated donning/doffing across ≥30 healthy adult participants under varied locomotion conditions (walking, slope ascent/descent, stair climbing). These are consumable-grade textile and polymer components that require periodic replacement to maintain sensor placement accuracy and participant comfort. |
| Replacement plantar pressure insole liners and hygiene covers | 25,000 | The six pairs of flexible plantar pressure insoles (procured under equipment) are placed inside participants' footwear during data collection. Disposable hygiene covers (one set per participant per session) and thin replacement liner membranes are required to maintain sensor hygiene across multiple subjects and to prevent sweat-induced degradation of the piezoelectric sensing elements. Estimated at ~200 sessions × ₹125/set in Year 1. |
| Reflective motion capture markers, adhesive dots, and marker tape | 20,000 | The VICON Nexus 10-camera motion capture system (reference ground truth for WP1.3) requires retroreflective spherical markers (14 mm) placed on anatomical landmarks. Markers are attached with double-sided adhesive dots and supplemented with marking tape. Markers are regularly lost, damaged during dynamic trials, or lose reflectivity after repeated use. Estimated consumption: ~500 markers and 1,000 adhesive sets over Year 1 data collection campaigns. |
| Electrode gel, skin preparation supplies, and medical adhesive tape | 10,000 | Surface preparation (alcohol swabs, abrasive gel) is required for consistent sensor-skin contact during IMU placement, particularly for participants with body hair or perspiration. Medical-grade adhesive tape is used to reinforce IMU mounting during dynamic activities. These are single-use biomedical supplies consumed per participant session. |
| SD cards, USB drives, and portable data storage media | 15,000 | Each IMU sensor kit generates data logged to onboard micro-SD cards. High-endurance industrial-grade micro-SD cards (64 GB, ×12) are procured as consumables due to their finite write-endurance cycle (~10,000 P/E cycles), with replacements needed over intensive data collection campaigns. USB drives are used for data transfer between data acquisition PCs and the shared repository. |
| Cables, connectors, and adapters (USB-C, micro-USB, BNC, Ethernet) | 15,000 | The data acquisition chain involves multiple cable connections: USB-C and micro-USB cables for IMU sensor charging and configuration; BNC cables for force plate connections to the data acquisition unit; Ethernet cables for VICON camera synchronization. Cables in a high-traffic experimental laboratory are subject to bending fatigue, connector wear, and accidental damage, requiring regular replacement. |
| 3D printing filament (PLA/PETG) and rapid prototyping materials | 20,000 | Custom 3D-printed mounting jigs, sensor housings, and anthropometric alignment fixtures are needed for consistent sensor placement across participants with varying body dimensions (WP1.2). The Indian site laboratory's 3D printer consumes PLA and PETG filament for each prototype iteration. Additional silicone casting compounds and heat-shrink tubing are required for custom cable harnesses. |
| Stationery, printed consent forms, clinical record sheets, and annotation materials | 10,000 | Ethical compliance (WP1.3) requires printed informed consent documents, participant information sheets, and clinical screening questionnaires for every enrolled subject. Data annotation protocols (WP1.4) require printed reference charts and codebooks. |
| Participant compensation and refreshments | 30,000 | Healthy adult participants recruited for gait recording sessions (WP1.3) at the Indian site are provided a nominal compensation (₹500–1,000 per session) and refreshments, consistent with institutional ethics board guidelines. Estimated at ~30 participants × 2 sessions average. |
| Miscellaneous lab consumables (batteries, zip ties, cable organizers, cleaning supplies) | 25,000 | General laboratory consumables including rechargeable batteries (AA, AAA) for peripheral devices, cable management materials, anti-static cleaning wipes for optical surfaces (motion capture cameras, force plates), and laboratory hygiene supplies. |

### Year 2: ₹2.50 Lakhs

| Item | Estimated Cost (₹) | Justification |
|------|--------------------:|---------------|
| Replacement IMU straps, insole liners, and motion capture markers (continued) | 30,000 | Continued data collection and annotation activities (WP1.3, WP1.4) with additional participants and multi-session recordings require replenishment of all sensor-mounting consumables. Year 2 includes cross-site consistency validation sessions requiring repeated measurements on the same subjects. |
| Edge computing unit accessories and thermal management consumables | 25,000 | The four NVIDIA Jetson Orin NX edge computing units deployed for embedded algorithm validation (WP2, WP3) require heatsink thermal paste (replacement during re-seating), thermal pads, cooling fans (brushless fans have finite bearing life of ~20,000 hours), power supply cables (barrel jack and USB-C PD), and protective enclosures. Intensive NAS and OT computation sessions generate sustained thermal loads requiring periodic thermal interface material replacement. |
| Micro-SD cards and NVMe SSD storage (edge computing units) | 20,000 | The Jetson Orin NX units use NVMe SSDs for model storage and inference logging. Write-intensive workloads from continuous model retraining and Sinkhorn solver iterations during OT experiments (WP3.2) accelerate SSD wear-levelling limits. Replacement NVMe drives (256 GB, ×4) and high-endurance micro-SD cards are budgeted as consumables. |
| PCB prototyping supplies and electronic components | 30,000 | The custom sensor-to-edge-computing interface board (connecting IMU arrays and plantar insoles to the Jetson Orin NX) requires iterative PCB prototyping. Consumables include FR4 copper-clad boards, solder wire and flux, through-hole and SMD components (connectors, voltage regulators, level shifters, capacitors, resistors), and soldering iron tips. Multiple board revisions are anticipated as the data acquisition architecture evolves during integration. |
| Replacement USB and data cables for edge computing deployment | 15,000 | The embedded deployment workflow requires repeated cable connections between the wearable sensor platform, edge computing units, and development workstations. USB-C cables (data + power delivery rated), UART serial cables, and JTAG debugging cables are subject to connector fatigue during intensive development-debug cycles. |
| 3D printing filament and enclosure materials | 20,000 | Custom enclosures for the Jetson Orin NX units, sensor hub housings, and wearable mounting brackets for the integrated sensing suit (Deliverable D3.2) require multiple 3D printing iterations in PLA, PETG, and flexible TPU filament. Ventilated enclosure designs with integrated cable routing are prototyped and refined across Year 2. |
| Software licenses (annual renewals) and cloud computing credits | 30,000 | Annual license renewals for MATLAB (for cross-validation with French team's Simulink models, WP4 support), and per-use cloud computing credits (AWS/Azure GPU instances for large-scale NAS experiments exceeding local GPU capacity) are treated as consumables. |
| Participant compensation and clinical supplies (expanded recruitment) | 40,000 | Year 2 includes expanded data collection with additional healthy adults (N=10–15) for cross-subject OT validation and preliminary elderly participant screening at the Indian site. Compensation, travel reimbursement, and refreshments for participants. |
| Data backup media (external HDDs, archival tapes) | 15,000 | The growing IF-GVD dataset (WP1.4, D2.1) and the computational artefacts from NAS experiments require redundant offline backup beyond cloud storage. Portable external HDDs (4 TB, ×3) are procured as consumables given their mechanical wear characteristics. |
| Miscellaneous lab consumables | 25,000 | Continuing laboratory consumables: batteries, cleaning supplies, cable management, ESD-safe packaging for component storage, labelling materials for dataset management. |

### Year 3: ₹2.50 Lakhs

| Item | Estimated Cost (₹) | Justification |
|------|--------------------:|---------------|
| Wearable sensing suit consumable components | 35,000 | Final assembly and validation of the wearable sensing suit (Deliverable D3.2) requires replacement straps, fabric mounting panels, Velcro, buckles, conductive thread, and elastic webbing materials. Multiple iterations are anticipated as the sensing suit is fitted to diverse participant body types during healthy-subject validation (WP5.2, N=10 at Indian site). |
| Sensor maintenance and replacement parts | 25,000 | After 24+ months of intensive use, IMU sensor kits and plantar insoles require maintenance: battery replacements (internal Li-Po cells in IMU units), replacement charging cradles, and insole sensor membrane refurbishment. These maintenance items extend the usable life of the equipment investment. |
| Edge computing unit maintenance consumables | 15,000 | Continued thermal management consumables (thermal paste, fans), power cable replacements, and GPIO header maintenance for the Jetson Orin NX units during the intensive system integration phase (WP5.1). |
| 3D printing and rapid prototyping (final demonstrator) | 25,000 | The final integrated MLO demonstrator (Deliverable D3.1, WP5.1) requires custom 3D-printed housings, mounting plates, and cable management fixtures for the complete edge computing + sensor + communication stack mounted on the exoskeleton frame. Final cosmetic and functional enclosures are printed in high-quality PETG and carbon-fibre-reinforced PLA. |
| PCB and electronics consumables (final integration) | 20,000 | Final integration of all three MLO levels requires soldering of final connector assemblies, custom power distribution boards, and signal routing harnesses for the wearable platform. Consumables include solder, flux, heat-shrink tubing, crimped connectors, and ESD-safe packaging. |
| Clinical documentation and ethical compliance materials | 15,000 | Printed informed consent forms, clinical record forms, and participant information sheets for the healthy-subject validation trials at the Indian site (WP5.2). Multi-language documentation as required by the institutional ethics committee. |
| Participant compensation (validation trials) | 40,000 | Healthy adult participants (N=10) for the five-scenario validation protocol (S1–S5) at the Indian site. Each participant undergoes multiple sessions including the 4-hour extended daily use test (S5). Compensation per session: ₹1,000–2,000 plus travel reimbursement. |
| Publication consumables (open-access charges, colour figures) | 30,000 | Open-access publication fees for 2–3 journal papers submitted in Year 3 (IEEE TNSRE, JNER). Colour figure charges for print editions. Conference paper registration fees (partial, for ICRA/IROS/EMBC submissions). |
| Poster printing and summer school materials (Deliverable D5.4) | 20,000 | The joint Indo-French summer school on "Optimization and AI for Assistive Robotics" requires printed materials: participant handbooks, tutorial handouts, large-format poster prints for the poster session, name badges, and certificates. |
| Data archival and final backup | 15,000 | Final backup and archival of the complete IF-GVD dataset, exoskeleton control benchmark dataset (D2.2), and all computational artefacts (trained models, NAS search histories, transport maps) on archival-grade external storage and preparation for Zenodo/PhysioNet upload. |
| Miscellaneous lab consumables | 10,000 | Remaining laboratory consumables for project closeout: cleaning, organization, labelling, and packaging of equipment for continued post-project use. |

---

## French Team — Consumables and Accessories (Total: to be determined by French funding agency guidelines)

The French team's consumables budget supports the exoskeleton experimentation platform, clinical data collection with impaired populations, and hardware-in-the-loop validation. The following categories are justified:

### Year 1

| Item | Justification |
|------|---------------|
| Exoskeleton wear parts (joint bearings, straps, padding, alignment shims) | The lower-limb exoskeleton platform undergoes systematic identification experiments (WP4.1) involving repeated actuation cycles across the full range of motion. Joint bearings, nylon bushings, strapping components, and foam padding are mechanical wear items requiring periodic replacement to maintain experimental safety and measurement accuracy. |
| Force/torque sensor calibration consumables | Strain-gauge-based force/torque sensors on the exoskeleton joints require periodic recalibration using precision calibration weights and jigs. Calibration shunt resistors and contact cleaner are consumable items. |
| Cabling and connectors for exoskeleton instrumentation | Actuator power cables, encoder signal cables, and CAN bus communication cables on the exoskeleton are subject to repeated flexion during walking experiments, leading to fatigue-induced failure. Replacement cables and mil-spec connectors are budgeted as consumables. |
| IMU sensor straps, insole liners, and motion analysis consumables | Same justification as the Indian team: wearable sensor-mounting consumables (straps, hygiene covers, adhesive dots) consumed during French data collection campaigns (WP1.3) with healthy adult participants. |
| 3D printing filament and rapid prototyping materials | Custom sensor mounting brackets, exoskeleton interface adapters, and anthropometric adjustment pieces for the exoskeleton-to-human interface are 3D-printed in engineering-grade materials (PETG, nylon, carbon-fibre-reinforced PLA). |
| Electronic prototyping supplies | Soldering supplies, protoboards, connectors, and passive components for the σ-AADRC controller hardware interface (WP4.2) connecting the ESO to the exoskeleton's real-time control unit (STM32H7). |

### Year 2

| Item | Justification |
|------|---------------|
| Exoskeleton actuator maintenance consumables | Hardware-in-the-loop validation (WP4.5) subjects the exoskeleton actuators (brushless DC motors, harmonic drives) to sustained dynamic loading during realistic walking experiments. Consumables include motor brushes (if applicable), harmonic drive lubricant, bearing grease, and O-ring seals. |
| Controller board consumables (STM32H7 development boards, JTAG cables) | The σ-AADRC firmware development and embedded DE tuning (WP4.4) cycle involves iterative flashing, debugging, and testing on STM32H7 microcontroller development boards. Boards are subject to ESD damage and GPIO pin wear from repeated probe connections. Replacement boards and debug cables are budgeted. |
| Clinical recruitment and participant supplies | Beginning of clinical population recruitment (elderly, post-stroke) through the affiliated rehabilitation hospital (WP1.3, Year 2). Consumables include printed consent forms, clinical screening materials (goniometers, manual muscle testing equipment disposables), participant hygiene supplies, and compensation vouchers. |
| Replacement insole sensors and wearable suit materials | Continued French data collection with expanding participant numbers requires replenishment of plantar insole liners, IMU mounting consumables, and wearable suit components. Clinical populations (elderly, post-stroke) may require larger or custom-fitted insoles and wider strapping systems. |
| Data storage media and backup devices | Expanding dataset size from French healthy and clinical population recordings requires additional NAS-grade HDDs and portable backup drives. |
| MATLAB/Simulink annual license renewal | Continued use of MATLAB/Simulink for σ-AADRC simulation validation and cross-team model verification. |

### Year 3

| Item | Justification |
|------|---------------|
| Exoskeleton final demonstrator assembly consumables | Assembly of the final instrumented exoskeleton prototype (Deliverable D3.1) requires mechanical fasteners, cable glands, heat-shrink tubing, thread-locking compound, and electrical connector assemblies. Custom-machined aluminium adapter plates may require cutting fluid and tooling inserts (consumable). |
| Wearable sensing suit finalization materials | Final assembly of the wearable sensing suit (Deliverable D3.2) including medical-grade elastic fabric, conductive thread, Velcro, snap fasteners, and hypoallergenic skin-contact materials suitable for clinical populations. |
| Clinical trial consumables | Clinical validation with elderly (N=15) and post-stroke (N=10) participants (WP5.3) over multiple testing scenarios (S1–S5) including the 4-hour extended daily use protocol (S5). Consumables include disposable electrode gel, skin preparation supplies, ECG monitoring electrodes (safety monitoring), blood pressure cuff sleeves, participant comfort items, and printed clinical record forms. Ethical compliance requires fresh sets of single-use items for each participant and each session. |
| Participant compensation (clinical populations) | Compensation and travel reimbursement for elderly and post-stroke participants in the clinical validation trials, consistent with CPP (Comité de Protection des Personnes) requirements and ICH-GCP guidelines. |
| Tablet and interface consumables | The clinician interface application (Deliverable D3.3) requires a dedicated tablet device with a protective case. Screen protectors, charging cables, and a tablet mounting stand for the clinical testing environment are consumable accessories. |
| Publication and dissemination consumables | Open-access publication fees for French-led journal submissions. Conference registration fees. Poster and banner printing for the Indo-French summer school (Deliverable D5.4). |
| Patent filing supplies | Administrative consumables associated with the French patent application (Deliverable D5.3): printed specification documents, technical drawings, and filing fees (classified as consumable administrative costs by some funding agencies). |
| Final data archival and packaging | Archival-grade storage media for the complete project dataset, software, and documentation. Packaging materials for equipment handover to continued research use. |

---

## Summary: Why Consumables Are Essential

The consumables budget is a critical enabler for the experimental and integration activities that constitute the core of this project. Unlike permanent equipment (IMU kits, GPU workstation, exoskeleton platform), consumables are items that are physically degraded, chemically depleted, or administratively consumed during normal project activities. Without adequate consumables funding:

1. **Data collection quality would degrade:** Worn sensor straps, degraded adhesive, and contaminated insole liners introduce measurement noise that directly undermines the IF-GVD dataset quality and all downstream algorithmic benchmarks.
2. **Embedded deployment would stall:** Edge computing units operating under sustained thermal loads without replacement thermal interface materials risk throttling or hardware failure during critical NAS and OT experiments.
3. **Clinical validation would be compromised:** Regulatory compliance (IEC in India, CPP in France) mandates fresh single-use consumable supplies for each clinical participant and each session.
4. **Integration iterations would be limited:** The transition from algorithmic development to physical deployment (WP5) inherently requires multiple hardware iteration cycles, each consuming prototyping materials, cables, and electronic components.
5. **Dissemination would be incomplete:** Open-access fees and summer school materials are essential for maximizing the societal impact of the project's scientific contributions.

The requested consumables budget is conservatively estimated based on prior experimental projects of comparable scope and is reinforced by the contingency allocation (10% India, 8% France) to absorb unforeseen cost variations.
