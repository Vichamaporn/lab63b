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
1. ทำการเสียบ microcontroller เข้าทาง serial port ของ USB 
2. ดูที่ตัวอย่างโปรแกรม ที่โฟลเดอร์ pattani
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

## การบันทึกผลการทดลอง (พร้อมตัวอย่าง)
First Header | Second Header
------------ | -------------
Content from cell 1 | Content from cell 2
Content in the first column | Content in the second column


## อภิปรายผลการทดลอง (พร้อมตัวอย่าง)

## คำถามหลังการทดลอง
คำถาม
- [ ] คำตอบผิด
- [x] คำตอบถูก
