1. ทดลองกับ int (จำนวนเต็ม) และ sizeof()
```md
1.1 int บน ESP32 ใช้ 4 ไบต์ (32 บิต)

1.2 เมื่อกำหนดค่าให้เกินขอบเขตของ int (เช่น 2147483647 + 1) จะเกิด Overflow ทำให้ค่ากลับไปเริ่มที่ -2147483648
และเมื่อเกินขอบเขตล่าง (เช่น -2147483648 - 1) จะเกิด Underflow ทำให้ค่ากลับไปเป็น 2147483647

```

2. ทดลองกับ float และ double (ทศนิยม) และ sizeof()
```md
2.2 float ใช้: 4 ไบต์ (Single Precision), double ใช้: 8 ไบต์ (Double Precision)

2.3 float แสดงทศนิยมได้ประมาณ 6–8 ตำแหน่ง, double แสดงทศนิยมได้ถึง 15–16 ตำแหน่ง
สถานการณ์ที่ควรใช้ double: เมื่อต้องการ ความแม่นยำสูง เช่น ในงานวิทยาศาสตร์ คณิตศาสตร์ ฟิสิกส์ หรืองานที่เกี่ยวข้องกับการเงินหรือหน่วยที่เล็กมาก
```

3. ทดลองกับ char (อักขระ) และ sizeof()
```md
ขนาดของ char: 1 ไบต์ ตัวแปร char ใช้เก็บ รหัส ASCII ของอักขระ
```

4. ทดลองกับ bool (ตรรกะ) และ sizeof()
```md
ขนาดของ bool: 1 ไบต์ true/false บน Serial Monitor
```

5. ทดลองกับ long, long long, unsigned int, unsigned long, unsigned long long (จำนวนเต็มขนาดใหญ่/ไม่มีเครื่องหมาย) และ sizeof()
```md
5.1 long มีขอบเขตเท่ากับ int บน ESP32 คือ 32-bit signed
5.2 หากต้องการเก็บ จำนวนเต็มบวกที่ใหญ่ที่สุด ควรใช้ unsigned long long ซึ่งสามารถเก็บได้ถึง 18,446,744,073,709,551,615 (2⁶⁴ - 1)
```

6. ทดลองกับ byte (ข้อมูล 8 บิต) และ sizeof()
```md
ขนาดของ byte: 1 ไบต์ ผลลัพธ์ที่ได้คือ 0 เพราะค่า 256 เกินขอบเขตของ byte (8 บิต)
```

7. การคำนวณด้วยชนิดข้อมูลต่างกัน (Type Promotion)
```md
มื่อคำนวณ 10 / 3.0 และตัวหารเป็น float หรือ double → ผลลัพธ์เป็นทศนิยม
เพราะ C++ จะ แปลงชนิดอัตโนมัติ (type promotion) จาก int ไปเป็น float หรือ double ก่อนการหาร
แต่ถ้าแปลง 3.0 เป็น int (เช่น 10 / (int)3.0) จะเป็น 10 / 3 → ได้ผลลัพธ์เป็นจำนวนเต็ม (3) เพราะการหารของ int ตัดเศษทิ้ง
```

8. การแปลงชนิดข้อมูล (Explicit Type Casting)
```md
8.1 ควบคุมผลลัพธ์ทางคณิตศาสตร์
เช่น float avg = (float)count / total; เพื่อให้ได้ค่าทศนิยม

8.2 แปลงประเภทก่อนแสดงผลหรือใช้งานร่วมกับฟังก์ชัน
เช่น int temperature = (int)temperatureCelsius; เพื่อไม่แสดงทศนิยมในอุณหภูมิ

8.3 แปลงค่าจาก char เป็น int เพื่อดู ASCII
เช่น (int)'A' → 65

8.4 ลดขนาดข้อมูล / จัดการหน่วยความจำ
เช่น แปลงจาก int เป็น byte ถ้าแน่ใจว่าค่าอยู่ในช่วง 0-255
```
