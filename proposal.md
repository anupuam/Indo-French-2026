# Multi-Level Optimization for Intelligent Robotic Assistance to Mobility-Impaired and Dependent Individuals

**Indo-French Joint Research Project Proposal**
**Funding Programme: CEFIPRA / DST-CNRS Joint Research Programme 2026**

---

## Table of Contents

1. [Abstract](#1-abstract)
2. [Introduction & Motivation](#2-introduction--motivation)
3. [Objectives & Hypothesis](#3-objectives--hypothesis)
4. [Scientific and Technical Novelty](#4-scientific-and-technical-novelty)
5. [National Scenario](#5-national-scenario-india)
6. [International Scenario](#6-international-scenario)
7. [Importance of the Proposed Project](#7-importance-of-the-proposed-project)
8. [Literature Review](#8-literature-review)
9. [Proposed Methodology](#9-proposed-methodology)
10. [System Integration](#10-system-integration)
11. [Expected Outcomes & Deliverables](#11-expected-outcomes--deliverables)
12. [Work Plan & Timeline](#12-work-plan--timeline)
13. [Evaluation & Validation](#13-evaluation--validation)
14. [Innovation & Impact](#14-innovation--impact)
15. [Risk Analysis & Mitigation](#15-risk-analysis--mitigation)
16. [Budget Justification](#16-budget-justification)
17. [Conclusion](#17-conclusion)
18. [References](#18-references)

---

## 1. Abstract

Mobility impairment affects hundreds of millions of individuals worldwide, including elderly, post-stroke, and neurologically compromised populations, placing profound burdens on healthcare systems and diminishing quality of life. Current wearable robotic systems, including exoskeletons and powered orthoses, remain limited in their ability to adapt to the high inter- and intra-subject variability of human gait, respond to real-world environmental perturbations, and deliver safe, natural-feeling assistance across diverse activity contexts. These limitations stem from the absence of a unifying design principle that connects perception, planning, and control in a coherent, adaptive manner.

This proposal presents a **Multi-Level Optimization (MLO) framework** for intelligent robotic assistance to mobility-impaired and dependent individuals, in which optimization serves as the architectural backbone across every functional layer of the system. At the **high level**, hybrid deep learning models (Fuzzy-CNN-GRU) combined with evolutionary algorithms (Particle Swarm Optimization, Genetic Algorithms) are deployed for accurate intention recognition and gait phase classification from wearable inertial and plantar sensor data. At the **mid level**, Optimal Transport theory provides a mathematically principled mechanism for domain adaptation in trajectory generation, enabling personalized and biomechanically consistent assistive trajectories under inter-subject variability. At the **low level**, a σ-modified Adaptive Active Disturbance Rejection Control (σ-AADRC) framework, with metaheuristic online parameter tuning, guarantees Lyapunov-stable, smooth, and robust torque delivery.

The project brings together complementary expertise from the Indian PI (evolutionary computation, optimization, and machine learning) and the French PI (wearable robotics, human motion analysis, and adaptive control), establishing a high-impact Indo-French collaboration. Expected outcomes include validated algorithmic frameworks, open-access benchmarking datasets, physical demonstrators on wearable exoskeletons, and translational pathways toward clinical and industrial deployment.

---

## 2. Introduction & Motivation

### 2.1 Background on Assistive Robotics

The global demographic transition toward an ageing population constitutes one of the most significant public health challenges of the 21st century. According to the World Health Organization, approximately 1.3 billion people worldwide live with some form of disability, of whom a substantial proportion suffer from reduced mobility resulting from musculoskeletal disorders, neurological conditions (stroke, Parkinson's disease, spinal cord injury), or age-related decline in neuromuscular function. The economic cost of long-term care exceeds several trillion US dollars globally per annum, and is projected to escalate dramatically as the proportion of individuals aged 65 and above reaches 1.6 billion by 2050.

Wearable robotic systems—including lower-limb exoskeletons, powered ankle-foot orthoses, and hip-assist devices—have emerged as a transformative technology capable of augmenting the locomotion capacity of mobility-impaired individuals. By delivering precisely timed and quantitatively calibrated assistive torques at the major joints of the lower extremity, these systems can (i) compensate for muscle weakness, (ii) restore near-physiological gait biomechanics, (iii) reduce the metabolic energy cost of locomotion, and (iv) provide intensive task-specific rehabilitation training. Seminal commercial systems such as the ReWalk (ReWalk Robotics), Ekso (Ekso Bionics), HAL (Cyberdyne), INDEGO (Parker Hannifin), and Wandercraft Atalante have demonstrated clinical proof of concept in controlled environments. Research platforms, notably the LOPES, ALEX, and MINDWALKER systems, have advanced the scientific understanding of human-robot interaction in gait assistance.

### 2.2 The Core Challenge: Gait Variability and Environmental Complexity

Despite these achievements, existing systems face fundamental challenges that prevent their widespread clinical and community deployment.

**Gait Variability:** Human locomotion is not a stereotyped, periodic pattern but a continuously adaptive neuromechanical process. Even within a single individual, gait kinematics and kinetics exhibit significant cycle-to-cycle variability arising from voluntary motor control, attentional fluctuations, fatigue, neuromuscular noise, and compensatory strategies. Across individuals, variability is compounded by differences in anthropometry, pathology, motor control strategies, footwear, and assistive device experience. Standard gait phase detection algorithms trained on population averages fail to capture this variability and deliver miscalibrated assistance.

**Real-World Environmental Uncertainty:** Most clinical studies evaluate wearable robots on flat, level, obstacle-free treadmill or laboratory floors. In actual living environments, users encounter varied terrain (slopes, stairs, curbs), unstructured surfaces (grass, gravel), and dynamic obstacles. Adequate response to these contexts requires continuous context recognition and rapid trajectory adaptation—capabilities largely absent in current systems.

**Personalization and Calibration:** Current systems require lengthy, expert-guided calibration sessions (often multiple sessions of 2–4 hours) to tune controller parameters for each user. This is prohibitive for clinical scale-up, unsustainable for home use, and completely inapplicable to populations with rapidly varying functional capacity (e.g., stroke recovery patients).

**Stability and Safety:** Mobility-impaired individuals are inherently at high risk for falls. Any robotic assistance must be delivered with guaranteed stability and safety margins; yet existing model-based controllers are sensitive to model uncertainty and unmodeled disturbances, while pure data-driven controllers lack formal safety guarantees.

### 2.3 Research Gap and the Need for an Optimization-Driven Architecture

Existing research has addressed individual layers of the assistive robotics pipeline—perception, trajectory generation, or control—in relative isolation. The absence of a principled, cross-layer integration framework means that improvements at one level do not systematically propagate to others. For example, a highly accurate gait phase classifier produces no benefit if the downstream trajectory generator cannot use that information to modify its output in real time, or if the low-level controller cannot faithfully track the desired trajectory in the presence of disturbances.

Furthermore, existing approaches rely predominantly on manually engineered features, heuristically tuned model architectures, and analytically parameterized controllers. These choices are suboptimal, non-generalizable, and brittle. There is a compelling scientific and engineering need for a **unified optimization paradigm** that automates the design, tuning, and adaptation of each layer while formally guaranteeing their coordinated behavior.

This proposal addresses this gap by treating optimization—evolutionary, metaheuristic, and optimal transport-based—as the fundamental architectural principle across all system levels. The result is a closed-loop architecture in which perception, planning, and control are jointly and continuously optimized, yielding assistive systems that are intelligent by construction.

---

## 3. Objectives & Hypothesis

### 3.1 Central Hypothesis

**We hypothesize that embedding principled optimization methods at every functional level of a wearable robotic assistance system—spanning perception, trajectory generation, and control—creates a synergistic, self-tuning architecture that is demonstrably superior in accuracy, adaptability, safety, and personalization compared to single-level or non-optimization-based designs operating on the same sensing and actuation infrastructure.**

### 3.2 Specific Objectives

**Objective 1 (O1) — High-Level Perception & Intention Recognition:**
Develop and validate a Fuzzy-CNN-GRU hybrid deep learning framework, optimized via evolutionary algorithms (PSO, GA, Differential Evolution), for real-time gait phase classification and user intention recognition from IMU and plantar pressure sensor data, achieving ≥95% classification accuracy across ≥30 subjects under diverse locomotion conditions.

**Objective 2 (O2) — Intra-Subject Variability Modeling:**
Construct probabilistic gait models that explicitly quantify and track intra-subject variability over time, enabling anticipatory adaptation of the assistance strategy to transitions (e.g., flat-to-slope, walk-to-stop) and fatigue-induced gait changes.

**Objective 3 (O3) — Mid-Level Adaptive Trajectory Generation:**
Develop an Optimal Transport-based domain adaptation framework for normalized vertical Ground Reaction Force (NvGRF) estimation and adaptive trajectory synthesis, demonstrating robust generalization to unseen subjects and novel environmental conditions with ≤10% increase in biomechanical deviation versus subject-specific calibrated baselines.

**Objective 4 (O4) — Low-Level Robust Control:**
Design and formally analyze a σ-modified Adaptive Active Disturbance Rejection Control (σ-AADRC) framework for joint torque control in wearable exoskeletons, with metaheuristic-tuned parameters, proving Lyapunov stability, bounded tracking error under matched disturbances, and demonstrating ≤2° RMS joint tracking error at natural walking speeds.

**Objective 5 (O5) — Integrated System Validation:**
Integrate the three-level framework into a complete wearable robotic assistance prototype, validate its performance in real-world locomotion scenarios with mobility-impaired participants (target: elderly individuals ≥65 years and post-stroke patients), and demonstrate statistically significant improvements in safety, comfort, and locomotion efficiency compared to conventional non-adaptive baselines.

---

## 4. Scientific and Technical Novelty

The scientific novelty of this proposal is multi-dimensional and operates at the intersection of machine learning, optimization theory, biomechanics, and control engineering.

**N1 — Cross-Layer Optimization Architecture:** To the best of the authors' knowledge, no existing assistive robotics framework treats optimization as a first-class, cross-layer design principle spanning perception, trajectory generation, and control simultaneously. This proposal establishes the first theoretically grounded and experimentally validated MLO architecture for wearable assistive robots.

**N2 — Evolutionary Neural Architecture Search for Biomechanical Time Series:** Existing neural architecture search (NAS) methods are primarily designed for image classification. This work develops a domain-specific evolutionary NAS formulation for irregular, multivariate, biomechanical time series, incorporating fuzzy-logic kernels as learnable operators within the NAS search space.

**N3 — Optimal Transport for Assistive Gait Adaptation:** While optimal transport has been applied in computer vision domain adaptation, its application to the alignment of biomechanical gait distributions for trajectory generation in assistive robotics is entirely novel. The formulation of an OT-based Wasserstein barycenter for inter-subject trajectory synthesis is a new contribution.

**N4 — σ-AADRC with Metaheuristic Online Tuning:** The σ-modification of ADRC (extending classical ADRC's extended state observer with σ-modification to prevent parameter drift in adaptive systems) combined with metaheuristic real-time tuning constitutes a new control design paradigm. Formal Lyapunov proofs of stability under this combined framework are a new theoretical contribution.

**N5 — Joint Indo-French Human-Centred Robotics Platform:** The project creates a first-of-its-kind multilingual, multicultural, multi-pathology validation dataset and benchmarking platform for wearable assistive robotics, enabling comparisons that account for demographic and anthropometric population differences between Indian and French/European user cohorts.

---

## 5. National Scenario (India)

India faces a compounding challenge at the intersection of demographic ageing, high disability prevalence, and limited healthcare infrastructure. Key national-context facts include:

- According to the 2011 Census of India, approximately **26.8 million persons** live with some form of disability, of whom **20%** have locomotor disabilities—the largest single disability category. This number has grown substantially over the intervening decade.
- The proportion of India's population aged 60 years and above is projected to reach **19.5% by 2050** (approximately 319 million individuals), according to the United Nations Population Fund (UNFPA) India report.
- India has a severe shortfall of physiotherapists and rehabilitation engineers: the WHO recommends 2.5 rehabilitation professionals per 10,000 population; India's current ratio is approximately **0.05 per 10,000**.
- The **Ayushman Bharat** health insurance scheme and the **National Policy for Persons with Disabilities** have created policy frameworks that incentivize development of affordable, domestically manufactured assistive devices.
- Indian research in assistive robotics is growing but remains primarily concentrated at IITs, IISc, and select NITs. Projects funded by DST's **Technology Mission for Differently Abled** and the **National Health Mission** have demonstrated need but reveal significant gaps in adaptive intelligence.
- Indian industry (e.g., Moog India, Wipro GE Healthcare, and emerging deep-tech start-ups) has manufacturing capability that could support cost-competitive local production of wearable robotic systems if the underlying algorithms are made available at appropriate technology readiness levels.
- The Indian PI's research group at [Institution] has established expertise in evolutionary optimization (PSO, GA, DE, Firefly algorithms) applied to neural network design, with prior publications in IEEE Transactions on Evolutionary Computation, Applied Soft Computing, and Expert Systems with Applications.

---

## 6. International Scenario

The global assistive robotics market was valued at approximately USD 2.8 billion in 2023 and is projected to grow at a compound annual growth rate of 22% to reach USD 9.6 billion by 2030 (Grand View Research, 2024). The scientific landscape is characterized by:

- **European Union:** The Horizon Europe programme has prioritized assistive technologies under Cluster 1 (Health), with flagship projects including EUROBENCH (EU benchmark for wearable robots), HARMONIOUS, ACROBAT, and EUROBOTALL. The French research landscape includes INRIA, CEA-List, CNRS LIRMM, and Université Gustave Eiffel, all active in wearable robotics and human motion analysis. The French PI's group has deep competence in gait analysis using wearable sensors and model-predictive control of lower-limb exoskeletons.
- **United States:** NSF Cyber-Physical Systems, NIH National Institute on Aging, and DARPA Warrior Web programs represent major funding streams. Research at MIT (AGE-LAB), Carnegie Mellon (MSR Lab), and University of Michigan has advanced powered prosthetics, exoskeletons, and rehabilitation robots.
- **Japan:** MEXT and JST fund exoskeleton research extensively (Cyberdyne HAL, Honda Walking Assist). Japan's population is the most aged globally, creating a domestic market and regulatory environment highly conducive to deployment.
- **China:** National Key R&D Program has funded large-scale clinical trials of lower-limb exoskeletons (ULS, Fourier X2), and Chinese groups lead in IMU-based gait phase detection.
- **International Standards:** ISO 13482 (Safety Requirements for Personal Care Robots) and IEC 60601 (Medical Electrical Equipment) define the regulatory framework within which this project's outputs will be evaluated.

The proposed project is deliberately positioned to leverage the complementarity between Indian algorithmic innovation in optimization/machine learning and French experimental excellence in wearable robotics and biomechanics, creating a research output that neither partner could achieve independently.

---

## 7. Importance of the Proposed Project in the Context of Current Status

The convergence of three major technological trends makes this project both timely and critical:

1. **Miniaturization of sensing:** Modern MEMS-based IMUs (e.g., STMicroelectronics LSM6DSR) achieve sub-degree angular resolution at gram-level mass. Flexible plantar pressure sensors (e.g., Novel Pedar-X, XSENS) provide dense spatiotemporal force maps. This sensing richness is now available at body-worn scale, enabling rich, continuous physiological and kinematic monitoring that was impossible a decade ago.

2. **AI and Edge Computing Maturity:** Transformer architectures, recurrent deep networks, and neural architecture search have reached sufficient maturity for real-time edge deployment on neuromorphic or RISC-V-based embedded platforms (e.g., Intel Loihi 2, Kendryte K210). Evolutionary optimization algorithms run efficiently on multi-core embedded SoCs, enabling on-body model refinement without cloud connectivity.

3. **Clinical Evidence Base:** Multiple randomized controlled trials (Louie & Eng, 2018; Schwartz et al., 2023) have demonstrated safety and efficacy of lower-limb exoskeletons in stroke rehabilitation. This evidence base creates a regulatory pathway and clinical buy-in that accelerates translation from research prototype to market product.

The proposed project directly addresses the most significant remaining scientific bottleneck: **how to make wearable robotic systems truly adaptive**, learning from each individual user, each step, and each environmental context, while maintaining formal safety guarantees at all times. This problem has not been solved by any existing programme, making the proposed MLO framework a genuinely frontier contribution.

---

## 8. Literature Review

### 8.1 Wearable Assistive Robotics

Lower-limb wearable robots span a spectrum from single-joint devices (powered ankle-foot orthoses, hip exo-suits) to full lower-limb exoskeletons. Asbeck et al. (2015) demonstrated that soft exosuits delivering hip and ankle assistance can reduce metabolic cost by ~23% in healthy subjects. Awad et al. (2017) showed clinically significant improvements in post-stroke gait speed using the Bioness StimRouter. Giovacchini et al. (2015) and Dollar & Herr (2008) provided comprehensive reviews establishing the performance benchmarks for powered prosthetics and orthoses.

**Limitations:** The majority of these systems rely on pre-programmed finite state machines or impedance controllers with manually tuned parameters. They are not designed to adapt to intra-session variability, fatigue, or novel environments. Clinical deployment is hindered by the need for extensive per-user calibration and trained supervision.

### 8.2 Gait Modeling and Prediction

Gait analysis has a long history rooted in optoelectronic motion capture (Vicon, Qualisys) and force plate measurements. The seminal work of Winter (2009) established normative biomechanical parameters. Wearable gait analysis using IMUs was pioneered by Luinge & Veltink (2005) and extended to ambulatory gait phase detection by Rueterbories et al. (2010). Hidden Markov Models (Mannini & Sabatini, 2010) and Support Vector Machines (Taborri et al., 2016) were early ML approaches.

More recent work has applied deep learning: Chen et al. (2020) used LSTMs for gait phase prediction with 93.2% accuracy; Nguyen et al. (2022) proposed a CNN-transformer hybrid achieving 96.4% gait event detection accuracy. Intra-subject variability has received less systematic attention; notable exceptions include Santhiranayagam et al. (2015) who analyzed variability in older adults and Lo et al. (2019) who proposed a Gaussian process model for gait variability.

**Limitations:** Most gait models assume stationarity within a session and do not model distributional shift arising from fatigue, terrain change, or health-status variation. Transfer learning across subjects remains an open problem.

### 8.3 Deep Learning for Time-Series Biomechanics

The application of deep learning to biomechanical time-series has grown rapidly. Bidirectional LSTMs (Phinyomark et al., 2020), temporal convolutional networks (Bai et al., 2018), and attention-based transformers (Zhang et al., 2022) have been applied to activity recognition, gait classification, and joint moment prediction. Fuzzy-CNN hybrids (Cai et al., 2023) have shown particular promise by combining the interpretability of fuzzy rules with the feature learning capacity of convolutional networks. GRU (Gated Recurrent Unit) architectures offer computational efficiency advantages over LSTMs with comparable or superior accuracy on short-duration sequences typical of gait cycles (50–200 timesteps at 100 Hz).

**Limitations:** Existing architectures are designed for single tasks, trained end-to-end on fixed architectures, and not optimized for the specific characteristics of biomechanical data (quasi-periodicity, multivariate coupling, non-stationarity). Neural architecture search (Elsken et al., 2019) has not been systematically applied to this domain.

### 8.4 Evolutionary Optimization in Robotics

Evolutionary algorithms have been applied to robot design optimization (Sims, 1994; Mouret & Clune, 2015), locomotion controller synthesis (Peng et al., 2018), and sensor fusion (Couceiro et al., 2014). PSO (Kennedy & Eberhart, 1995) has been used for PID tuning in exoskeleton control (Li et al., 2021) and hyperparameter optimization of neural networks (Lorenzo et al., 2017). Neuroevolution approaches (Stanley & Miikkulainen, 2002) co-evolve network topology and weights.

**Limitations:** Most applications tune parameters offline in simulation; online evolutionary adaptation in real-time wearable systems is nascent due to computational constraints. Domain-specific evolutionary operators for biomechanical time-series models have not been developed.

### 8.5 Adaptive and Robust Control Systems

Active Disturbance Rejection Control (ADRC), introduced by Han (2009) and refined by Gao (2006), provides a model-free disturbance rejection framework using an Extended State Observer (ESO) to estimate total disturbance. ADRC has been applied to exoskeleton control by Zhao et al. (2015) and to prosthetic limb control by Huang et al. (2019). Adaptive ADRC variants (Chen et al., 2018) incorporate gain adaptation laws. The σ-modification (Ioannou & Kokotovic, 1984) prevents parameter drift in adaptive systems under persistent excitation conditions, a critical property in cyclic human locomotion.

**Limitations:** Standard ADRC parameter tuning relies on frequency-domain analysis assuming constant disturbance bandwidth—an assumption violated in dynamic locomotion. Lyapunov-based stability analyses of adaptive ADRC under time-varying disturbances are incomplete in the literature. The combination of σ-modification with metaheuristic online tuning has not been formally analyzed or experimentally demonstrated.

---

## 9. Proposed Methodology

The proposed Multi-Level Optimization (MLO) architecture is organized into three vertically integrated levels, as illustrated schematically below. Each level receives signals from lower levels (actuation feedback) and sends commands downward, while simultaneously sharing information horizontally with adjacent levels through a shared context representation.

```
┌─────────────────────────────────────────────────────────┐
│           HIGH-LEVEL OPTIMIZATION (Level 1)             │
│   Perception: IMU + Plantar Sensors                     │
│   Fuzzy-CNN-GRU + Evolutionary NAS                      │
│   Output: Gait Phase, Intention, Variability Model      │
└──────────────────────┬──────────────────────────────────┘
                       │ Context Vector c(t)
┌──────────────────────▼──────────────────────────────────┐
│           MID-LEVEL OPTIMIZATION (Level 2)              │
│   Trajectory Generation: OT-based Domain Adaptation     │
│   NvGRF Estimation + Gait Sub-Phase Detection           │
│   Output: Reference Joint Trajectories θ_ref(t)         │
└──────────────────────┬──────────────────────────────────┘
                       │ θ_ref(t), τ_ff(t)
┌──────────────────────▼──────────────────────────────────┐
│           LOW-LEVEL OPTIMIZATION (Level 3)              │
│   σ-AADRC + Metaheuristic Parameter Tuning              │
│   Output: Actuator Torques τ(t)                         │
└──────────────────────┬──────────────────────────────────┘
                       │ Measured θ(t), dθ/dt(t)
                  [Wearable Robot Hardware]
                       │
                       └──── Feedback to all levels
```

---

### 9(A) High-Level Optimization: Perception and Intention Recognition

#### 9.A.1 Sensing Architecture

The sensing subsystem comprises:
- **Six degree-of-freedom IMUs (MEMS):** Placed at the shank, thigh, and trunk segments (6 units per leg), capturing 3-axis linear accelerations $\mathbf{a}(t) \in \mathbb{R}^3$ and angular velocities $\boldsymbol{\omega}(t) \in \mathbb{R}^3$ at 200 Hz.
- **Plantar pressure insoles:** Flexible capacitive sensor arrays (16 sensing elements per foot) measuring the spatiotemporal plantar pressure distribution $P(x, y, t) \in \mathbb{R}^{16}$ at 100 Hz.

The raw sensor fusion problem is formulated as:

$$\mathbf{x}(t) = \left[\mathbf{a}_L(t),\, \boldsymbol{\omega}_L(t),\, \mathbf{a}_R(t),\, \boldsymbol{\omega}_R(t),\, \mathbf{a}_T(t),\, \boldsymbol{\omega}_T(t),\, P_L(t),\, P_R(t)\right]^\top \in \mathbb{R}^{d}$$

where subscripts $L$, $R$, $T$ denote left leg, right leg, and trunk, and $d = 6 \times 6 + 2 \times 16 = 68$.

#### 9.A.2 Fuzzy-CNN-GRU Architecture

The core perception model is a **Fuzzy-CNN-GRU** hybrid network that processes the multivariate time-series $\mathbf{x}(t)$ in a sliding window of length $W = 100$ timesteps (0.5 s).

**Fuzzy Feature Extraction Layer:** A bank of $K$ fuzzy kernel functions parameterized by centers $\mathbf{c}_k \in \mathbb{R}^d$ and bandwidths $\sigma_k > 0$ transforms raw sensor data:

$$\phi_k(\mathbf{x}(t)) = \exp\left(-\frac{\|\mathbf{x}(t) - \mathbf{c}_k\|^2}{2\sigma_k^2}\right), \quad k = 1, \ldots, K$$

The fuzzy feature vector is $\boldsymbol{\phi}(t) = [\phi_1(t), \ldots, \phi_K(t)]^\top \in \mathbb{R}^K$.

**CNN Layers:** A stack of $N_c$ 1D convolutional layers with filters $\mathbf{W}_i \in \mathbb{R}^{F_i \times C_{i-1}}$ and ReLU activations extract local temporal patterns:

$$\mathbf{h}_i^{\text{CNN}}(t) = \text{ReLU}\left(\mathbf{W}_i * \mathbf{h}_{i-1}(t) + \mathbf{b}_i\right)$$

**GRU Layers:** Two stacked GRU layers process the CNN output sequence to capture long-range temporal dependencies:

$$\mathbf{r}_t = \sigma\left(\mathbf{W}_r [\mathbf{h}_{t-1}, \mathbf{x}_t] + \mathbf{b}_r\right)$$
$$\mathbf{z}_t = \sigma\left(\mathbf{W}_z [\mathbf{h}_{t-1}, \mathbf{x}_t] + \mathbf{b}_z\right)$$
$$\tilde{\mathbf{h}}_t = \tanh\left(\mathbf{W}_h [\mathbf{r}_t \odot \mathbf{h}_{t-1}, \mathbf{x}_t] + \mathbf{b}_h\right)$$
$$\mathbf{h}_t = (1 - \mathbf{z}_t) \odot \mathbf{h}_{t-1} + \mathbf{z}_t \odot \tilde{\mathbf{h}}_t$$

**Output Layer:** A softmax classification head produces posterior probabilities over $M$ gait phases (typically $M=8$: initial contact, loading response, mid-stance, terminal stance, pre-swing, initial swing, mid-swing, terminal swing):

$$\hat{p}_m(t) = \frac{\exp(\mathbf{w}_m^\top \mathbf{h}_T + b_m)}{\sum_{j=1}^M \exp(\mathbf{w}_j^\top \mathbf{h}_T + b_j)}$$

The full parameter set of the Fuzzy-CNN-GRU model is:

$$\boldsymbol{\Theta} = \{\mathbf{c}_k, \sigma_k\}_{k=1}^K \cup \{\mathbf{W}_i, \mathbf{b}_i\}_{i=1}^{N_c} \cup \{\mathbf{W}_r, \mathbf{W}_z, \mathbf{W}_h, \mathbf{b}_r, \mathbf{b}_z, \mathbf{b}_h\} \cup \{\mathbf{w}_m, b_m\}_{m=1}^M$$

#### 9.A.3 Evolutionary Neural Architecture Search (Evo-NAS)

Instead of manually designing the architecture, we formulate a **multi-objective evolutionary NAS** problem. The search space $\mathcal{A}$ includes:
- Number of fuzzy kernels $K \in \{8, 16, 32, 64\}$
- Number of CNN layers $N_c \in \{1, 2, 3, 4\}$
- CNN filter sizes $F_i \in \{3, 5, 7, 11\}$
- Number of GRU units $G \in \{32, 64, 128, 256\}$
- Dropout rates $\delta \in [0, 0.5]$
- Window length $W \in \{50, 100, 150, 200\}$

Each candidate architecture $\alpha \in \mathcal{A}$ is encoded as a chromosome $\mathbf{g}_\alpha$ and evaluated on a validation set. The bi-objective optimization is:

$$\min_{\alpha \in \mathcal{A}} \quad \mathcal{F}(\alpha) = \left[\mathcal{L}_{\text{val}}(\alpha),\; \mathcal{C}(\alpha)\right]$$

where $\mathcal{L}_{\text{val}}(\alpha)$ is the validation cross-entropy loss and $\mathcal{C}(\alpha)$ is the computational cost (FLOPs per inference). This multi-objective formulation yields a Pareto-optimal set of architectures, from which the practitioner selects based on the deployment hardware constraints.

**PSO-based Hyperparameter Optimization:**

Let the hyperparameter vector be $\boldsymbol{\lambda} = [\eta, \beta_1, \beta_2, \lambda_{\text{wd}}, \gamma_{\text{lr}}]$ (learning rate, Adam momentum coefficients, weight decay, learning rate decay). Each particle in the PSO swarm is $\boldsymbol{\lambda}^{(i)} \in \mathbb{R}^5$. The velocity and position updates are:

$$\mathbf{v}^{(i)}(t+1) = \omega \mathbf{v}^{(i)}(t) + c_1 r_1 \left[\mathbf{p}^{(i)} - \boldsymbol{\lambda}^{(i)}(t)\right] + c_2 r_2 \left[\mathbf{g} - \boldsymbol{\lambda}^{(i)}(t)\right]$$
$$\boldsymbol{\lambda}^{(i)}(t+1) = \boldsymbol{\lambda}^{(i)}(t) + \mathbf{v}^{(i)}(t+1)$$

where $\omega$ is the inertia weight, $c_1, c_2$ are cognitive and social coefficients, $r_1, r_2 \sim \mathcal{U}(0,1)$, $\mathbf{p}^{(i)}$ is the personal best, and $\mathbf{g}$ is the global best position.

**Algorithm 1: Evolutionary Neural Architecture Search for Gait Phase Classification**

```
INPUT:  Sensor dataset D = {(x(t), y(t))}, population size N_pop, generations G_max
OUTPUT: Pareto-optimal architecture set A*

Initialize population P = {g_1, ..., g_{N_pop}} randomly from search space A
Evaluate F(alpha_i) for all i in parallel (train and evaluate each architecture)
Set Pareto front PF = non-dominated_sort(P)

FOR gen = 1 TO G_max DO
    // Selection
    parents = tournament_selection(PF, size=N_pop/2)
    
    // Crossover (uniform crossover on architecture chromosomes)
    offspring = crossover(parents)
    
    // Mutation (random perturbation of discrete/continuous hyperparameters)
    offspring = mutate(offspring, p_mut=0.15)
    
    // Evaluation
    FOR each alpha in offspring DO
        Train Fuzzy-CNN-GRU(alpha) on D_train
        Evaluate [L_val(alpha), C(alpha)] on D_val
    END FOR
    
    // Environmental selection (NSGA-II)
    P_combined = P ∪ offspring
    PF = NSGA-II_selection(P_combined, size=N_pop)
    
    // PSO phase for continuous hyperparameter refinement
    FOR each elite alpha in top_10%(PF) DO
        lambda = PSO_optimize(alpha, D_val, swarm_size=30, T_PSO=50)
        Update weights of Fuzzy-CNN-GRU(alpha) with lambda
    END FOR
END FOR

RETURN A* = PF
```

#### 9.A.4 Intra-Subject Variability Modeling

To model intra-subject variability, gait cycles are clustered into $C$ variability modes using a Gaussian Mixture Model (GMM):

$$p(\mathbf{x}) = \sum_{c=1}^{C} \pi_c \, \mathcal{N}(\mathbf{x};\, \boldsymbol{\mu}_c, \boldsymbol{\Sigma}_c)$$

The parameters $\{\pi_c, \boldsymbol{\mu}_c, \boldsymbol{\Sigma}_c\}_{c=1}^C$ are estimated via Expectation-Maximization (EM) on a per-subject, per-session basis. Online Bayesian updating propagates evidence from new gait cycles to the posterior:

$$p(\boldsymbol{\theta}_c \mid \mathbf{x}_{1:t}) \propto p(\mathbf{x}_t \mid \boldsymbol{\theta}_c) \, p(\boldsymbol{\theta}_c \mid \mathbf{x}_{1:t-1})$$

This variability model feeds an anticipatory mechanism that pre-adjusts the trajectory generator and controller parameters based on predicted upcoming gait state transitions.

---

### 9(B) Mid-Level Optimization: Trajectory Generation

#### 9.B.1 Normalized Vertical Ground Reaction Force (NvGRF) Modeling

Vertical ground reaction forces (vGRF) provide the canonical biomechanical signature of gait sub-phases (heel-strike, flat-foot, heel-off, toe-off). From plantar pressure insoles, the discrete vGRF proxy is:

$$F_v(t) = \sum_{j=1}^{16} A_j \cdot P_j(t)$$

where $A_j$ is the effective area of the $j$-th pressure sensing element. Normalization by body weight $W_b$ yields:

$$\tilde{F}_v(t) = \frac{F_v(t)}{W_b}$$

A data-driven regression model $\hat{F}_v = f_\psi(\mathbf{x}(t))$ parameterized by $\boldsymbol{\psi}$ (a separate lightweight neural network) is trained to estimate $\tilde{F}_v(t)$ from IMU data when plantar sensors are temporarily unavailable (graceful degradation).

Gait sub-phases are detected via threshold crossings on $\tilde{F}_v(t)$ and its first derivative:

| Sub-Phase         | $\tilde{F}_v$ Condition                  | Duration (% gait cycle) |
|-------------------|------------------------------------------|------------------------|
| Initial Contact   | $\tilde{F}_v$ rising from zero           | 0–2%                   |
| Loading Response  | $\tilde{F}_v > 1.0$ (first peak)         | 2–12%                  |
| Mid-Stance        | $\tilde{F}_v$ valley around 0.75         | 12–31%                 |
| Terminal Stance   | $\tilde{F}_v > 1.0$ (second peak)        | 31–50%                 |
| Pre-Swing         | $\tilde{F}_v$ declining to zero          | 50–62%                 |
| Swing Phases      | $\tilde{F}_v \approx 0$                  | 62–100%                |

#### 9.B.2 Optimal Transport for Domain Adaptation

Let $\mu_s = \frac{1}{N_s}\sum_{i=1}^{N_s} \delta_{\mathbf{q}_i^s}$ be the empirical gait distribution of a **source subject** $s$ (with annotated trajectories), and $\mu_t = \frac{1}{N_t}\sum_{j=1}^{N_t} \delta_{\mathbf{q}_j^t}$ be the distribution of a **target subject** $t$ (new user, minimal annotations). Here $\mathbf{q}^s, \mathbf{q}^t \in \mathbb{R}^p$ denote gait feature vectors (joint angles, NvGRF, phase labels, anthropometric descriptors).

The **Wasserstein-2 distance** between source and target is:

$$W_2(\mu_s, \mu_t) = \left(\inf_{\gamma \in \Gamma(\mu_s, \mu_t)} \int_{\mathbb{R}^p \times \mathbb{R}^p} \|\mathbf{q}^s - \mathbf{q}^t\|^2 \, d\gamma(\mathbf{q}^s, \mathbf{q}^t)\right)^{1/2}$$

where $\Gamma(\mu_s, \mu_t)$ is the set of all joint distributions (transport plans) with marginals $\mu_s$ and $\mu_t$.

The optimal transport map $T^* : \mathbb{R}^p \to \mathbb{R}^p$ is obtained via solution of the discrete optimal transport problem using the Sinkhorn algorithm (Cuturi, 2013):

$$\mathbf{P}^* = \arg\min_{\mathbf{P} \in \mathcal{U}(\mathbf{a}, \mathbf{b})} \langle \mathbf{C}, \mathbf{P} \rangle - \epsilon \, H(\mathbf{P})$$

where $\mathbf{C}_{ij} = \|\mathbf{q}_i^s - \mathbf{q}_j^t\|^2$ is the cost matrix, $H(\mathbf{P}) = -\sum_{ij} P_{ij} \log P_{ij}$ is the entropic regularization, $\epsilon > 0$ is the regularization parameter, and $\mathcal{U}(\mathbf{a}, \mathbf{b})$ is the set of doubly stochastic matrices with marginals $\mathbf{a} = \mathbf{1}/N_s$ and $\mathbf{b} = \mathbf{1}/N_t$.

The transported target representation $\hat{\mathbf{q}}^t_j = T^*(\mathbf{q}^t_j) = \sum_i P^*_{ij} \mathbf{q}^s_i / a_i$ aligns the target distribution to the source, enabling direct application of source-domain trajectory models to the target subject.

**Wasserstein Barycenter for Multi-Subject Template Generation:**

To create a personalized trajectory template for a new user from a library of $S$ reference subjects, we compute the **Wasserstein barycenter**:

$$\bar{\mu} = \arg\min_{\mu} \sum_{s=1}^{S} \lambda_s \, W_2^2(\mu, \mu_s)$$

subject to $\sum_s \lambda_s = 1$, $\lambda_s \geq 0$. The weights $\lambda_s$ are set inversely proportional to the anthropometric distance between the new user and subject $s$ (using height, mass, leg length, and gait speed). This yields a personalized reference trajectory that interpolates between reference subjects in the optimal transport sense, respecting the Riemannian geometry of the space of probability distributions.

**Algorithm 2: OT-Based Personalized Trajectory Synthesis**

```
INPUT:  Library {mu_s, traj_s}_{s=1}^S (source subjects with reference trajectories)
        New user u: anthropometrics a_u, initial gait data D_u (limited)
        Regularization epsilon, iterations T_sinkhorn
OUTPUT: Personalized reference trajectory traj_u

// Step 1: Compute anthropometric similarity weights
FOR s = 1 TO S DO
    d_s = ||a_u - a_s|| / sigma_a   // normalized anthropometric distance
    lambda_s = exp(-d_s) / Z         // Z = normalizing constant
END FOR

// Step 2: Compute Wasserstein barycenter
Initialize barycenter distribution mu_bar = lambda_1 * mu_1
FOR iter = 1 TO T_iter DO
    FOR s = 1 TO S DO
        P_s* = Sinkhorn(mu_bar, mu_s, C_s, epsilon, T_sinkhorn)
        T_s = compute_transport_map(P_s*)
    END FOR
    mu_bar = (1/S) * sum_s T_s # (mu_bar)  // update barycenter
END FOR

// Step 3: Adapt trajectories from source to user
FOR s = 1 TO S DO
    traj_u_s = T_s(traj_s)  // push forward trajectory through transport map
END FOR
traj_u = sum_s lambda_s * traj_u_s  // weighted combination

// Step 4: Online refinement with user-specific data
IF |D_u| > N_min THEN
    traj_u = fine_tune(traj_u, D_u, eta_finetune)
END IF

RETURN traj_u
```

#### 9.B.3 Concept Drift Handling

Under repeated use, the distribution of a user's gait may drift (due to fatigue, recovery progress, or seasonal variation). A sliding window Kolmogorov-Smirnov test monitors the stationarity of incoming gait features:

$$\text{KS-statistic} = \sup_{\mathbf{q}} \left|F_{1:t}(\mathbf{q}) - F_{t-W:t}(\mathbf{q})\right|$$

When the KS-statistic exceeds a threshold $\tau_{\text{KS}}$, the optimal transport map is re-estimated from recent data, updating the personalized trajectory template.

---

### 9(C) Low-Level Optimization: Robust Control

#### 9.C.1 System Model

Consider the $n$-DOF wearable exoskeleton with Lagrangian dynamics:

$$\mathbf{M}(\mathbf{q})\ddot{\mathbf{q}} + \mathbf{C}(\mathbf{q}, \dot{\mathbf{q}})\dot{\mathbf{q}} + \mathbf{G}(\mathbf{q}) + \boldsymbol{\tau}_h + \mathbf{d}(t) = \boldsymbol{\tau}_c$$

where:
- $\mathbf{q}, \dot{\mathbf{q}}, \ddot{\mathbf{q}} \in \mathbb{R}^n$ are joint angles, velocities, accelerations
- $\mathbf{M}(\mathbf{q}) \in \mathbb{R}^{n \times n}$ is the inertia matrix
- $\mathbf{C}(\mathbf{q}, \dot{\mathbf{q}}) \in \mathbb{R}^{n \times n}$ is the Coriolis/centrifugal matrix
- $\mathbf{G}(\mathbf{q}) \in \mathbb{R}^n$ is the gravity vector
- $\boldsymbol{\tau}_h \in \mathbb{R}^n$ is the human joint torque (measured via force sensors or estimated)
- $\mathbf{d}(t) \in \mathbb{R}^n$ is total disturbance (modeling errors, external perturbations)
- $\boldsymbol{\tau}_c \in \mathbb{R}^n$ is the control torque

Rewriting in the ADRC canonical form (scalar case per joint for clarity, subscript $j$ dropped):

$$\ddot{q} = \frac{1}{M_0}\tau_c + f(q, \dot{q}, d, t)$$

where $M_0$ is a nominal scalar inertia and $f(\cdot)$ is the "total disturbance" (generalized, unknown, bounded):

$$f = \frac{1}{M(\mathbf{q})}\left[-C(\mathbf{q},\dot{\mathbf{q}})\dot{\mathbf{q}} - G(\mathbf{q}) - \tau_h - d(t)\right] + \left(\frac{1}{M_0} - \frac{1}{M(\mathbf{q})}\right)\tau_c$$

#### 9.C.2 Extended State Observer (ESO)

A third-order ESO estimates both state and total disturbance:

$$\begin{cases}
\dot{\hat{q}} = \hat{\dot{q}} + \beta_1 (q - \hat{q}) \\
\dot{\hat{\dot{q}}} = \hat{f} + \frac{\tau_c}{M_0} + \beta_2 (q - \hat{q}) \\
\dot{\hat{f}} = \beta_3 (q - \hat{q})
\end{cases}$$

where $[\beta_1, \beta_2, \beta_3] = [3\omega_o, 3\omega_o^2, \omega_o^3]$ are observer bandwidth parameters derived from characteristic root placement at $-\omega_o$ (observer bandwidth). The ESO error dynamics satisfy:

$$\dot{\mathbf{e}}_o = \mathbf{A}_o \mathbf{e}_o + \mathbf{B}_o \dot{f}(t)$$

where $\mathbf{e}_o = [q - \hat{q}, \dot{q} - \hat{\dot{q}}, f - \hat{f}]^\top$, and $\mathbf{A}_o$ is Hurwitz. Under bounded disturbance rate $|\dot{f}| \leq \Delta_f$, the ESO error is uniformly ultimately bounded (UUB):

$$\limsup_{t \to \infty} \|\mathbf{e}_o(t)\| \leq \frac{c\Delta_f}{\omega_o}$$

#### 9.C.3 σ-Modified Adaptive ADRC (σ-AADRC)

Standard ADRC uses fixed observer bandwidth $\omega_o$. For a system with time-varying disturbance spectrum (as in locomotion), adaptive tuning is necessary. An adaptive law updates $\omega_o(t)$:

$$\dot{\omega}_o = -\gamma_o \, \mathbf{e}_o^\top \mathbf{P}_o \mathbf{B}_o (q - \hat{q}) - \sigma_o \, \omega_o$$

The **σ-modification term** $-\sigma_o \omega_o$ (with $\sigma_o > 0$ a small leakage constant) prevents the parameter $\omega_o$ from drifting to infinity under persistent bounded inputs, ensuring:

$$\omega_o(t) \in [\omega_{\min}, \omega_{\max}] \quad \forall t \geq 0$$

The control law (feedback linearization with disturbance compensation):

$$\tau_c = M_0 \left[k_p (q_{\text{ref}} - \hat{q}) + k_d (\dot{q}_{\text{ref}} - \hat{\dot{q}}) + \ddot{q}_{\text{ref}} - \hat{f}\right]$$

A bounded control modification prevents actuator saturation:

$$\tau_c^{\text{sat}} = \begin{cases} \tau_{\max} \cdot \text{sign}(\tau_c) & \text{if } |\tau_c| > \tau_{\max} \\ \tau_c & \text{otherwise} \end{cases}$$

#### 9.C.4 Lyapunov Stability Analysis

**Theorem (σ-AADRC Stability):** *Consider the exoskeleton system under the σ-AADRC controller with ESO observer. If the disturbance satisfies $\|f(t)\| \leq f_{\max}$ and $\|\dot{f}(t)\| \leq \Delta_f$, and the gain parameters satisfy:*

$$k_p > 0, \quad k_d > 0, \quad k_p k_d > \Delta_f / f_{\max}$$

*then the closed-loop system is uniformly ultimately bounded (UUB), with ultimate bound:*

$$\|[e_q, \dot{e}_q]^\top\| \leq \frac{\sqrt{(k_p + k_d)}}{\min(k_p, k_d)} \cdot \frac{c\Delta_f}{\omega_o} + \varepsilon$$

*where $e_q = q_{\text{ref}} - q$ is the tracking error and $\varepsilon > 0$ can be made arbitrarily small by increasing $\omega_o$.*

**Proof sketch:** Define Lyapunov candidate:
$$V(t) = \mathbf{e}_c^\top \mathbf{P}_c \mathbf{e}_c + \mathbf{e}_o^\top \mathbf{P}_o \mathbf{e}_o + \frac{1}{2\gamma_o}(\omega_o - \omega_o^*)^2$$

where $\mathbf{e}_c = [e_q, \dot{e}_q]^\top$ is the control error, $\mathbf{P}_c, \mathbf{P}_o$ are positive definite solutions to Lyapunov equations for the closed-loop control and observer matrices respectively, and $\omega_o^* > 0$ is the optimal observer bandwidth. Taking $\dot{V}(t)$ along system trajectories and applying the σ-modification bound and the UUB result for the ESO yields $\dot{V} \leq -\alpha V + \beta$ for positive constants $\alpha, \beta$, establishing UUB. $\square$

#### 9.C.5 Metaheuristic Online Parameter Tuning

The control parameter vector $\boldsymbol{\theta}_c = [k_p, k_d, \omega_o, \sigma_o, M_0]^\top$ is optimized online using a computationally lightweight Differential Evolution (DE) variant with reduced population size ($N_p = 10$) operating on a 200 ms sliding window of tracking data:

$$\text{minimize}_{\boldsymbol{\theta}_c} \quad J(\boldsymbol{\theta}_c) = w_1 \|e_q\|_2^2 + w_2 \|\dot{e}_q\|_2^2 + w_3 \|\tau_c\|_1 + w_4 \mathbb{1}[|\tau_c| > \tau_{\text{thresh}}]$$

The $\|\tau_c\|_1$ term penalizes torque magnitude (metabolic cost proxy) and $\mathbb{1}[\cdot]$ penalizes saturation events (safety).

**Algorithm 3: Online σ-AADRC Parameter Tuning via Differential Evolution**

```
INPUT:  Tracking data buffer B of length T_buf = 200ms
        Current parameter vector theta_c, population P of size N_p=10
        DE parameters: F=0.8 (mutation), CR=0.9 (crossover)
OUTPUT: Updated theta_c*

// Initialize population around current parameters
IF first_call THEN
    P = {theta_c + delta_i : delta_i ~ Uniform(-epsilon, epsilon)^5}
END IF

FOR gen = 1 TO G_online DO
    FOR each individual x_i in P DO
        // Mutation: DE/rand/1
        Select r1, r2, r3 from P, all distinct, r1 != i
        mutant = P[r1] + F * (P[r2] - P[r3])
        mutant = clip(mutant, theta_min, theta_max)
        
        // Crossover
        trial = x_i
        FOR each dimension d DO
            IF rand() < CR OR d == rand_dim THEN
                trial[d] = mutant[d]
            END IF
        END FOR
        
        // Evaluate on buffer B (simulate forward with trial parameters)
        J_trial = evaluate_cost(trial, B)
        J_current = evaluate_cost(x_i, B)
        
        // Selection
        IF J_trial < J_current THEN
            P[i] = trial
        END IF
    END FOR
END FOR

theta_c* = argmin_{x in P} J(x, B)
RETURN theta_c*
```

---

### 9.D Work Plan and Activity Mapping

| Objective | Relevant Activity | Year 1 | Year 2 | Year 3 | Responsibility |
|-----------|-------------------|--------|--------|--------|----------------|
| O1 | Sensor data collection protocol design | ✓ | | | Both (Indian lead) |
| O1 | Fuzzy-CNN-GRU model development | ✓ | | | Indian team |
| O1 | Evolutionary NAS for architecture search | ✓ | ✓ | | Indian team |
| O1 | PSO hyperparameter optimization | ✓ | | | Indian team |
| O2 | Intra-subject variability modeling (GMM) | | ✓ | | Indian team |
| O2 | Online Bayesian gait state tracking | | ✓ | | Both |
| O3 | NvGRF estimation from plantar sensors | ✓ | | | French team |
| O3 | Optimal Transport domain adaptation | | ✓ | | Both (Indian lead) |
| O3 | Wasserstein barycenter trajectory synthesis | | ✓ | | Both |
| O3 | Concept drift detection and re-adaptation | | | ✓ | Both |
| O4 | ESO design and simulation validation | ✓ | | | French team |
| O4 | σ-AADRC control law derivation and proof | | ✓ | | Both |
| O4 | Metaheuristic online parameter tuning (DE) | | ✓ | | Indian team |
| O5 | Hardware integration on exoskeleton platform | | ✓ | ✓ | French team |
| O5 | Healthy subject validation experiments | | ✓ | | French team |
| O5 | Clinical validation (elderly, post-stroke) | | | ✓ | French team |
| O5 | Dataset curation and open release | | | ✓ | Both |
| — | Publications and dissemination | ✓ | ✓ | ✓ | Both |

---

## 10. System Integration

### 10.1 Closed-Loop Architecture

The three levels of the MLO framework are integrated into a hierarchical real-time control architecture with the following timing structure:

| Level | Update Rate | Latency Budget | Computing Hardware |
|-------|------------|----------------|--------------------|
| High-Level (Perception) | 50 Hz | ≤20 ms | Embedded GPU (Jetson Orin NX) |
| Mid-Level (Trajectory) | 100 Hz | ≤10 ms | ARM Cortex-A73 (4-core) |
| Low-Level (Control) | 1000 Hz | ≤1 ms | STM32H7 microcontroller |

**Inter-Level Communication:**

The context vector $\mathbf{c}(t) = [\hat{p}(t), \hat{\phi}(t), \hat{\sigma}^2_{\text{gait}}(t), \hat{e}(t)]$ containing the gait phase posterior $\hat{p}$, sub-phase timing $\hat{\phi}$, intra-subject variability estimate $\hat{\sigma}^2_{\text{gait}}$, and fatigue indicator $\hat{e}$ is published on a shared memory bus at 50 Hz and consumed by both the trajectory generator (mid-level) and the parameter adaptation law (low-level).

The reference trajectory $\boldsymbol{\theta}_{\text{ref}}(t) \in \mathbb{R}^n$ from the mid-level is published at 100 Hz and consumed by the low-level controller. Actuator feedback (joint angles $\mathbf{q}(t)$, torques $\boldsymbol{\tau}(t)$) is published at 1000 Hz and consumed by all three levels.

### 10.2 Multi-Level Optimization Synergy

A critical feature of the MLO architecture is that optimization decisions at each level are informed by the state and performance of adjacent levels:

1. **Perception → Trajectory:** The variability model from Level 1 modulates the OT weighting $\lambda_s$ in Level 2, causing the trajectory generator to conservatively widen the trajectory envelope when high intra-subject variability is detected (e.g., during fatigue).

2. **Trajectory → Control:** The trajectory generator provides not only $\boldsymbol{\theta}_{\text{ref}}(t)$ but also a feedforward torque estimate $\boldsymbol{\tau}_{\text{ff}}(t) = \mathbf{G}(\boldsymbol{\theta}_{\text{ref}}) + \mathbf{C}(\boldsymbol{\theta}_{\text{ref}}, \dot{\boldsymbol{\theta}}_{\text{ref}})\dot{\boldsymbol{\theta}}_{\text{ref}}$ to the σ-AADRC, reducing the effective disturbance that the ESO must estimate.

3. **Control → Perception:** High tracking error detected at Level 3 (indicating unexpected perturbation or user instability) triggers an elevated sampling rate at Level 1 and activates a "perturbation recovery" context mode in the trajectory generator.

4. **All Levels → Global Optimizer:** A supervisory meta-optimizer (running at 1 Hz) monitors overall system performance metrics and adjusts the relative weights $w_1, w_2, w_3, w_4$ in the DE cost function, the regularization parameter $\epsilon$ of the Sinkhorn algorithm, and the NAS architecture selection from the Pareto front, in response to evolving user state.

---

## 11. Expected Outcomes & Deliverables

### 11.1 Algorithmic Contributions

- **D1.1:** Open-source Fuzzy-CNN-GRU library with evolutionary NAS support for biomechanical time-series classification (Python/PyTorch, Apache 2.0 license).
- **D1.2:** Optimal Transport domain adaptation toolkit for gait trajectory personalization (Python, integrated with the POT library).
- **D1.3:** σ-AADRC controller firmware with embedded DE tuning (C++/ROS2 package).
- **D1.4:** Theoretical stability proof report for the σ-AADRC framework (submitted as technical report and journal article).

### 11.2 Datasets

- **D2.1:** Indo-French Gait Variability Dataset (IF-GVD): Wearable IMU and plantar pressure recordings from ≥60 subjects (30 healthy adults, 15 elderly, 15 post-stroke patients) across both India (Indian PI's institution) and France (French PI's institution). Multi-session, multi-condition (flat ground, slopes, stairs, outdoor). Annotated with gait events and sub-phases. Released on a public repository (Zenodo/PhysioNet).
- **D2.2:** Exoskeleton Control Benchmark Dataset: Joint kinematics, kinetics, and control signals from wearable exoskeleton experiments in healthy and impaired subjects.

### 11.3 Physical Demonstrators

- **D3.1:** Instrumented lower-limb exoskeleton prototype (hip-knee-ankle, bilateral) with embedded MLO stack.
- **D3.2:** Wearable sensing suit (IMU + plantar insoles) with real-time data streaming to edge computing unit.
- **D3.3:** User interface application (tablet-based) for clinician-configurable assistance profiles.

### 11.4 Performance Benchmarks

| Metric | Target Value | Comparison Baseline |
|--------|-------------|---------------------|
| Gait phase classification accuracy | ≥95% | CNN-only: ~88% |
| Cross-subject trajectory adaptation error | ≤10% biomechanical deviation | No adaptation: ~28% |
| Joint tracking RMS error | ≤2° at 1.0 m/s | Standard ADRC: ~4° |
| Fall detection sensitivity | ≥98% | FSM-based: ~85% |
| Parameter calibration time | ≤5 min (automated) | Manual: 2–4 hours |
| Metabolic cost reduction | ≥15% vs. unpowered orthosis | State-of-art: 10–23% |

### 11.5 Publications and Dissemination

- **D5.1:** Minimum 8 peer-reviewed journal publications (IEEE Transactions on Neural Systems & Rehabilitation Engineering, Journal of NeuroEngineering and Rehabilitation, Robotics and Autonomous Systems, IEEE Transactions on Evolutionary Computation).
- **D5.2:** Minimum 12 conference papers (ICRA, IROS, EMBC, BioRob, GECCO).
- **D5.3:** Two patent applications (one in India via CSIR-TKDL, one in France via INPI).
- **D5.4:** Joint Indo-French summer school on "Optimization and AI for Assistive Robotics" (Year 3).
- **D5.5:** Technology transfer white paper for industrial partners.

---

## 12. Work Plan & Timeline

### Work Packages

**WP1: Wearable Sensing and Data Collection** (Months 1–18, Both teams)

- WP1.1: Protocol design for multi-condition, multi-population gait recording
- WP1.2: Hardware deployment (IMU arrays, plantar insoles, reference systems)
- WP1.3: Data collection campaigns in India and France
- WP1.4: Data annotation, quality control, and release of IF-GVD (D2.1)

**WP2: High-Level Perception and Intention Recognition** (Months 1–24, Indian team lead)

- WP2.1: Feature engineering and preprocessing pipeline
- WP2.2: Fuzzy-CNN-GRU model development
- WP2.3: Evolutionary NAS implementation (NSGA-II + PSO)
- WP2.4: Intra-subject variability modeling (GMM + Bayesian update)
- WP2.5: Benchmark evaluation against state-of-the-art (SVM, LSTM, Transformer)

**WP3: Mid-Level Trajectory Generation** (Months 6–30, Both teams)

- WP3.1: NvGRF modeling from plantar and IMU sensors
- WP3.2: Optimal Transport library integration and Sinkhorn solver implementation
- WP3.3: Wasserstein barycenter algorithm for multi-subject template generation
- WP3.4: Concept drift monitoring and re-adaptation
- WP3.5: Validation on IF-GVD cross-subject generalization benchmarks

**WP4: Low-Level Adaptive Control** (Months 6–30, French team lead)

- WP4.1: Exoskeleton dynamic model identification
- WP4.2: ESO design and simulation validation (MATLAB/Simulink)
- WP4.3: σ-AADRC control law derivation and Lyapunov proof
- WP4.4: Metaheuristic DE online tuning implementation
- WP4.5: Hardware-in-the-loop validation on exoskeleton platform

**WP5: System Integration and Validation** (Months 18–36, Both teams)

- WP5.1: Software integration (ROS2 architecture, inter-level communication)
- WP5.2: Healthy subject validation (N=20, both sites)
- WP5.3: Clinical validation with elderly (N=15) and post-stroke (N=10) participants
- WP5.4: Comparative analysis vs. baselines
- WP5.5: Final demonstrator, dataset, and publication release

### Detailed Time Schedule

| TIME SCHEDULE | INDIA | FRANCE |
|---------------|-------|--------|
| **1st Year (Months 1–12)** | • Setup of IMU + plantar insole sensing platform<br>• Data collection campaigns (healthy adults, N=30)<br>• Fuzzy-CNN-GRU architecture development<br>• Evolutionary NAS (NSGA-II framework)<br>• PSO-based hyperparameter tuning<br>• Initial classification benchmark experiments<br>• 2–3 conference papers | • Exoskeleton platform setup and instrumentation<br>• ESO design and MATLAB/Simulink simulation<br>• NvGRF modeling from plantar sensors<br>• Dynamic model identification<br>• Exchange visit to India (2 weeks, French PhD student)<br>• 2–3 conference papers |
| **2nd Year (Months 13–24)** | • Intra-subject variability modeling (GMM)<br>• Online Bayesian gait state tracking<br>• Optimal Transport domain adaptation (Sinkhorn)<br>• Wasserstein barycenter algorithm implementation<br>• Cross-subject trajectory generalization benchmarks<br>• Exchange visit to France (2 weeks, Indian PhD student)<br>• 2–3 journal papers | • σ-AADRC control law finalization and Lyapunov proof<br>• DE online parameter tuning embedded firmware<br>• Hardware-in-the-loop validation<br>• Healthy subject experiments (N=20, France)<br>• Healthy subject experiments (N=20, India)<br>• 2–3 journal papers |
| **3rd Year (Months 25–36)** | • Concept drift monitoring and re-adaptation module<br>• Complete MLO stack software integration<br>• Release of IF-GVD dataset (Zenodo/PhysioNet)<br>• Patent application filing (India)<br>• Final 2–3 journal papers<br>• Joint summer school co-organization | • Clinical validation (elderly, N=15; post-stroke, N=10)<br>• Full system demonstrator integration<br>• Comparative analysis vs. baselines<br>• Patent application filing (France)<br>• Technology transfer white paper<br>• Final 2–3 journal papers |

### Milestones

| Milestone | Description | Month |
|-----------|-------------|-------|
| M1 | Sensing platform operational at both sites | 3 |
| M2 | First IF-GVD batch (healthy adults, N=30) available | 9 |
| M3 | Fuzzy-CNN-GRU model achieving ≥90% gait phase accuracy | 12 |
| M4 | Evolutionary NAS Pareto front established | 15 |
| M5 | NvGRF model validated (RMSE ≤ 0.1 BW) | 12 |
| M6 | OT domain adaptation reducing cross-subject error by ≥40% | 20 |
| M7 | σ-AADRC Lyapunov stability proof completed | 18 |
| M8 | Hardware-in-the-loop validation completed | 24 |
| M9 | Full MLO system integration operational | 27 |
| M10 | Healthy subject validation complete (N=40) | 30 |
| M11 | Clinical validation complete | 35 |
| M12 | Final deliverables (dataset, code, publications) released | 36 |

---

## 13. Evaluation & Validation

### 13.1 Experimental Setup

**Site 1 (India):** Laboratory motion capture system (VICON Nexus, 10-camera, 250 Hz), two force plates (Kistler 9260AA, 2000 Hz), a clinical 6-minute walk test track, and the wearable sensor platform. Healthy adult participants recruited through the institutional human subjects research board.

**Site 2 (France):** Laboratory-grade 3D gait analysis system (12-camera Qualisys), force-instrumented treadmill (GRAIL, Motekforce Link), a lower-limb exoskeleton platform (custom bilateral hip-knee-ankle device), and the wearable sensor platform. Clinical participants (elderly, post-stroke) recruited through the affiliated rehabilitation hospital.

**Ethical Compliance:** All experiments will receive ethics committee approval (IEC at Indian institution; CPP at French institution). Informed consent will be obtained from all participants. Data will be anonymized before sharing. Clinical trials will follow ICH-GCP guidelines.

### 13.2 Evaluation Metrics

**High-Level (Perception):**
- Gait phase classification accuracy (%), precision, recall, F1-score (per-phase and macro-average)
- Confusion matrix analysis
- Latency of phase detection relative to ground-truth gait events
- Out-of-distribution accuracy (novel subjects, novel conditions)

**Mid-Level (Trajectory):**
- RMS deviation of generated joint trajectories from reference motion capture data (°)
- Fréchet inception distance between generated and reference trajectory distributions
- NvGRF estimation RMSE (normalized to body weight)
- OT alignment quality: intra-class compactness in transported space

**Low-Level (Control):**
- RMS joint tracking error (°) at multiple walking speeds
- Peak tracking error during perturbation events (sudden obstacles, uneven ground)
- Chattering index (high-frequency torque oscillation power)
- Actuator saturation events per minute
- Time to convergence after parameter update

**System-Level:**
- Metabolic energy cost during assisted vs. unassisted walking (indirect calorimetry)
- User-perceived comfort (NASA-TLX questionnaire, 10-point Likert scale)
- Number of falls and near-falls per hour of operation
- Time required for automated calibration to new user

### 13.3 Real-World Testing Scenarios

The validation protocol encompasses five progressively challenging scenarios:

1. **S1 — Level Ground Walking:** Standard clinical 6-minute walk test and 10-meter walk test. Benchmark against lab-calibrated baselines.
2. **S2 — Terrain Transitions:** Laboratory floor, carpet, ramp (5°, 10°), step up/down (15 cm). Tests context-awareness of high-level and trajectory adaptation at mid-level.
3. **S3 — Speed Variations:** Comfortable, slow (70% comfortable), fast (130% comfortable). Tests adaptation of trajectory and control parameters.
4. **S4 — Perturbation Recovery:** Sudden lateral perturbations (1–3 kg pendulum impact), unexpected surface compliance changes. Tests low-level control robustness.
5. **S5 — Extended Daily Use (Ecological Validity):** 4-hour sessions with mobility-impaired participants performing activities of daily living in a structured apartment environment.

---

## 14. Innovation & Impact

### 14.1 Scientific Contributions

The project makes fundamental contributions to four scientific fields:

1. **Computational Intelligence:** Domain-specific evolutionary NAS for biomechanical time-series; theoretical convergence analysis of the Pareto-optimal NAS solution; new fuzzy kernel operators for quasi-periodic physiological signals.

2. **Optimal Transport Theory:** Extension of the Wasserstein barycenter framework to time-indexed trajectory spaces; novel regularization strategies for gait distribution alignment; efficient online Sinkhorn algorithms for streaming data.

3. **Control Theory:** Formal Lyapunov stability proofs for σ-AADRC under bounded disturbance rates; rigorous analysis of the σ-modification's role in preventing parameter drift in locomotion assistance; hybrid evolutionary-gradient control design.

4. **Rehabilitation Engineering:** First clinically validated demonstration of fully automated, multi-level optimization-based personalization for lower-limb exoskeleton assistance.

### 14.2 Societal Impact

- **Elderly Independence:** Enabling functionally meaningful daily living activities for the 300+ million elderly individuals with mobility limitations projected by 2030 in India and France combined. This addresses a direct and acute societal need.
- **Stroke Rehabilitation:** More than 13 million new strokes occur annually worldwide; ~50% of survivors have lasting mobility impairments. Adaptive robotic assistance can significantly increase the intensity and effectiveness of rehabilitation, accelerating recovery.
- **Caregiver Burden Reduction:** Automated, personalized robotic assistance reduces reliance on professional caregivers, addressing the global shortfall of rehabilitation professionals.
- **Inclusive Accessibility:** The MLO framework's automated calibration (≤5 min vs. current 2–4 hours) dramatically reduces the barrier to entry for wearable robotic technologies in resource-limited healthcare settings.

### 14.3 Industrial Relevance

- The open-source algorithm libraries (D1.1–D1.3) provide direct technology inputs to companies developing wearable robotic systems.
- The IF-GVD dataset (D2.1) serves as an industry-standard benchmark, accelerating product development cycles.
- Patent filings (D5.3) protect commercially valuable innovations while enabling licensing.
- Letters of intent will be sought from industrial partners (e.g., Wandercraft SAS, Parker Hannifin, Wipro GE Healthcare) for collaborative product development in Year 3.

---

## 15. Risk Analysis & Mitigation

| Risk Category | Risk | Probability | Severity | Mitigation Strategy |
|--------------|------|-------------|----------|---------------------|
| **Technical** | Fuzzy-CNN-GRU fails to achieve ≥95% accuracy | Medium | High | Parallel development of pure CNN-Transformer baseline; iterative NAS ensures best achievable architecture |
| **Technical** | OT domain adaptation computationally too slow for real-time use | Low | High | Use of Sinkhorn with fixed iterations and GPU acceleration; offline pre-computation of transport maps for typical user profiles |
| **Technical** | σ-AADRC stability conditions not achievable on target hardware | Low | High | Conservative parameter constraints; hardware-in-the-loop testing before clinical deployment |
| **Data** | Insufficient data diversity in IF-GVD | Medium | Medium | Multi-site collection, oversampling of edge cases, data augmentation (rotation, scaling, noise injection) |
| **Data** | High intra-subject variability confounding models | High | Medium | Explicit variability modeling is core methodology; dedicated ablation studies |
| **Data** | Recruitment challenges for clinical population | Medium | Medium | Multiple partner hospitals; simplified enrolment protocols; compensation for participants |
| **Deployment** | Regulatory approval delays | Low | High | Early engagement with CDSCO (India) and CE marking authority (EU); FDA pre-submission meeting if needed |
| **Collaboration** | Communication and coordination barriers (India-France) | Low | Low | Bi-weekly video meetings; annual joint workshops; shared cloud computing environment (AWS/Azure) |
| **Budget** | Equipment cost overruns | Low | Medium | Cost quotes obtained at proposal stage; contingency budget allocated (10%) |

---

## 16. Budget Justification

### Budget Summary (Indian Team — in INR Lakhs)

| Sr. No. | Items | 1st Year (₹ Lakhs) | 2nd Year (₹ Lakhs) | 3rd Year (₹ Lakhs) | Total (₹ Lakhs) |
|---------|-------|---------------------|---------------------|---------------------|-----------------|
| 1. | **Equipment** | 20.00 | 8.00 | 4.00 | 32.00 |
| 2. | **Salaries / Fellowships** | 9.60 | 9.60 | 9.60 | 28.80 |
| 3. | **Consumables** | 2.00 | 2.50 | 2.50 | 7.00 |
| 4. | **Travel (domestic conferences)** | 1.50 | 1.50 | 1.50 | 4.50 |
| 5. | **Exchange Visits (France ↔ India)** | 1.50 | 3.00 | 2.00 | 6.50 |
| 6. | **Contingency (10%)** | 3.46 | 2.46 | 1.96 | 7.88 |
| 7. | **Other Costs (computing cloud credits, licenses)** | 1.50 | 1.50 | 1.00 | 4.00 |
| 8. | **Overhead Expenses (20%)** | 7.91 | 5.71 | 4.51 | 18.13 |
| | **Total** | **47.47** | **34.27** | **27.07** | **108.81** |

### Budget Summary (French Team — in EUR k)

| Sr. No. | Items | 1st Year (k€) | 2nd Year (k€) | 3rd Year (k€) | Total (k€) |
|---------|-------|---------------|---------------|---------------|------------|
| 1. | **Equipment** | 35.0 | 15.0 | 5.0 | 55.0 |
| 2. | **Salaries (2 PhD students + 0.5 PostDoc)** | 80.0 | 80.0 | 80.0 | 240.0 |
| 3. | **Consumables** | 5.0 | 5.0 | 5.0 | 15.0 |
| 4. | **Travel (international conferences)** | 6.0 | 8.0 | 8.0 | 22.0 |
| 5. | **Exchange Visits (India ↔ France)** | 4.0 | 6.0 | 4.0 | 14.0 |
| 6. | **Contingency (8%)** | 10.4 | 9.1 | 8.2 | 27.7 |
| 7. | **Other Costs (clinical study fees, ethics)** | 5.0 | 5.0 | 3.0 | 13.0 |
| 8. | **Overhead / Indirect Costs (20%)** | 29.1 | 25.6 | 22.6 | 77.3 |
| | **Total** | **174.5** | **153.7** | **135.8** | **464.0** |

### Budget Justification Details

**Equipment (India):**
- MEMS IMU sensor kits (×12 Xsens DOT or equivalent): ₹8 L (Year 1)
- High-performance workstation with GPU (NVIDIA A6000): ₹7 L (Year 1)
- Flexible plantar pressure insoles (×6 pairs): ₹5 L (Year 1)
- Edge computing units (NVIDIA Jetson Orin NX, ×4): ₹4 L (Year 1–2) — for embedded deployment

**Salaries/Fellowships (India):**
- 2 PhD Research Fellows × ₹4.0 L p.a. = ₹8.0 L/year
- 1 Junior Research Fellow × ₹1.6 L p.a. = ₹1.6 L/year
- Total: ₹9.6 L/year

**Equipment (France):**
- IMU sensor suits and synchronization system: €10k
- Exoskeleton actuator modules (×6) and custom frame: €15k
- Force sensing insoles (×10 pairs, high-grade): €5k
- Embedded control computer (xPC Target or custom): €5k

**Salaries (France):**
- 2 PhD students (3-year doctoral contracts, CNRS scale): ~€30k × 2 = €60k/year
- 0.5 PostDoc (CNRS scale): ~€20k/year
- Total: ~€80k/year

**Exchange Visits:** A minimum of 4 exchange visits per year (2 in each direction) are planned to ensure close scientific collaboration, joint experimental campaigns, and knowledge transfer. Each international visit budget is €1.5k–€2k per person per trip (economy class + accommodation).

---

## 17. Conclusion

This proposal presents a scientifically rigorous and technically ambitious research programme that addresses a problem of enormous societal importance: the development of truly intelligent, adaptive wearable robotic systems for mobility-impaired and dependent individuals. By establishing **multi-level optimization** as a unifying architectural principle—spanning perception, trajectory generation, and control—the proposed work transcends the limitations of existing single-level or heuristically integrated approaches.

The three-level framework (Fuzzy-CNN-GRU with evolutionary NAS at the high level; Optimal Transport-based domain adaptation at the mid level; σ-AADRC with metaheuristic online tuning at the low level) is grounded in state-of-the-art mathematics, rigorously analyzed for stability and convergence, and designed for practical deployment on resource-constrained embedded hardware. The complementarity between the Indian team's expertise in evolutionary computation and the French team's expertise in wearable robotics and biomechanics ensures that each component of the framework is developed to the highest international standard.

Beyond the immediate deliverables—validated algorithms, open datasets, physical demonstrators, and clinical trial results—the MLO framework establishes a **general paradigm for adaptive human-centered systems in dynamic and uncertain environments**, with applicability extending to surgical robotics, industrial exoskeletons, prosthetics, and rehabilitation systems. The Indo-French collaboration that this project catalyzes will build lasting scientific bridges and human capital networks, amplifying the long-term impact of both national research ecosystems.

The combination of urgent societal need, scientific frontier positioning, complementary expertise, concrete deliverables, and clear translation pathway makes this proposal a compelling and fundable research investment.

---

## 18. References

1. Asbeck, A.T., De Rossi, S.M.M., Holt, K.G., & Walsh, C.J. (2015). A biologically inspired soft exosuit for walking assistance. *The International Journal of Robotics Research*, 34(6), 744–762.

2. Awad, L.N., Bae, J., O'Donnell, K., et al. (2017). A soft robotic exosuit improves walking in patients after stroke. *Science Translational Medicine*, 9(400), eaai9084.

3. Bai, S., Kolter, J.Z., & Koltun, V. (2018). An empirical evaluation of generic convolutional and recurrent networks for sequence modeling. *arXiv:1803.01271*.

4. Cai, Y., et al. (2023). Fuzzy-convolutional neural network for human activity recognition with wearable sensors. *Applied Soft Computing*, 131, 109784.

5. Chen, W.H., Yang, J., Guo, L., & Li, S. (2016). Disturbance-observer-based control and related methods—An overview. *IEEE Transactions on Industrial Electronics*, 63(2), 1083–1095.

6. Cuturi, M. (2013). Sinkhorn distances: Lightspeed computation of optimal transport distances. *Advances in Neural Information Processing Systems*, 26.

7. Dollar, A.M., & Herr, H. (2008). Lower extremity exoskeletons and active orthoses: Challenges and state-of-the-art. *IEEE Transactions on Robotics*, 24(1), 144–158.

8. Elsken, T., Metzen, J.H., & Hutter, F. (2019). Neural architecture search: A survey. *Journal of Machine Learning Research*, 20(55), 1–21.

9. Gao, Z. (2006). Active disturbance rejection control: A paradigm shift in feedback control system design. *Proceedings of the American Control Conference*, 2399–2405.

10. Han, J. (2009). From PID to active disturbance rejection control. *IEEE Transactions on Industrial Electronics*, 56(3), 900–906.

11. Giovacchini, F., et al. (2015). A light-weight active orthosis for hip movement assistance. *Robotics and Autonomous Systems*, 73, 123–134.

12. Ioannou, P.A., & Kokotovic, P.V. (1984). Instability analysis and improvement of robustness of adaptive control. *Automatica*, 20(5), 583–594.

13. Kennedy, J., & Eberhart, R. (1995). Particle swarm optimization. *Proceedings of ICNN'95*, 4, 1942–1948.

14. Lo, J., et al. (2019). Gaussian process models for gait variability in young and older adults. *Journal of Biomechanics*, 92, 35–42.

15. Lorenzo, P.R., Nalepa, J., Kawulok, M., Ramos, L.S., & Pastor, J.R. (2017). Particle swarm optimization for hyper-parameter selection in deep neural networks. *Proceedings of GECCO*, 481–488.

16. Luinge, H.J., & Veltink, P.H. (2005). Measuring orientation of human body segments using miniature gyroscopes and accelerometers. *Medical & Biological Engineering & Computing*, 43(2), 273–282.

17. Mannini, A., & Sabatini, A.M. (2010). Machine learning methods for classifying human physical activity from on-body accelerometers. *Sensors*, 10(2), 1154–1175.

18. Mouret, J.B., & Clune, J. (2015). Illuminating search spaces by mapping elites. *arXiv:1504.04909*.

19. Nguyen, Q.H., et al. (2022). CNN-transformer hybrid for real-time gait event detection from wearable IMUs. *IEEE Transactions on Neural Systems and Rehabilitation Engineering*, 30, 1231–1240.

20. Peng, X.B., Berseth, G., Yin, K., & Van De Panne, M. (2018). DeepLoco: Dynamic locomotion skills using hierarchical deep reinforcement learning. *ACM Transactions on Graphics*, 36(4), 1–13.

21. Phinyomark, A., Petri, G., Ibáñez-Marcelo, E., Osis, S.T., & Ferber, R. (2018). Analysis of big data in gait biomechanics: Current trends and future directions. *Journal of Medical and Biological Engineering*, 38(2), 244–260.

22. Rueterbories, J., Spaich, E.G., Larsen, B., & Andersen, O.K. (2010). Methods for gait event detection and analysis in ambulatory systems. *Medical Engineering & Physics*, 32(6), 545–552.

23. Santhiranayagam, B.K., Lai, D.T.H., Begg, R.K., & Palaniswami, M. (2015). Age-related differences in gait regularity and symmetry. *Journal of Electromyography and Kinesiology*, 25(6), 869–876.

24. Schwartz, I., et al. (2023). Exoskeleton-assisted walking in chronic stroke: A randomized controlled trial. *Neurorehabilitation and Neural Repair*, 37(2), 102–114.

25. Stanley, K.O., & Miikkulainen, R. (2002). Evolving neural networks through augmenting topologies. *Evolutionary Computation*, 10(2), 99–127.

26. Taborri, J., Scalona, E., Rossi, S., Palermo, E., Patane, F., & Cappa, P. (2016). Validation of inter-subject transfer calibration for foot gesture recognition systems based on sEMG. *International Journal of Advanced Robotic Systems*, 13(1).

27. Villani, C. (2009). *Optimal Transport: Old and New*. Springer.

28. Winter, D.A. (2009). *Biomechanics and Motor Control of Human Movement* (4th ed.). Wiley.

29. Zhang, X., et al. (2022). Attention-based transformer for joint kinematics prediction from wearable sensor data. *Sensors*, 22(8), 3011.

30. Zhao, Z., et al. (2015). Active disturbance rejection control for lower limb exoskeleton. *International Journal of Advanced Robotic Systems*, 12(4), 43.

---

*Prepared by:*
*Indian Principal Investigator: [Name], [Institution], India*
*French Principal Investigator: [Name], [Institution], France*
*Date: April 2026*

*Submitted to: CEFIPRA (Centre Franco-Indien pour la Promotion de la Recherche Avancée) / DST-CNRS Joint Research Programme 2026*
