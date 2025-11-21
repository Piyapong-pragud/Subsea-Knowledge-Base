# Glossary
รวมศัพท์ 60 คำสำคัญในโลก Submarine Cable

🔹 A – C

🔹Armored Cable

สายใต้น้ำที่มีเกราะเหล็ก เพื่อกันลากอวน/สมอเรือ
ใช้ตรงไหน: ใกล้ฝั่ง, fishing zone

🔹ASE Noise (Amplified Spontaneous Emission)

สัญญาณรบกวนจาก EDFA ใต้น้ำ ทำให้ OSNR ต่ำลง
ผลกระทบ: คุณภาพช่องตกเร็วเมื่อ span ยาวหลายร้อยกิโล

🔹BMH (Beach Manhole)

จุดที่สายใต้น้ำขึ้นฝั่ง
งานจริง: จุดทดสอบ OTDR ก่อนเข้า CLS

🔹BU (Branching Unit)

กล่องแยกสาขาใต้น้ำ แยก traffic ไปหลายประเทศ/หลายเกาะ
APG: มี BU หลายจุด เช่น เวียดนาม
CSN: ใช้แยกสายไปเกาะ

🔹Capacity Planning

การวางแผนเพิ่มช่อง เช่น 100G → 200G → 400G
ต้องคำนวณ OSNR, nonlinear limit

🔹 C – G

🔹CD (Chromatic Dispersion)

การกระจายตัวของแสง ทำให้สัญญาณเบลอ
APG/CSN: Coherent แก้ด้วย DSP ไม่ต้องใช้ DCM

🔹CLS (Cable Landing Station)

สถานีที่สายใต้น้ำมาสิ้นสุด
มี: PFE, SLTE, NOC, ระบบไฟฟ้า

🔹Coherent Transmission

วิธีส่งสัญญาณแบบใหม่ ใช้ QPSK/8QAM/16QAM
APG: 100G/200G coherent
ข้อดี: เดินทางไกล มี FEC ดีมาก

🔹EDFA (Repeater ใต้น้ำ)

แอมป์ขยายแสง ใช้ pump laser
Gain: 14–20 dB ต่อ span
อายุ: 25–30 ปี

🔹Equalization (Gain Flatness)

ทำให้กำลังทุกช่องเท่ากัน
อุปกรณ์: WSS / GFF

🔹 F – L

🔹FEC (Forward Error Correction)

ช่วยลดข้อผิดพลาดบนลิงก์
APG: SD-FEC
10G รุ่นเก่า: RS(255,239)

🔹Fiber Attenuation

ค่าลดทอนของไฟเบอร์
ทั่วไป: 0.17–0.18 dB/km

🔹Flex-Grid

ระบบปรับช่องแบบยืดหยุ่น 12.5 GHz
APG: ใช้กับ coherent

🔹GSNR

ตัววัดคุณภาพสัญญาณแบบนับ nonlinear ด้วย
QPSK: ต้อง >11 dB

🔹Landing Station Power System

ระบบไฟฟ้า CLS

🔹UPS

AC/DC plant

🔹PFE

🔹 M – P

🔹Marine Repair

การซ่อมสายในทะเล
ขั้นตอน: ROV → Cut → Recovery → Splice → Relay

🔹OTDR (Optical Time Domain Reflectometer)

เครื่องยิงแสงเพื่อดูความผิดปกติ/ระยะขัดข้อง
สายใต้น้ำต้องใช้: Long-range 40–50 dB

🔹OSNR (Optical Signal-to-Noise Ratio)

อัตราส่วนสัญญาณ/Noise
สำคัญที่สุดของ DWDM
QPSK: ~14 dB
10G NRZ: 18–23 dB

🔹PFE (Power Feeding Equipment)

จ่ายไฟ DC ให้ repeater
แรงดัน: ±1.5–10 kV
โหมด: Constant current
APG: ใช้ 1.0–1.5 A

🔹Power Budget

การคำนวณกำลังขยายและ loss ทั้งระบบ
สำคัญก่อนเพิ่ม channel

🔹 R – S

🔹Repeater

EDFA ใต้น้ำต่อกันเป็น chain
ระยะ: 60–80 km/ตัว

🔹ROADM

สวิตช์ออปติคสำหรับเพิ่ม/ดรอปช่องแบบ dynamic
APG: มี BU แบบ ROADM บางจุด

🔹RPL (Route Position List)

พิกัดเส้นทางสายใต้น้ำทั้งหมด

🔹SDM (Space Division Multiplexing)

เทคโนโลยีอนาคต Multi-core / Multi-fiber
เพิ่ม capacity แบบไม่เพิ่ม nonlinear

🔹SLM (Submarine Line Monitoring)

ระบบ monitor สถานะ repeater + BU
ผ่าน supervisory channel

🔹 S – W

🔹Span

ระยะระหว่าง repeater 2 ตัว
ค่ามาตรฐาน: 50–80 km

🔹Span Loss

loss ของ span
ปกติ: 9–14 dB

🔹Superchannel

หลาย carriers รวมเป็นช่องใหญ่
เช่น 400G, 600G

🔹WDM / DWDM

หลายช่องในไฟเบอร์เส้นเดียว
Spacing: 50/37.5 GHz

🔹WSS (Wavelength Selective Switch)

ตัวสวิตช์ปรับช่องใน ROADM
IL: 5–7 dB
