# 🚀 Predictive Maintenance: Vibration Analysis & Failure Prediction

## 🌟 ภาพรวมของโปรเจกต์ (Project Overview)
โปรเจกต์นี้เป็นการพัฒนาระบบ **Predictive Maintenance (การบำรุงรักษาเชิงคาดการณ์)** สำหรับวิเคราะห์สุขภาพของเครื่องจักรในโรงงานอุตสาหกรรม โดยใช้ข้อมูลความสั่นสะเทือน (Vibration Data) จากเซนเซอร์ ระบบจะทำการประมวลผลข้อมูลดิบ ประเมินสถานะเครื่องจักรตามมาตรฐานสากล **ISO 10816-3** และใช้ **Machine Learning (Linear Regression)** เพื่อพยากรณ์ล่วงหน้าว่าเครื่องจักรมีแนวโน้มจะเสียหาย (Failure) ในวันใด เพื่อให้วิศวกรสามารถวางแผนซ่อมบำรุงได้อย่างทันท่วงที

## ✨ ฟีเจอร์หลัก (Key Features)
โปรเจกต์นี้แบ่งการทำงานออกเป็น 5 ขั้นตอนหลัก:
1. **Data Parsing & Cleaning:** สกัดข้อมูลความสั่นสะเทือนดิบจากไฟล์ `.txt` พร้อมทำความสะอาดและจัดการกับ Metadata (ชื่อเครื่องจักร, วันที่)
2. **Signal Processing (RMS Calculation):** คำนวณหาค่าความเร็วรากกำลังสองเฉลี่ย (**Velocity RMS**) จากข้อมูลสัญญาณนับพันแถว เพื่อให้ได้ตัวเลข 1 ตัวที่เป็นตัวแทนความรุนแรงของการสั่นสะเทือนในแต่ละรอบการวัด
3. **Data Aggregation:** สร้างลูปอัตโนมัติเพื่อกวาดอ่านและสรุปผลข้อมูลจากทุกไฟล์ในโฟลเดอร์ให้ออกมาเป็นตารางสรุป (Summary DataFrame)
4. **Health Assessment & Visualization:** สร้างกราฟแสดงแนวโน้ม (Trend Analysis) และระบายสีแบ่งโซนความรุนแรงตามมาตรฐาน **ISO 10816-3** (ใช้เกณฑ์ Conservative: Machinery Groups 2 and 4, Rigid Foundation)
5. **Failure Prediction:** ใช้ **Linear Regression** วิเคราะห์ความชัน (Slope) ของแนวโน้มข้อมูล หากเครื่องจักรมีแนวโน้มแย่ลง ระบบจะลากเส้นพยากรณ์ไปในอนาคตเพื่อหา "วันที่คาดว่าจะพัง (Predicted Failure Date)" พร้อมระบบแจ้งเตือนฉุกเฉินหากค่าปัจจุบันทะลุเกณฑ์อันตรายไปแล้ว

## 🛠️ เครื่องมือและไลบรารีที่ใช้ (Tech Stack)
- **Python 3.x**
- **Pandas:** สำหรับจัดการและแปลงข้อมูล (Data Manipulation)
- **NumPy:** สำหรับการคำนวณเชิงตัวเลข
- **Matplotlib & Seaborn:** สำหรับสร้างกราฟและ Data Visualization
- **Scikit-learn:** สำหรับสร้างโมเดล Machine Learning (Linear Regression)

## 📊 เกณฑ์การประเมินตามมาตรฐาน ISO 10816-3
โปรเจกต์นี้ใช้เกณฑ์ที่เข้มงวดที่สุดเพื่อความปลอดภัยสูงสุด (Worst-case Scenario) โดยกำหนดเกณฑ์แจ้งเตือน (Velocity RMS) ดังนี้:
* 🟢 **Zone A (Good):** 0.0 - 1.4 mm/s
* 🟡 **Zone B (Satisfactory):** 1.4 - 2.8 mm/s
* 🟠 **Zone C (Warning):** 2.8 - 4.5 mm/s
* 🔴 **Zone D (Danger):** > 4.5 mm/s (จุดวิกฤตที่ต้องหยุดเครื่องจักร)

## 📂 โครงสร้างโฟลเดอร์ (Project Structure)
```text
📦 Predictive-Maintenance-Vibration
 ┣ 📂 raw-data/              # โฟลเดอร์เก็บไฟล์ข้อมูลดิบ (.txt) ของเครื่องจักรในแต่ละเดือน
 ┣ 📜 main.ipynb                # โค้ดหลักของโปรแกรม (รวม Step 1 ถึง Step 5)
 ┣ 📜 README.md              # คำอธิบายโปรเจกต์
 ┗ 📜 requirements.txt       # รายชื่อไลบรารีที่ต้องติดตั้ง
```
## 👨‍💻 พัฒนาโดย: ณฐวัฒน์ สุวรรณรินทร์ (65160048)
> ไฟล์ main.ipynb อาจจะไม่สามารถเปิดได้จากหน้า web GitHub
> กรุณา clone ลงเครื่องของท่านครับ
