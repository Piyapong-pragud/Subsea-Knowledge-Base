# PFE Power Theory – Submarine Cable Systems
> Deep dive into how DC power feeding works in subsea cable systems  
> Repeater Chain • Sea Earth • Station Earth • Voltage Drop • Fault Flow

---

## 🔵 1. Concept Overview – ทำไมต้องมี PFE?
Power Feeding Equipment (PFE) คือระบบที่ใช้ **จ่ายไฟแรงดันสูง (High Voltage DC)**  
เพื่อเลี้ยง **repeater ทั้งหมดในสายเคเบิลใต้น้ำ** ซึ่งเชื่อมต่อแบบอนุกรม (series chain)

- Repeater แต่ละตัวต้องการ ~50–70 V
- จำนวน 100–300 ตัว = ต้องการหลายพันโวลต์
- ระบบยาว 1,000–10,000 km = ต้องคุมไฟแม่นยำ

PFE ทำงานแบบ **Constant Current Feeding** เพื่อให้ repeater ทุกตัวได้รับกระแสเท่ากัน

---

## 🔵 2. วงจรไฟฟ้าที่แท้จริงของ Submarine Cable

โครงสร้างไฟฟ้าคือระบบแบบ “เส้นเดียว” (single-wire system)

PFE (+)  →  Conductor  →  Repeater Chain  →  Sea Water  →  Sea Earth  →  PFE (–)

- **Conductor** = ส่งไฟ
- **Sea Water** = Return path
- **Sea Earth** = จุดรับกระแสกลับบนฝั่ง

ระบบจะสมบูรณ์ก็ต่อเมื่อกระแสไหลกลับถึง PFE (–)

---

## 🔵 3. Conductor – เส้นทางส่งไฟเลี้ยง Repeater

ทองแดงในสายใต้น้ำ (2.5–5 mm²):

- ความต้านทาน ~1.5–2.5 Ω/km
- หน้าที่ส่งไฟไปยัง repeater ทุกตัว
- ทนแรงดันสูง 1.5–12 kV

---

## 🔵 4. Sea Water – เส้นทางคืนกลับของไฟ (Return Path)

น้ำทะเลมีการนำไฟฟ้าสูงมาก (~4 S/m)

ปลายสายใต้น้ำมีทองแดงที่ “สัมผัสน้ำ” เมื่อไปถึงจุดสุดสาย  
กระแสจะกระโดดลงทะเลเป็นวงจรกลับ

---

## 🔵 5. Sea Earth Electrode (เฉพาะด้าน PFE –)

ตำแหน่ง:
- อยู่ในทะเลตื้น 3–15 m
- ห่าง CLS 100–500 m
- เป็นแผ่น Titanium หรือ Graphite

หน้าที่:
- รับกระแสกลับจากน้ำทะเล
- ส่งกลับเข้า PFE (–)

Sea Earth → PFE (–)

⚠ **ฝั่ง PFE (+) ไม่ต้องมี Sea Earth และห้ามมีโดยเด็ดขาด**

---

## 🔵 6. Station Earth vs Sea Earth

| ระบบ | หน้าที่ | เชื่อมกับ |
|------|---------|------------|
| **Sea Earth** | คืนกระแสไฟกลับสู่ PFE | PFE (–) |
| **Station Earth** | กราวด์อุปกรณ์ในอาคาร CLS | UPS, AC plant, Router/SLTE |

**สองระบบนี้แยกกัน ไม่เกี่ยวข้องกัน**

---

## 🔵 7. Voltage Calculation – คำนวณแรงดันที่ต้องใช้

สูตรหลัก:

V_total = (I × R_cable) + ΣV_repeater + Margin

ตัวอย่างระบบ APG:
- กระแส: 1.0 A
- R_cable ≈ 1.5 Ω/km × 5,000 km = 7,500 Ω
- Repeater ~ 250 ตัว × 60 V = 15,000 V
- Margin 1,500–2,000 V
- รวมประมาณ = **24–28 kV**

PFE ทำงานได้ถึง ~±10 kV ต่อด้าน ใช้ BEF เพื่อแบ่งโหลด

---

## 🔵 8. Repeater Power Consumption

ภายใน repeater มี:

- Pump Laser (1480 nm / 980 nm)
- EDFA gain unit
- Supervisory sensor
- Control ASIC

กินไฟ ~50–70 V ต่อ repeater  
ต่อกันแบบอนุกรม → ใช้ไฟรวมหลายพันโวลต์

---

## 🔵 9. Fault Flow – Ground Fault คืออะไร?

เกิดเมื่อทองแดงมีการสัมผัสน้ำก่อนถึงปลายสาย

PFE (+) → leak → seawater → Sea Earth → PFE (–)

อาการ:

- Earth Current ↑
- Voltage drop ↓
- IR ต่ำกว่า 5 MΩ
- SLM แจ้ง Repeater Differential Fault

---

## 🔵 10. Feeding Modes (SEF / BEF / Earth-Free)

### 🟦 SEF – Single-End Feed  
จ่ายจากฝั่งเดียว → ใช้ sea water คืนกลับ  
เหมาะกับระบบ CSN / Domestic

### 🟧 BEF – Both-End Feed  
จ่ายสองฝั่งเข้าหากัน → ลดแรงดัน  
ใช้กับระบบยาวอย่าง APG / AAG / SMW

### 🔴 Earth-Free  
ให้วงจร “ลอยจากดิน”  
ใช้ทดสอบ fault หรือ IR test

---

## 🔵 11. สรุปโครงสร้างวงจรแบบมองเห็นภาพ

PFE (+HV) │ │  ส่งไฟ ▼ (Conductor) │ ▼ [Repeater 1] – กิน 60V [Repeater 2] – กิน 60V : [Repeater N] │ ▼ (Near cable end → ลงทะเล) │ ▼ Sea Water (Return Path) │ ▼ Sea Earth Electrode │ ▼ PFE (–HV)

---

## 🔵 12. Key Concepts (จำให้ขึ้นใจ)

- PFE จ่าย **Constant Current**
- Conductor ส่งไฟ → Sea Return คืนไฟ
- Sea Earth อยู่เฉพาะ PFE (–)
- ฝั่ง PFE (+) ต้องลอย (floating)
- Repeater chain ต่ออนุกรมทั้งหมด
- ระบบยิ่งยาว = ต้องการแรงดันมากขึ้น
- Ground Fault = กระแสไหลลงทะเลก่อนเวลา

---

## 📘 สรุปสั้นที่สุด

**PFE คือหัวใจทั้งหมดของระบบ Subsea**  
ทำให้ repeater ทำงาน  
ควบคุมแรงดัน  
วัด fault  
รักษาความเสถียรของระบบใต้น้ำทั้งเส้น

ถ้าเข้าใจไฟฟ้าใต้ทะเล = เข้าใจครึ่งนึงของ Subsea แล้ว

---
File: pfe-power-theory.md
Category: PFE & Grounding Systems
Link: /pfe-power-theory.md

---
