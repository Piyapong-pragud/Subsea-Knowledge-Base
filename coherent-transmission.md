# Coherent Optical Transmission – End-to-End Architecture
Coherent transmission is the foundation of modern submarine and long-haul optical  
communication systems. It enables high capacity, long reach, advanced modulation  
formats, and sophisticated digital signal processing (DSP).

This document provides a full end-to-end view of coherent transmission,  
from laser generation → IQ modulation → fiber propagation → EDFA chain →  
coherent receiver → DSP recovery.

---

## 📘 1. What Is Coherent Transmission?
Coherent optical transmission uses:

- A narrow-linewidth laser
- IQ (In-phase / Quadrature) modulation
- Dual polarization
- A coherent receiver with a local oscillator (LO)
- Digital signal processing (DSP)

Unlike legacy IM-DD (10G NRZ), coherent systems detect **phase + amplitude**,  
not only power level, enabling:

- Advanced modulation formats (QPSK / 16QAM / 64QAM)
- Compensation for dispersion and PMD
- Error correction using powerful FEC
- Long-haul and submarine performance

---

## 📘 2. Coherent Transmitter Architecture

### Main components:
- Narrow linewidth tunable laser (≤ 100 kHz)
- IQ Modulator (LiNbO₃ or silicon photonics)
- Driver amplifiers
- Polarization multiplexing
- Pulse shaping filters (Nyquist)
- FEC encoder

### Transmitter Block Diagram

Laser (narrow linewidth)
           │
           ▼
    IQ Modulator (I/Q)
   ┌─────────┬─────────┐
   │Amplitude│  Phase  │
   │ Control │ Control │
   └─────────┴─────────┘
           │
    Polarization Split
           │
  DP-QPSK / DP-16QAM Signal
           │
     Pulse Shaping Filter
           │
          Fiber

---

## 📘 3. IQ Modulation (Core of Coherent Tx)
The IQ modulator controls:

- **I-branch** → amplitude
- **Q-branch** → phase

By combining both, the transmitter can generate any point in a constellation:

- QPSK → 4 symbols
- 8QAM → 8 symbols
- 16QAM → 16 symbols
- 64QAM → 64 symbols

This directly determines the number of bits per symbol and the OSNR required.

---

## 📘 4. Polarization Multiplexing (DP-QPSK / DP-16QAM)
To double spectral efficiency, coherent systems transmit:

- One data stream in **X-polarization**
- Another in **Y-polarization**

Combined capacity:

| Format | Bits per Symbol |
|--------|-----------------|
| QPSK | 2 |
| **DP-QPSK** | **4** |
| 16QAM | 4 |
| **DP-16QAM** | **8** |

This is a critical feature for high-capacity subsea systems.

---

## 📘 5. Propagation in Fiber (Submarine vs Terrestrial)
Signals pass through:

- Fiber attenuation (0.17–0.19 dB/km)
- Chromatic dispersion (17 ps/nm/km)
- PMD (0.1–1 ps/√km)
- Nonlinear effects (SPM, XPM, FWM)
- EDFA noise accumulation (ASE)

Submarine differences:
- Long spans (60–100 km)
- Hundreds of repeaters
- Tight OSNR budget
- Better CD uniformity
- No transient events like ROADM bypass

---

## 📘 6. Repeated Amplification (EDFA Chain)
Submarine repeaters use **EDFA amplifiers**:

- Pump wavelength: 980 or 1480 nm
- Gain per stage: 14–20 dB
- Noise figure ~4.5–6 dB
- Hundreds of amplifiers in series
- Power fed by submarine conductor (1–1.5 A DC)

ASE accumulates through all repeaters →  
OSNR gradually drops along the cable.

---

## 📘 7. Coherent Receiver Architecture
The coherent receiver uses:

- Optical hybrid (mixing incoming light with LO laser)
- Balanced photodiodes (BPD)
- Sampling ADCs
- High-speed DSP

### Receiver Block Diagram

Incoming Signal ───┐
                   │
                Optical Hybrid
                   │

LO Laser ───────────┘ │ Balanced Photodiodes │ ADCs │ DSP │ Bits Out

The LO laser enables phase recovery by mixing with the received signal  
(in contrast to direct detection systems).

---

## 📘 8. DSP Processing (The Brain of the System)
DSP compensates all major transmission impairments:

### Electrical domain:
- IQ imbalance correction
- Adaptive equalization

### Optical domain:
- Chromatic dispersion compensation
- PMD compensation
- Phase noise recovery
- Polarization tracking
- Carrier frequency offset correction

### System domain:
- Nonlinear mitigation (partial)
- FEC decoding
- Constellation shaping

DSP is why coherent signals can:

- Cross oceans  
- Withstand repeater gain tilt  
- Survive nonlinear distortions  
- Maintain stable Q-factor

---

## 📘 9. Baud Rate Considerations
Symbol rate affects bandwidth, nonlinear tolerance, and reach.

Typical submarine values:
- 100G DP-QPSK → ~32 Gbaud
- 200G DP-QPSK → dual carrier or ~32–40 Gbaud
- 400G → 60–70 Gbaud (with advanced shaping)

Higher baud rate →  
+ higher capacity  
– lower tolerance to impairments  

---

## 📘 10. OSNR Requirements (Critical in Submarine Systems)

| Format | OSNR Required (0.1 nm) |
|--------|-------------------------|
| BPSK | 7–9 dB |
| **QPSK** | **11–14 dB** |
| 8QAM | 15–17 dB |
| 16QAM | 18–20 dB |
| 64QAM | 22–24 dB |

Submarine repeaters support QPSK reliably.  
Higher-order QAM is limited to short-haul/terrestrial systems.

---

## 📘 11. End-to-End Transmission Flow Summary

Laser → IQ Modulator → DP-QPSK → Pulse Shaping → Fiber → EDFA Repeaters → Accumulated ASE → Coherent Receiver → LO Laser → Optical Hybrid → BPD → ADC → DSP → Bits / Frames / Traffic

This completes one full “coherent chain” across the ocean.

---

## 📘 12. Why Coherent Transmission Is Ideal for Submarine Systems
- High tolerance to noise  
- Long-haul capability  
- DSP corrects dispersion and PMD  
- Excellent nonlinear tolerance  
- Supports flexible spectral shaping  
- Works on legacy wet plants (G.977)  
- Enables upgrades (10G → 100G → 200G) without new wet plant

Submarine coherent transmission =  
**the most robust long-distance communication method ever built.**

---

File: coherent-transmission.md
Category: Optical Transmission Systems
