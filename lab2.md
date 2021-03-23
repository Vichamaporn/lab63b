# การทดลองที่ 2 การเขียนโปรแกรมค้นหาไวไฟ

## วัตถุประสงค์ 
1. เพื่อรันโปรแกรมบน microcontroller ในการค้นหา wifi

## อุปกรณ์ที่ใช้ 
1. CPU
2. เสาอากาศสำหรับรับ wifi
3. อุปกรณ์เชื่อมต่อ USB เข้าไปยัง serial
4. microcontroller ESP-01 ที่มี wifi ในตัวเอง

## แหล่งข้อมูลเพื่อการศึกษา
https://www.youtube.com/watch?v=yBjab0UNuB8

## วิธีการทำการทดลอง (ทำเป็นขั้นตอนพร้อมภาพประกอบ)

1. เสียบไมโครคอนโทรลเลอร์ใน USB to serealพอร์ต
2. อัปโหลดโปรแกรมโดยรันคำสั่ง upload image
3. กดปุ่มอัปโหลด
4. กดปุ่มรีเซ็ต image
5. เมื่อuploadครบ100%
  - พิมพ์ pio device monitor image

```javascript
#include <Arduino.h>
#include <ESP8266WiFi.h>

int cnt = 0;

void setup()
{
	Serial.begin(115200);
	WiFi.mode(WIFI_STA);
	WiFi.disconnect();
	delay(100);
	Serial.println("\n\n\n");
}

void loop()
{
	Serial.println("========== เริ่มต้นแสกนหา Wifi ===========");
	int n = WiFi.scanNetworks();
	if(n == 0) {
		Serial.println("NO NETWORK FOUND");
	} else {
		for(int i=0; i<n; i++) {
			Serial.print(i + 1);
			Serial.print(": ");
			Serial.print(WiFi.SSID(i));
			Serial.print(" (");
			Serial.print(WiFi.RSSI(i));
			Serial.println(")");
			delay(10);
		}
	}
	Serial.println("\n\n");
}
```

## การบันทึกผลการทดลอง 
First Header | Second Header
------------ | -------------
Content from cell 1 | Content from cell 2
Content in the first column | Content in the second column


## อภิปรายผลการทดลอง
จากการทดลองสามารถค้นหาwifiที่มีสัญญาณอยู่บริเวณนั้นๆได้

## คำถามหลังการทดลอง 
คำถาม
- [x] คำตอบถูก
- [ ] คำตอบผิด
