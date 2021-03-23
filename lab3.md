# การทดลองที่ 3 การเขียนโปรแกรมเอ้าพุทสัญญาณดิจิทัล

## วัตถุประสงค์ 
1. เพื่อศึกษาหน้าที่ของ Relay
2. เพื่อให้สามารถเขียนโปรแกรมและรัน microcontroller ที่ต่อกับ adapter และให้มี output ออกมาภายนอกได้


## อุปกรณ์ที่ใช้ 
1. Relay
2. adapter
3. หลอด LED เปล่งแสง
4. microcontroller ESP-01
5. อุปกรณ์เชื่อมต่อ USB เข้าไปยัง serial



## แหล่งข้อมูลเพื่อการศึกษา
- https://www.youtube.com/watch?v=CCnN1WJsXQY
- https://www.youtube.com/watch?v=6JnhaUILGuw

## วิธีการทำการทดลอง (ทำเป็นขั้นตอนพร้อมภาพประกอบ)
1. นำ adapter(ต่อกับLED) ต่อเข้ากับ USB 
2. ทำการเสียบ microcontroller เข้าทาง serial port ของ USB 
3. ดูที่ตัวอย่างโปรแกรม ที่โฟลเดอร์ pattani
- พิมพ์ cd pattani เพื่อไปยังโฟลเดอร์
- แสดงโฟลเดอร์ ซึ่งมีโปรแกรมตัวอย่าง 9 โปรแกรม
  - ไปที่ตัวอย่างที่ 3
    - พิมพ์ cd 03_Output-Port
    
![image](https://user-images.githubusercontent.com/80879942/112137666-1e88bb80-8c03-11eb-866b-b516ad5036b6.jpg)

3. ดู source code program 
- พิมพ์ vi src/main.cpp
- set up 1 ครั้ง โดยการ set up serial port ที่ความเร็ว 115200
- ใน loop แสดงให้เห็นถึงการวนไปเรื่อยๆ ในบรรทัดต่างๆ ประกอบด้วย
  - cnt++ หมายถึง การนับเพิ่มเรื่อยๆ 
    - หาก cnt%2 แปลว่า ตัวเลขเป็นเลขคี่ ให้ดำเนินการ on
    - หากไม่ใช่ แปลว่า ตัวเลขเป็นเลขคู่ ให้ดำเนินการ off
  - delay(500) หมายถึง ช่วงเวลา 500 ms 
 
```javascript
#include <Arduino.h>
#include <ESP8266WiFi.h>

int cnt = 0;

void setup()
{
	Serial.begin(115200);
	pinMode(0, OUTPUT);
	Serial.println("\n\n\n");
}

void loop()
{
	cnt++;
	if(cnt % 2) {
		Serial.println("========== ON ===========");
		digitalWrite(0, HIGH);
	} else {
		Serial.println("========== OFF ===========");
		digitalWrite(0, LOW);
	}
	delay(500);
}
```

4. อัพโหลดโปรแกรม 03_Output-Port เข้าไปยัง microcontroller โดยใช้คำสั่ง upload
   - พิมพ์ pio run -t upload
   - ในขณะที่ program กำลังรันข้อมูล เพื่อให้ microcontroller รับโปรแกรมใหม่เข้าไป
     - กดปุ่มสีแดง เพื่อให้เกิดการ reset
     
![image](https://user-images.githubusercontent.com/80879942/112140260-5e9d6d80-8c06-11eb-9a5d-70b1e3322553.jpg)

 
   - สังเกตผลลัพธ์ที่แสดงผลผ่านคอมพิวเตอร์
     - พิมพ์ pio device monitor

5. จากนั้น นำ microcontroller ต่อเข้ากับ Relay เพื่อให้ Relay ทำหน้าที่เปิด-ปิดสวิตซ์ แล้วนำแหล่งจ่ายไฟมาต่อเข้ากับตัว Relay เพื่อจ่ายไฟให้ Relay ทำงานได้
6. เมื่อต่อ microcontroller เข้ากับ Relay การทำงานของ Relay จะทำให้เกิดการเปิด-ปิด สวิตซ์ ดังภาพ
   
![image](https://user-images.githubusercontent.com/80879942/112144123-5eec3780-8c0b-11eb-94d0-840e7917e15a.jpg)

## การบันทึกผลการทดลอง 
- ก่อนทำการต่อ Relay
**ผลลัพธ์ออกมาเป็น on off สลับกันไปเรื่อยๆ**

count | ลักษณะสีของหลอดไฟ
------------ | -------------
เลขคี่ | สีเขียวจะติดดับๆสลับกัน
เลขคู่ | ไฟสีน้ำเงินจะไม่ติด
 
![image](https://user-images.githubusercontent.com/80879942/112142078-ba68f600-8c08-11eb-97b0-456029f00641.jpg)
   


## อภิปรายผลการทดลอง (พร้อมตัวอย่าง)

## คำถามหลังการทดลอง
คำถาม
- [ ] คำตอบผิด
- [x] คำตอบถูก
