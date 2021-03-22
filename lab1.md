# การทดลองที่ 1 การเขียนโปรแกรมเพื่อรันบนไมโครคอนโทรเลอร์

## วัตถุประสงค์
1. เพื่อศึกษาองค์ประกอบ หน้าที่ ของ microcontroller
2. เพื่อการเขียนและรันโปรแกรมจาก microcontroller

## อุปกรณ์ที่ใช้
1. microcontroller ESP-01 ที่ประกอบไปด้วย CPU เสาอากาศสำหรับ WIFI
2. อุปกรณ์เชื่อมต่อ USB เข้าไปยัง serial

## แหล่งข้อมูลเพื่อการศึกษา
https://www.youtube.com/watch?v=NLIUsWLEpmg

## วิธีการทำการทดลอง (ทำเป็นขั้นตอนพร้อมภาพประกอบ)
1. เขียนโปรแกรมบน microcontroller โดยทำการเสียบ microcontroller เข้าทาง serial port ของ USB 

(จากซ้ายไปขวา microcontroller ESP-01, อุปกรณ์เชื่อมต่อ USB และ การเสียบเข้าทาง serial port ตามลำดับ)
![image](https://user-images.githubusercontent.com/80879966/112019858-6dcadf80-8b62-11eb-8370-cc9b002280f5.jpg)

2. ดูที่ตัวอย่างโปรแกรม ที่โฟลเดอร์ pattani
- พิมพ์ cd pattani เพื่อไปยังโฟลเดอร์
- แสดงโฟลเดอร์ ซึ่งมีโปรแกรมตัวอย่าง 9 โปรแกรม
  - ไปที่ตัวอย่างที่ 1
    - พิมพ์ cd 01_Serial Monitor
    - พิมพ์ vi src/main.cpp
 
![image](https://user-images.githubusercontent.com/80879966/112027096-72df5d00-8b69-11eb-9673-d481aa1b012b.jpg)


4. แสดงผลโปรแกรม โดยมี 15 บรรทัด 2 ส่วน
- set up 1 ครั้ง โดยการ set up serial port ที่ความเร็ว 115200
- ใน loop แสดงให้เห็นถึงการวนไปเรื่อยๆ ในบรรทัดต่างๆ ประกอบด้วย
  - cnt++ หมายถึง การนับเพิ่มเรื่อยๆ 
  - Serial.printf("PATTANI :%d\n",cnt) แทนคำสั่ง การแสดงผลตัวแปลcountออกมา
  - delay(1000) หมายถึง ช่วงเวลา 1000 ms หรือ 1 วินาที

![image](https://user-images.githubusercontent.com/80879966/112027096-72df5d00-8b69-11eb-9673-d481aa1b012b.jpg)

5.เข้าไปที่ configuration file ใน program
- พิมพ์ vi platformio.ini เพื่อแสดงข้อมูล

![image](https://user-images.githubusercontent.com/80879966/112023078-7b359900-8b65-11eb-89bb-9c9c617811b9.jpg)

  - platform แสดงถึง บริษัทผู้ผลิต
  - board แสดงถึง ชื่อบอร์ด
  - framwork แสดงถึง วิธีการเขียนโปรแกรม
  - upload_port แสดงถึง portที่ใช้ติดต่อ 
    - ในกรณีนี้เป็น windows จึงแสดงว่า COM3 (หรือCOM4)

6.อัพโหลดโปรแกรม 01_Serial Monitor เข้าไปยัง microcontroller โดยใช้คำสั่ง upload
- พิมพ์ pio run -t upload
- ในขณะที่ program กำลังรันข้อมูล เพื่อให้ microcontroller รับโปรแกรมใหม่เข้าไป
  - กดปุ่มดำ เพื่อทำให้เกิดการโหลด 
  - กดอีกปุ่ม เพื่อให้เกิดการset

![image](https://user-images.githubusercontent.com/80879966/112024929-41659200-8b67-11eb-8684-a86257d30a28.jpg)

  อัพโหลดเข้า microcontroller เสร็จสิ้น

![image](https://user-images.githubusercontent.com/80879966/112025795-1b8cbd00-8b68-11eb-89e9-aa61561284e4.jpg)
## การบันทึกผลการทดลอง (พร้อมตัวอย่าง)
## อภิปรายผลการทดลอง (พร้อมตัวอย่าง)
## คำถามหลังการทดลอง (พร้อมตัวอย่างคำตอบ)
