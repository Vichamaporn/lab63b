# การทดลองที่ 3 การเขียนโปรแกรมเอ้าพุทสัญญาณดิจิทัล

## วัตถุประสงค์ 
1.เพื่อ
2.เพื่อ

## อุปกรณ์ที่ใช้ 
1. microcontroll


## แหล่งข้อมูลเพื่อการศึกษา
- https://www.youtube.com/watch?v=CCnN1WJsXQY
- https://www.youtube.com/watch?v=6JnhaUILGuw

## วิธีการทำการทดลอง (ทำเป็นขั้นตอนพร้อมภาพประกอบ)

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
