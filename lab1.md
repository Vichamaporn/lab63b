# การทดลองที่ 1 การเขียนโปรแกรมเพื่อรันบนไมโครคอนโทรเลอร์

## วัตถุประสงค์
1. เพื่อศึกษาองค์ประกอบ หน้าที่ ของ microcontroller
2. เพื่อการเขียนและรันโปรแกรมจาก microcontroller

## อุปกรณ์ที่ใช้
1. microcontroller ESP-01 ที่ประกอบไปด้วย CPU เสาอากาศสำหรับ WIFI
2. อุปกรณ์เชื่อมต่อ USB เข้าไปยัง serial

## แหล่งข้อมูลเพื่อการศึกษา
https://www.youtube.com/watch?v=NLIUsWLEpmg

## วิธีการทำการทดลอง
1. เขียนโปรแกรมบน microcontroller โดยทำการเสียบ microcontroller เข้าทาง serial port ของ USB 

(จากซ้ายไปขวา microcontroller ESP-01, อุปกรณ์เชื่อมต่อ USB และ การเสียบเข้าทาง serial port ตามลำดับ)
![image](https://user-images.githubusercontent.com/80879966/112019858-6dcadf80-8b62-11eb-8370-cc9b002280f5.jpg)

2. ดูที่ตัวอย่างโปรแกรม ที่โฟลเดอร์ pattani
- พิมพ์ cd pattani เพื่อไปยังโฟลเดอร์
- แสดงโฟลเดอร์ ซึ่งมีโปรแกรมตัวอย่าง 9 โปรแกรม
  - ไปที่ตัวอย่างที่ 1
    - พิมพ์ cd 01_Serial Monitor
    - พิมพ์ vi src/main.cpp

![image](https://user-images.githubusercontent.com/80879966/112027725-0a44b000-8b6a-11eb-89d6-69a81fd87226.jpg)

3. แสดงผลโปรแกรม โดยมี 15 บรรทัด 2 ส่วน
- set up 1 ครั้ง โดยการ set up serial port ที่ความเร็ว 115200
- ใน loop แสดงให้เห็นถึงการวนไปเรื่อยๆ ในบรรทัดต่างๆ ประกอบด้วย
  - cnt++ หมายถึง การนับเพิ่มเรื่อยๆ 
  - Serial.printf("PATTANI :%d\n",cnt) แทนคำสั่ง การแสดงผลตัวแปลcountออกมา
  - delay(1000) หมายถึง ช่วงเวลา 1000 ms หรือ 1 วินาที
 
```javascript
#include <Arduino.h>

int cnt = 0;

void setup()
{
	Serial.begin(115200);
}

void loop()
{
	cnt++;
	Serial.printf("PATTANI :%d\n",cnt);
	delay(1000);
}
```

![image](https://user-images.githubusercontent.com/80879966/112027096-72df5d00-8b69-11eb-9673-d481aa1b012b.jpg)

4.เข้าไปที่ configuration file ใน program
- พิมพ์ vi platformio.ini เพื่อแสดงข้อมูล

```javascript
; IOT for KIDS
;
; By Dr.Choompol Boonmee
; 

[env:exercise01]
platform = espressif8266
board = esp01_1m
framework = arduino
board_build.flash_mode = dout

upload_port = /dev/cu.usbserial-1420
;upload_port = COM3

monitor_port = /dev/cu.usbserial-1420
;monitor_port = COM3
monitor_speed = 115200
```

  - platform แสดงถึง เทคโนโลยีของบริษัทผู้ผลิต
  - board แสดงถึง ชื่อบอร์ด
  - framwork แสดงถึง วิธีการเขียนโปรแกรม
  - upload_port แสดงถึง portที่ใช้ติดต่อ 
    - ในกรณีนี้เป็น windows จึงแสดงว่า COM3 (หรือCOM4)

5.อัพโหลดโปรแกรม 01_Serial Monitor เข้าไปยัง microcontroller โดยใช้คำสั่ง upload
- พิมพ์ pio run -t upload
- ในขณะที่ program กำลังรันข้อมูล เพื่อให้ microcontroller รับโปรแกรมใหม่เข้าไป
  - กดปุ่มสีดำ เพื่อทำให้เกิดการload 
  - กดปุ่มสีแดง เพื่อให้เกิดการreset

![image](https://user-images.githubusercontent.com/80879966/112024929-41659200-8b67-11eb-8684-a86257d30a28.jpg)

- อัพโหลดเข้า microcontroller เสร็จสิ้น

![image](https://user-images.githubusercontent.com/80879966/112025795-1b8cbd00-8b68-11eb-89e9-aa61561284e4.jpg)

- สังเกตผลลัพธ์ที่แสดงผลผ่านคอมพิวเตอร์
  - พิมพ์ pio device monitor
    - PATTANI แสดงถึง ตัวแปรcountที่ถูกimplimentทีละ1,2,3ไปเรื่อยๆ โดยแสดงผลทุก 1 วินาที

![image](https://user-images.githubusercontent.com/80879966/112079578-038e5b00-8bb3-11eb-9a51-9aeab6db344d.jpg)

   - กดปุ่มสีแดง เพื่อทำการresetโปรแกรม  โดยโปรแกรมจะหยุดทำงานและเริ่มนับ 1 ใหม่

![image](https://user-images.githubusercontent.com/80879966/112079589-0721e200-8bb3-11eb-89ac-e9135632f920.jpg)

## การบันทึกผลการทดลอง 
  คำสั่ง | ผลลัพธ์ที่แสดง
  ------------ | -------------
  src/main.cpp | ผลลัพธ์ของโปรแกรมส่วน set up & loop
  platformio.ini | ข้อมูลใน configuration file
  pio run -t upload | รันข้อมูลในตัวอย่าง
  pio device monitor | PATTANIที่เพิ่มขึ้นใน 1 วินาที
  การกดปุ่มสีดำ | โปรแกรมถูกโหลด
  การกดปุ่มสีแดง | โปรแกรมถูกรีเซ็ต
  
## อภิปรายผลการทดลอง 
- platformio นั้น สามารถใช้เขียนโปรแกรมจาก microcontroller หลายชนิดที่มีบริษัทต่างกันได้ โดย คำสั่ง platformio.ini เป็นเหมือนตัวแสดงผลว่าการเขียนโปรแกรมครั้งนี้เราจะเขียนให้กับ microcontroller ตัวไหน
- pio run -t upload นั้นใช้ในการอัพโหลดข้อมูลไปยัง microcontroller โดยสามารถกดปุ่มซึ่งอยู่ภายนอก microcontroller เพื่อทำการโหลดและรีเซ็ตการรันโปรแกรมได้

## คำถามหลังการทดลอง 
หากต้องการให้โปรแกรมเริ่มนับใหม่อีกครั้ง ปุ่มใดบนmicrocontrollerที่สามารถใช้ได้
- [ ] ปุ่มสีดำ เพื่อให้เกิดการloadโปรแกรม
- [x] ปุ่มสีแดง เพื่อทำการresetโปรแกรม

