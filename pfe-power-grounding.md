# 🟧 PFE – Fault & SLM Diagnostics

คู่มือการตรวจ Fault, Earth Leakage และการอ่าน Supervisory สำหรับระบบสายใต้น้ำ

---

# 1) PFE Fault Diagnostics (การตรวจหาความผิดปกติของ PFE)

---

## 🔥 Ground Fault

### อาการ:
- กระแสไหลลง Sea Earth ผิดปกติ  
- ค่า IR (Insulation Resistance) ต่ำ  
- Voltage drift  
- Earth current ไม่เป็นศูนย์แม้ใน BEF  

### วิธีตรวจ:
- IR Test จาก PFE  
- แยกฝ่ายด้วย Sectionalizing Test  
- สังเกต Earth Current Trend  
- ตรวจแรงดันจากแต่ละฝั่ง SEF / BEF  

### ความหมาย:
Ground fault มักเกิดจาก  
- น้ำเข้าชั้น conductor  
- Joint เก่าเริ่มเสื่อม  
- ความเสียหายจาก anchor/dragging  

---

## 🔥 Current Imbalance

### อาการ:
ใน BEF โหมด → กระแสฝั่ง A ≠ กระแสฝั่ง B

### สาเหตุที่เป็นไปได้:
- BU เสียบางส่วน  
- Repeater aging / pump fail  
- Conductor resistance เปลี่ยน  
- มี leakage บาง segment  

### วิธีตรวจ:
- เปรียบเทียบ Current Telemetry  
- ตรวจ Voltage Drop แต่ละฝั่ง  
- ตรวจจาก SLM ว่ามี repeater ใดตอบสนองผิดปกติ  

---

# 2) SLM (Submarine Line Monitoring)

ระบบ Supervisory เฝ้าระวังสายใต้น้ำผ่าน Optical Supervisory Channel (OSC)

---

## 📡 สิ่งที่ SLM ตรวจได้:
- Repeater status  
- Pump current / pump power  
- BU switching state  
- Span loss trend  
- Earth leakage trend  
- Aging margin  
- Fault location (คร่าว ๆ)  
- Communication loss / degraded repeater  

---

## 📉 ค่าที่ต้องระวัง:
- Pump current สูงผิดปกติ  
- Pump power ตกลงต่อเนื่อง (pump aging)  
- Repeater ไม่ตอบสนอง (communication fail)  
- BU report error  
- Margin ลดลงเกิน 0.3–0.5 dB ต่อปี  

---

# 3) Fault Scenarios (สถานการณ์ fault ที่พบบ่อย)

---

### **A) Partial Ground Fault**
- IR ลดลงแต่ยังไม่ลัดเต็มที่  
- Earth current มีแต่ไม่ถึงกับ trip  
- ต้องเฝ้าจับตาเป็นเดือน ๆ  

### **B) Full Ground Fault**
- กระแสลงทะเลทันที  
- แรงดัน collapse  
- ระบบดับหรือ ALARM รุนแรง  
- ต้อง repair  

### **C) Conductor Break**
- ความต้านทานขึ้นสูงมาก  
- แรงดันต้องเพิ่มขึ้นถึงขีดจำกัด  
- Repeater ตายเป็นช่วง ๆ  

### **D) Pump Fail (EDFA)**
- OSNR ตก  
- Margin ลด  
- SLM แจ้ง pump current/power anomaly  

---

# 4) Flow Diagram – Fault Isolation

PFE Alarm Detected
↓
Check Earth Current
↓
Is IR low?
↓ ↓
YES NO
↓ ↓
Ground Fault Check Current Imbalance
↓ ↓
Sectionalize Compare A/B Current
↓ ↓
Identify Fault Segment Abnormal? → BU/Repeater suspected

---

# 5) SLM Supervisory Path Diagram (Text)

CLS A → SLTE A
→ Supervisory Laser
→ Wet Plant
→ Repeaters (telemetry hop-by-hop)
→ BU
→ Repeaters
→ SLTE B → CLS B


---

# 6) ค่าปกติที่ควรจำ (Typical Values)

| Parameter | Typical | หมายเหตุ |
|----------|---------|----------|
| PFE Current | 0.8–1.5 A | APG ใช้ ~1.0 A |
| Voltage | ±1.5–10 kV | แล้วแต่ระยะ total |
| Repeater Gain | 14–20 dB | ต่อ span |
| IR | > 50 MΩ | ต่ำกว่าเสี่ยง |
| OSNR Degradation | < 0.2 dB/ปี | aging |
| Pump Current Drift | 1–5% ต่อปี | ผิดกว่านี้คือเตือน |

---

# สรุป

ไฟล์นี้ครอบคลุม:
- Fault detection (IR, Earth Current, Voltage)  
- Repeater & BU diagnosis  
- SLM interpretation  
- Fault trend prediction  

ใช้ร่วมกับ Phase 2 และ Phase 3 จะเข้าใจระบบทั้งภาพรวมและภาพลึกของสายใต้น้ำได้สมบูรณ์ที่สุด

---
