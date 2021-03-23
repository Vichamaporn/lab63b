# การทดลองที่ 2 การเขียนโปรแกรมค้นหาไวไฟ

## วัตถุประสงค์ (อธิบายเป็นข้อๆ)
1. เพื่อรันโปรแกรมบน microcontroller ในการค้นหา wifi

## อุปกรณ์ที่ใช้ (รายการอุปกรณ์)
1. CPU
2. อุปกรณ์เชื่อมต่อ USB
3. เสาอากาศสำหรับรับ wifi
4. microcontroller ESP-01 ที่มี wifi ในตัวเอง


## แหล่งข้อมูลเพื่อการศึกษา
https://www.youtube.com/watch?v=yBjab0UNuB8

## วิธีการทำการทดลอง (ทำเป็นขั้นตอนพร้อมภาพประกอบ)

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

## การบันทึกผลการทดลอง (พร้อมตัวอย่าง)

## อภิปรายผลการทดลอง (พร้อมตัวอย่าง)

## คำถามหลังการทดลอง (พร้อมตัวอย่างคำตอบ)
