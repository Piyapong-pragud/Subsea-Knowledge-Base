# 🔢 Optical & Power Budget Calculator (Subsea Edition)
เครื่องมือคำนวณ Link Budget / OSNR / Voltage / Current สำหรับระบบใต้น้ำ  
รองรับระบบ APG / AAE-1 / CSN และสาย domestic

---

# 1) OSNR Calculator (ต่อช่อง)

สูตรพื้นฐานสำหรับระบบ Coherent:

OSNR(dB) = Pch(dBm) – NF(dB) – 10·log10(Nspans)


### ตัวแปร:
- **Pch** = Launch power per channel  
- **NF** = Noise figure ของ repeater (5.5–6.5 dB)  
- **Nspans** = จำนวน span (repeater count)

### ตัวอย่าง APG:
- Pch = 0 dBm  
- NF = 6.0 dB  
- Nspans = 92  

OSNR ≈ 0 – 6 – 19.6 = -25.6 dB (ก่อน FEC normalization)


หลัง normalize (0.1 nm BW):

≈ **15–16 dB** → เพียงพอสำหรับ QPSK

---

# 2) Launch Power Recommendation

| ระบบ | Launch Power ที่แนะนำ |
|------|------------------------|
| 10G NRZ | -2 ถึง +2 dBm |
| 100G QPSK | -1 ถึง +1 dBm |
| 200G 8QAM | -3 ถึง -1 dBm |
| 400G (new) | -5 ถึง -3 dBm |

Subsea มักใช้ **0 dBm ± 0.5** เพื่อควบคุม nonlinear

---

# 3) Span Loss Calculator

Span Loss = Distance(km) × Fiber Attenuation(dB/km) + Splice Loss


ค่าอ้างอิง:
- Attenuation = 0.17–0.18 dB/km  
- Splice = 0.05–0.1 dB / splice  
- Wet splice ≈ 0.3 dB  

### ตัวอย่าง:
Span = 72 km  
Fib. att = 0.17 dB/km

Loss = 72 × 0.17 = 12.24 dB


Repeater gain ต้องสูงกว่า 12.5–13 dB

---

# 4) Total Link Attenuation (Chain)

Total Loss = Σ(Span Loss) + Σ(Splice Loss) + BU Loss


BU Loss:
- 0.3–0.7 dB/pass  
- Undersea ROADM (rare) = 3–6 dB

---

# 5) Repeater Gain Requirement

Gain Required = Span Loss + Margin
Margin = 1–2 dB


---

# 6) Power Budget Calculator (รวมสายใต้น้ำ)

OSNR_total = OSNR_span – 10·log10(Nspans)


### ค่า Recommended OSNR:
| Modulation | OSNR (dB) |
|------------|-----------|
| QPSK | ≥14 dB |
| 8QAM | ≥17 dB |
| 16QAM | ≥21 dB |

---

# 7) PFE Voltage Calculator

แรงดันรวมที่ต้องใช้บน conductor:

V_total = (I × R_total) + V_repeaters + Margin


### ค่าอ้างอิง:
- I = 0.8–1.5 A  
- R (copper) = 1.4–1.7 Ω/km  
- V per repeater = 40–70 V  

### ตัวอย่าง APG:
Distance = 3000 km  
R = 1.5 Ω/km → R_total = 4500 Ω  
I = 1.0 A  
Repeaters = 90  
V_rep = 50 V

Voltage = (1 × 4500) + (90 × 50) = 9000 V
Margin 500–1500 V


รวม **≈ 10–11 kV**  
ตรงกับค่าจริงใน APG

---

# 8) Sea Earth Return Current (SEF Mode)

I_earth = I_feed (ในระบบ SEF)


ดูได้จาก PFE → Earth Current Meter  
ค่าปกติ:

- 0.95–1.05 A (stable link)  
- ถ้าต่างจาก feed current → มี leakage or ground fault

---

# 9) Nonlinear Threshold Calculator

สูตรประเมิน:

Penalty ≈ 10·log10(1 + (Pch / P_th)^2)


ค่า P_th เฉลี่ย:
- QPSK → +1.0 dBm  
- 8QAM → -1.0 dBm  
- 16QAM → -3.0 dBm  

---

# 10) Recommended Monitoring Table (สำหรับ CLS)

| Parameter | ช่วงค่าปกติ | อันตราย |
|-----------|--------------|----------|
| Launch Power | 0 ± 0.5 dBm | > ±1 dB |
| Span Loss Drift | < 0.03 dB/ปี | > 0.1 dB/ปี |
| Pump Current | ±5% | > ±10% |
| OSNR | ≥14 dB | < 12 dB |
| Earth Current (SEF) | = Feed | แตกต่าง >0.05 A |

---

# 11) สรุป

ไฟล์นี้รวมชุดสูตร + ค่าอ้างอิง เพื่อคำนวณคุณภาพระบบใต้น้ำ  
เหมาะสำหรับ:

- CLS Engineer  
- Optical planner  
- ผู้วางแผนเพิ่มช่อง (capacity upgrade)  
- ผู้ตรวจสุขภาพลิงก์รายปี  

ใช้ร่วมกับไฟล์อื่นในหมวด  
**Optical & Transmission**  
เพื่อทำให้วิเคราะห์ระบบได้ครบทั้ง chain

---
