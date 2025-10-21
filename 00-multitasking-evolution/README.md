```
graph TD
    A[Start] --> B(Initialize: LED = OFF, Button_State = RELEASED);
    B --> C{Loop Forever};
    C --> D(Read Button Pin);
    D --> E{Button == LOW (Pressed)?};
    E -- No (Released) --> F(Button_State = RELEASED);
    F --> C;
    E -- Yes (Pressed) --> G{Button_State == RELEASED?};
    G -- No (Already Held) --> C;
    G -- Yes (First Press) --> H(Wait 20ms <br> 'Debounce Delay');
    H --> I(Read Button Pin Again);
    I --> J{Still LOW (Pressed)?};
    J -- No (Noise) --> C;
    J -- Yes (Real Press) --> K(Toggle LED <br> 'if OFF -> ON, if ON -> OFF');
    K --> L(Button_State = PRESSED);
    L --> C;
```



# 00. วิวัฒนาการของ Multitasking ในไมโครคอนโทรลเลอร์

## ภาพรวมหัวข้อ

หัวข้อนี้จะพาคุณทำความเข้าใจเกี่ยวกับประวัติศาสตร์และวิวัฒนาการของการทำ Multitasking ในไมโครคอนโทรลเลอร์ ตั้งแต่ยุคเริ่มต้นจนถึงยุค RTOS

## 📋 เนื้อหาในหัวข้อ

### 📖 ทฤษฎี (1 ชั่วโมง)
- [theory.md](theory.md) - เนื้อหาบรรยายหลัก
  - ยุคเริ่มต้น: Single Task Systems
  - การพัฒนาสู่ Time-Sharing
  - เทคนิค Multitasking ต่างๆ
  - การเกิดขึ้นของ RTOS

### 💻 ปฏิบัติ (2 ชั่วโมง)
- [practice/](practice/) - โฟลเดอร์สำหรับการปฏิบัติ
  - Lab 1: Single Task vs Multitasking Demo
  - Lab 2: Time-Sharing Implementation
  - Lab 3: Cooperative vs Preemptive Comparison

## 🎯 วัตถุประสงค์การเรียนรู้

เมื่อจบหัวข้อนี้ นักเรียนจะสามารถ:
1. อธิบายวิวัฒนาการของ Multitasking ได้
2. เข้าใจปัญหาของระบบ Single Task
3. อธิบายเทคนิค Multitasking ต่างๆ พร้อมข้อดี-ข้อเสีย
4. เข้าใจเหตุผลที่ RTOS เกิดขึ้น
5. เลือกเทคนิคที่เหมาะสมสำหรับแต่ละงาน

## 📚 เอกสารอ้างอิง
- Real-Time Systems Design and Analysis (Phillip A. Laplante)
- FreeRTOS Reference Manual
- ESP-IDF Programming Guide

## ⏱️ เวลาที่ใช้
- **ทฤษฎี**: 1 ชั่วโมง
- **ปฏิบัติ**: 2 ชั่วโมง
- **รวม**: 3 ชั่วโมง
