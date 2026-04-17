# Year-Wise Role of Indian and French Teams

This document describes the detailed year-wise roles and responsibilities of the Indian team (Dr B.R. Ambedkar NIT Jalandhar) and the French team (Université Paris-Est Créteil / Université Gustave Eiffel) within the Multi-Level Optimization (MLO) framework for intelligent robotic assistance to mobility-impaired and dependent individuals. The project spans three years (36 months) and is organized across five work packages (WP1–WP5).

---

## Year 1 (Months 1–12): Foundation — Sensing, Data Collection, and High-Level Algorithm Development

### Indian Team

**Lead responsibility: WP2 — High-Level Perception and Intention Recognition**

- **Experimental protocol co-design (WP1.1):** Collaborate with the French team to finalize the multi-condition, multi-population gait recording protocol, defining sensor placement standards, data formats, synchronization schemes, and annotation guidelines that will be used consistently across both sites.
- **Sensor hardware deployment in India (WP1.2):** Procure and deploy MEMS IMU sensor kits (Xsens DOT or equivalent, ×12 units), flexible plantar pressure insoles (×6 pairs), and the reference motion capture system (VICON Nexus, 10-camera, 250 Hz) with force plates (Kistler 9260AA). Set up the clinical 6-minute walk test track at the Indian site.
- **Indian data collection campaign (WP1.3):** Recruit and record gait data from healthy adult participants at the Indian site under multiple locomotion conditions (level ground, slopes, stairs, varied speeds). Begin building the Indian portion of the Indo-French Gait Variability Dataset (IF-GVD).
- **Feature engineering and preprocessing pipeline (WP2.1):** Design and implement the complete signal processing pipeline for raw IMU and plantar pressure data, including filtering, segmentation, normalization, and feature extraction routines. Establish a shared code repository accessible to both teams.
- **Fuzzy-CNN-GRU model development (WP2.2):** Develop the initial Fuzzy-CNN-GRU hybrid deep learning architecture for gait phase classification. Implement the fuzzy feature extraction layer with parameterized membership functions, 1D convolutional layers for local temporal pattern extraction, and GRU layers for sequential modelling. Train and evaluate baseline models on the Indian data collected in WP1.3.
- **Evolutionary Neural Architecture Search — initial implementation (WP2.3):** Begin implementing the multi-objective evolutionary NAS framework (NSGA-II + Differential Evolution) for automated architecture design of the Fuzzy-CNN-GRU model. Define the search space (number of fuzzy kernels, CNN layers, filter sizes, GRU units, dropout rates, window length) and the bi-objective fitness function (classification accuracy vs. computational cost). Procure and configure the high-performance GPU workstation (NVIDIA A6000) for large-scale NAS experiments.
- **PSO-based hyperparameter optimization (WP2.3):** Implement the Particle Swarm Optimization module for continuous hyperparameter refinement (learning rate, Adam momentum, weight decay, learning rate schedule) of elite architectures identified by the evolutionary NAS.
- **Exchange visits:** Host at least two visits from the French team to align experimental protocols, share preliminary data, and co-develop the data annotation pipeline. Send at least two Indian researchers to the French site for familiarization with the exoskeleton platform and joint experimental planning.

### French Team

**Lead responsibility: WP4 — Low-Level Adaptive Control (initiation)**

- **Experimental protocol co-design (WP1.1):** Co-lead with the Indian team the design of the gait recording protocol, contributing clinical expertise in gait analysis, wearable sensor placement, and biomechanical annotation standards. Ensure that the protocol meets the requirements for clinical populations (elderly, post-stroke) that will be recruited in subsequent years.
- **Sensor hardware deployment in France (WP1.2):** Deploy the wearable sensing platform (IMU arrays, plantar insoles) at the French site. Prepare the lower-limb exoskeleton platform for instrumented experiments. Set up synchronized data acquisition systems.
- **French data collection campaign (WP1.3):** Begin gait recording sessions with healthy adult participants at the French site under the agreed multi-condition protocol. Contribute the French portion of the IF-GVD dataset.
- **Exoskeleton dynamic model identification (WP4.1):** Conduct systematic identification experiments on the lower-limb exoskeleton to characterize the inertial, Coriolis, gravitational, and friction parameters of the coupled human-exoskeleton system. Establish the dynamic model that will serve as the foundation for the ADRC-based controller design.
- **Extended State Observer design and simulation (WP4.2):** Design the third-order Extended State Observer (ESO) for real-time estimation of the total disturbance (model uncertainties, human torque, external perturbations) acting on each exoskeleton joint. Validate the ESO in simulation (MATLAB/Simulink) using the identified dynamic model and synthetic disturbance profiles.
- **σ-AADRC control law derivation (WP4.3 — initiation):** Begin the formal derivation of the σ-modified Adaptive Active Disturbance Rejection Control law, including the sigma-modification adaptive law for observer bandwidth and the Lyapunov stability analysis framework. Draft the initial stability proof establishing uniformly ultimately bounded tracking error.
- **Exchange visits:** Send at least two French researchers to the Indian site for joint protocol calibration and data collection oversight. Host at least two Indian researchers for exoskeleton familiarization and control algorithm co-development.

### Joint Activities (Year 1)

- Establish the shared data repository, version control, and communication infrastructure (monthly video conferences, shared computational resources).
- Jointly publish 2–3 conference papers presenting the sensing architecture, preliminary gait classification results, and the exoskeleton model identification.
- Conduct a joint mid-year review meeting (Month 6) to evaluate progress and synchronize Year 2 planning.

---

## Year 2 (Months 13–24): Core Algorithm Development — Perception Maturation, Trajectory Generation, and Control Refinement

### Indian Team

**Continued lead on WP2; co-lead on WP3 — Mid-Level Trajectory Generation**

- **Complete evolutionary NAS and benchmarking (WP2.3, WP2.5):** Run full-scale multi-objective evolutionary NAS experiments on the combined Indo-French dataset, producing a Pareto front of optimal Fuzzy-CNN-GRU architectures. Benchmark the best architectures against state-of-the-art methods (SVM, LSTM, Transformer) and publish comparative results.
- **Intra-subject variability modelling (WP2.4):** Develop and validate the Gaussian Mixture Model-based intra-subject variability framework, implementing online Bayesian updating to track gait variability modes in real time. Integrate the variability model with the perception output to enable anticipatory adaptation of downstream trajectory and control parameters.
- **Data annotation and quality control (WP1.4):** Complete annotation of the Indian portion of the IF-GVD dataset with gait events, sub-phase labels, and quality flags. Coordinate with the French team for cross-site annotation consistency checks.
- **NvGRF modelling and Optimal Transport implementation (WP3.1, WP3.2):** Develop the normalized vertical Ground Reaction Force estimation model from plantar pressure and IMU data. Implement the Optimal Transport library integration (POT library) and the Sinkhorn solver for entropy-regularized transport computation. Train and validate the NvGRF backup regression model for graceful sensor degradation.
- **Wasserstein barycenter algorithm (WP3.3):** Implement the Wasserstein barycenter algorithm for multi-subject trajectory template generation, with anthropometric similarity-based weighting. Validate on the IF-GVD dataset, demonstrating cross-subject trajectory personalization.
- **Concept drift monitoring (WP3.4):** Implement the sliding-window Kolmogorov-Smirnov test for concept drift detection and the automated re-estimation mechanism for the transport map when drift is detected.
- **Edge computing deployment (WP2, WP3):** Begin porting the Fuzzy-CNN-GRU inference model and the OT trajectory generator to the NVIDIA Jetson Orin NX edge computing units, validating real-time performance (latency, throughput) on embedded hardware.
- **Metaheuristic online tuning — algorithm development (WP4.4 support):** Develop the computationally lightweight Differential Evolution variant for online parameter tuning of the σ-AADRC controller. This module, while deployed at the low level, draws on the Indian team's core expertise in evolutionary optimization. Design the cost function balancing tracking accuracy, torque economy, and saturation avoidance.
- **Exchange visits:** Send researchers to France for joint Optimal Transport validation experiments on French exoskeleton data and for collaborative integration of the DE online tuning module with the control firmware. Host French researchers for joint data analysis and variability model validation.

### French Team

**Continued lead on WP4; co-lead on WP3; initiation of WP5**

- **Complete σ-AADRC derivation and Lyapunov proof (WP4.3):** Finalize the formal derivation and stability proof of the σ-AADRC controller, establishing conditions for uniformly ultimately bounded tracking error. Prepare the theoretical stability proof report (Deliverable D1.4) for submission as a journal article.
- **Metaheuristic DE online tuning — integration (WP4.4):** Integrate the Differential Evolution online tuning module (developed jointly with the Indian team) into the σ-AADRC control firmware. Implement the 200 ms sliding-window evaluation and the 10-individual DE population for real-time parameter adaptation.
- **Hardware-in-the-loop validation (WP4.5):** Conduct hardware-in-the-loop experiments on the exoskeleton platform, validating the σ-AADRC controller with metaheuristic tuning under realistic walking conditions. Measure joint tracking error, torque smoothness, and convergence time after parameter updates.
- **NvGRF and trajectory validation on French data (WP3.1, WP3.5):** Validate the NvGRF estimation and OT-based trajectory personalization algorithms on French site data and exoskeleton kinematic recordings. Test cross-subject generalization performance.
- **French data collection — clinical populations (WP1.3):** Begin recruiting and recording gait data from elderly participants (≥65 years) and post-stroke patients through the affiliated rehabilitation hospital. Expand the IF-GVD dataset with clinical population data.
- **Data annotation and IF-GVD release preparation (WP1.4):** Complete annotation and quality control of the French portion of the IF-GVD dataset. Coordinate with the Indian team for the joint public release (Zenodo/PhysioNet).
- **σ-AADRC controller firmware (Deliverable D1.3):** Develop the C++/ROS2 package for the σ-AADRC controller with embedded DE tuning, preparing it for system integration in Year 3.
- **Exchange visits:** Send researchers to India for joint NAS results analysis, variability model testing, and collaborative edge computing deployment. Host Indian researchers for hardware-in-the-loop experiments and clinical data collection campaigns.

### Joint Activities (Year 2)

- Release the Indo-French Gait Variability Dataset (IF-GVD, Deliverable D2.1) on a public repository.
- Submit 3–4 journal papers covering: evolutionary NAS for biomechanical time series; Optimal Transport for gait adaptation; σ-AADRC stability analysis; and cross-population gait variability analysis.
- Submit 4–5 conference papers (ICRA, IROS, EMBC, BioRob, GECCO).
- Conduct joint mid-year and end-of-year review meetings to plan the system integration strategy for Year 3.
- File the first patent application (India or France, depending on readiness).

---

## Year 3 (Months 25–36): System Integration, Clinical Validation, and Dissemination

### Indian Team

**Co-lead on WP5 — System Integration and Validation**

- **Software integration — perception and trajectory modules (WP5.1):** Integrate the Fuzzy-CNN-GRU perception module and the OT-based trajectory generator into the ROS2 architecture, establishing inter-level communication protocols. Implement the shared memory bus for the context vector (gait phase posterior, sub-phase timing, variability estimate, fatigue indicator) at 50 Hz and the reference trajectory publication at 100 Hz.
- **Supervisory meta-optimizer implementation (WP5.1):** Implement the supervisory meta-optimizer that runs at 1 Hz, monitoring system-wide performance and adjusting the DE cost function weights, Sinkhorn regularization parameter, and NAS architecture selection from the Pareto front in response to evolving user state.
- **Embedded deployment and optimization (WP5.1):** Finalize the deployment of all three MLO levels on the embedded edge computing platform (NVIDIA Jetson Orin NX), optimizing for real-time latency constraints at each level.
- **Healthy subject validation in India (WP5.2):** Conduct integrated system validation with healthy adult participants (N=10 at Indian site) across all five testing scenarios (level ground, terrain transitions, speed variations, perturbation recovery, extended use).
- **Comparative analysis (WP5.4):** Perform statistical comparative analysis of the MLO-assisted condition versus conventional non-adaptive baselines, evaluating metabolic cost reduction, user comfort (NASA-TLX), gait symmetry, and fall/near-fall incidence.
- **Open-source library releases (Deliverables D1.1, D1.2):** Release the open-source Fuzzy-CNN-GRU library with evolutionary NAS support (Python/PyTorch, Apache 2.0) and the Optimal Transport domain adaptation toolkit for gait trajectory personalization (Python, integrated with POT).
- **Exoskeleton Control Benchmark Dataset (Deliverable D2.2):** Compile and release the exoskeleton control benchmark dataset with joint kinematics, kinetics, and control signals from both sites.
- **Patent application (Deliverable D5.3):** File the Indian patent application for commercially valuable innovations from the MLO framework.
- **Technology transfer white paper (Deliverable D5.5):** Co-author the technology transfer white paper targeting industrial partners (Wipro GE Healthcare, others).
- **Exchange visits:** Send researchers to France for joint clinical validation experiments and final demonstrator assembly. Host French researchers for Indian site validation campaigns and final data analysis.

### French Team

**Co-lead on WP5 — System Integration and Clinical Validation**

- **Software integration — control module (WP5.1):** Integrate the σ-AADRC controller firmware (C++/ROS2) into the full MLO stack, establishing the feedforward torque interface from the trajectory generator and the feedback loop from the control level to the perception level.
- **Exoskeleton prototype assembly (Deliverable D3.1):** Complete the instrumented lower-limb exoskeleton prototype (hip-knee-ankle, bilateral) with the embedded MLO stack, including all three optimization levels running in real time.
- **Wearable sensing suit finalization (Deliverable D3.2):** Finalize the wearable sensing suit (IMU + plantar insoles) with real-time data streaming to the edge computing unit.
- **Clinician interface application (Deliverable D3.3):** Develop and deploy the tablet-based user interface application enabling clinicians to configure assistance profiles, monitor system performance, and adjust personalization parameters.
- **Healthy subject validation in France (WP5.2):** Conduct integrated system validation with healthy adult participants (N=10 at French site) across all five testing scenarios.
- **Clinical validation with impaired populations (WP5.3):** Lead the clinical validation trials with elderly participants (N=15) and post-stroke patients (N=10) recruited through the affiliated rehabilitation hospital. Ensure ethical compliance (CPP approval, ICH-GCP guidelines, informed consent). Conduct the five progressive testing scenarios (S1–S5) including the 4-hour extended daily use session (S5) in the structured apartment environment.
- **Comparative analysis (WP5.4):** Contribute exoskeleton-specific performance metrics (RMS joint tracking error, chattering index, actuator saturation, convergence time) to the comparative analysis.
- **Patent application (Deliverable D5.3):** File the French patent application.
- **Industrial partner engagement (Year 3):** Seek letters of intent from industrial partners (Wandercraft SAS, Parker Hannifin) for collaborative product development based on the MLO framework.
- **Exchange visits:** Send researchers to India for joint validation data analysis and final system benchmarking. Host Indian researchers for clinical trial participation and demonstrator finalization.

### Joint Activities (Year 3)

- **Final demonstrator release (Deliverable D3.1):** Demonstrate the complete MLO-equipped exoskeleton prototype at both sites.
- **Indo-French Summer School (Deliverable D5.4):** Organize and deliver the joint Indo-French summer school on "Optimization and AI for Assistive Robotics," bringing together students, researchers, and clinicians from both countries.
- **Publication push:** Submit the remaining journal papers (target: minimum 8 cumulative journal publications in IEEE TNSRE, JNER, RAS, IEEE TEC) and conference papers (target: minimum 12 cumulative, at ICRA, IROS, EMBC, BioRob, GECCO).
- **Final dataset and code release:** Release all open-source code libraries, datasets, and the exoskeleton control benchmark on public repositories.
- **Final review meeting and project closure:** Conduct a comprehensive final review, documenting lessons learned, future research directions, and the technology transfer roadmap.
- **Technology transfer white paper:** Finalize and distribute the white paper to potential industrial licensees in India, France, and internationally.

---

## Summary Table: Year-Wise Lead Responsibilities

| Year | Indian Team (NIT Jalandhar) | French Team (UPEC / UGE) | Joint |
|------|---------------------------|--------------------------|-------|
| **Year 1** (M1–12) | Sensor deployment (India); data collection (India); feature engineering; Fuzzy-CNN-GRU development; evolutionary NAS implementation; PSO hyperparameter tuning | Sensor deployment (France); data collection (France); exoskeleton model identification; ESO design & simulation; σ-AADRC derivation (initiation) | Protocol co-design; shared repository setup; exchange visits (4+); 2–3 conference papers |
| **Year 2** (M13–24) | Full NAS experiments & benchmarking; intra-subject variability modelling; NvGRF estimation; OT implementation; Wasserstein barycenter; concept drift monitor; DE tuning algorithm; edge deployment | σ-AADRC stability proof; DE tuning integration; HIL validation; clinical data collection; controller firmware (ROS2); IF-GVD annotation | IF-GVD public release; 3–4 journal papers; 4–5 conference papers; first patent filing; exchange visits (4+) |
| **Year 3** (M25–36) | Perception & trajectory integration (ROS2); meta-optimizer; embedded deployment; Indian healthy-subject validation; open-source library releases; Indian patent; comparative analysis | Control integration; exoskeleton prototype; clinician UI; French healthy-subject validation; clinical trials (elderly + post-stroke); French patent; industrial engagement | Final demonstrator; Indo-French summer school; remaining publications; dataset & code release; technology transfer white paper; project closure |
