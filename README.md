# Analog Neuron Circuit Model – Simplified Hodgkin-Huxley Architecture

## Overview

This project presents a simplified analog circuit model of a neuron, inspired by the Hodgkin-Huxley framework. The objective was to design a hardware-realistic analog system that demonstrates:

- Dendritic frequency filtering  
- Threshold-based spike generation (soma)  
- Axonal signal transmission with minimal distortion  

The design was developed and validated in Multisim, with signal analysis and verification performed in MATLAB.

This work forms part of my MSc Electronics dissertation at the University of Southampton.

---

## System Architecture

The system is structured into three functional stages:

### 1. Dendritic Filtering (RC Band-Pass Network)

- Each input signal passes through an RC band-pass filter.
- Filters tuned to preserve the alpha band (8–13 Hz), centered near 10 Hz.
- Purpose: Remove irrelevant frequency components while preserving biologically meaningful content.
- Multiple input types tested (EEG, HH spike, PQRST, multi-sine).

### 2. Soma – Spike Generation

- Implemented using LM311 comparator.
- Threshold-based activation mimics biological "all-or-none" principle.
- Schmitt trigger stage provides noise immunity and prevents false triggering.
- Output: Clean, sharp digital-like spike.

### 3. Axonal Transmission Line

- 9-stage RC ladder network simulates axonal propagation.
- Amplification stages inserted after every three sections.
- RC values tuned to minimize distortion and preserve spike shape.
- Final output maintains amplitude and timing fidelity.

---

## Input Signals Used

- EEG (real brain signal – PhysioNet)
- Hodgkin-Huxley spike waveform
- PQRST synthetic biomedical waveform
- Multi-frequency sinewave test input

All signals were independently validated through the dendritic filtering stage.

---

## Quantitative Validation

### Pulse Width
- Measured spike width: ~4.07 ms  
- Biological reference range: 2–5 ms  

### Spike Timing Jitter
- Average jitter: ~0.94 ms  
- Within expected biological range (1–2 ms)

### Gain Error
- Dendrite → Soma: ~7–8 dB (intentional reshaping)
- Soma → Axon: ~0 dB (minimal amplitude distortion)

### Phase Lag
- Dendrite filtering: 11–16 ms (expected RC delay)
- Soma → Axon: ~0.07 ms (minimal propagation delay)

### Signal Fidelity Metrics
- RMSE and normalized RMSE used to quantify distortion
- SNR measured across stages
- Minimal degradation observed across axonal transmission

These results demonstrate biologically realistic signal behavior in a simplified analog implementation.

---

## Tools Used

- **Multisim** – Analog circuit design and simulation
- **MATLAB** – FFT analysis, Bode plots, RMSE, SNR, jitter calculation
- Oscilloscope-based waveform validation in simulation environment

---

## Repository Contents

- `/report/` – Full MSc dissertation
- `/presentation/` – Project demonstration slides
- `/multisim/` – Multisim simulation file (.ms14)
- `/schematics/` – Full circuit schematic
- `/results/` – Key validation plots and signal outputs

---

## Hardware Implementation Considerations

While this project was validated in simulation, practical hardware implementation would require:

- Proper decoupling of comparator and op-amps
- Careful analog ground routing and separation
- Tolerance analysis of RC networks
- Noise mitigation strategies (shielding, filtering)
- Power supply stability and ripple suppression
- Layout optimization to reduce parasitic effects

---

## Limitations

- Ideal component models used (no thermal drift or parasitic modelling)
- Linear cascaded RC representation of axon
- Fixed threshold and time constants (no adaptive behavior)
- No modeling of synaptic plasticity

---

## Applications

Short-Term:
- Educational neuromorphic circuit demonstrations
- Analog signal processing testbed

Medium-Term:
- Low-power analog front-end for biosignal processing
- Hybrid analog-digital neuromorphic architectures

Long-Term:
- Spike encoding for EEG/ECG modelling
- Potential applications in neuroprosthetics and implantable systems

---

## Author

Kruthika Yogeesh Gowda  
MSc Electronics – University of Southampton  
