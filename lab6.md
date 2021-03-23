# การทดลองที่ 6 การเขียนโปรแกรมสร้างไวไฟแอคเซสพอยต์ (Wifi AP)

## วัตถุประสงค์ (อธิบายเป็นข้อๆ)
1.เพื่อ
2.เพื่อ


## อุปกรณ์ที่ใช้ (รายการอุปกรณ์)
1.microcontroller


## แหล่งข้อมูลเพื่อการศึกษา
https://www.youtube.com/watch?v=T26DVHePlTs

## วิธีการทำการทดลอง (ทำเป็นขั้นตอนพร้อมภาพประกอบ)
1.เริ่มจาก

```javascript
#include <ESP8266WiFi.h>
//#include <WiFiClient.h>
#include <ESP8266WebServer.h>

const char* ssid = "MY-ESP8266";
const char* password = "choompol";

IPAddress local_ip(192, 168, 1, 1);
IPAddress gateway(192, 168, 1, 1);
IPAddress subnet(255, 255, 255, 0);

ESP8266WebServer server(80);

int cnt = 0;

void setup(void){
	Serial.begin(115200);

	WiFi.softAP(ssid, password);
	WiFi.softAPConfig(local_ip, gateway, subnet);
	delay(100);

	server.onNotFound([]() {
		server.send(404, "text/plain", "Path Not Found");
	});

	server.on("/", []() {
		cnt++;
		String msg = "Hello cnt: ";
		msg += cnt;
		server.send(200, "text/plain", msg);
	});

	server.begin();
	Serial.println("HTTP server started");
}

void loop(void){
  server.handleClient();
}

© 2021 GitHub, Inc.
```

## การบันทึกผลการทดลอง 
First Header | Second Header
------------ | -------------
Content from cell 1 | Content from cell 2
Content in the first column | Content in the second column

## อภิปรายผลการทดลอง (พร้อมตัวอย่าง)

## คำถามหลังการทดลอง 
คำถาม
- [x] คำตอบถูก
- [ ] คำตอบผิด
