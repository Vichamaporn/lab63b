# การทดลองที่ 5 การเขียนโปรแกรมเชื่อมต่อไวไฟและเว็บเซอร์เวอร์

## วัตถุประสงค์ (อธิบายเป็นข้อๆ)
1. เพื่อ
2. เพือ่


## อุปกรณ์ที่ใช้ (รายการอุปกรณ์)
1. microcontroller


## แหล่งข้อมูลเพื่อการศึกษา
https://www.youtube.com/watch?v=VX-QNQcO-b4

## วิธีการทำการทดลอง (ทำเป็นขั้นตอนพร้อมภาพประกอบ)
1. เริ่มจาก

```javascript
#include <ESP8266WiFi.h>
//#include <WiFiClient.h>
#include <ESP8266WebServer.h>

const char* ssid = "HI_BMFWIFI_2.4G";
const char* password = "0819110933";

ESP8266WebServer server(80);

int cnt = 0;

void setup(void){
	Serial.begin(115200);

	WiFi.mode(WIFI_STA);
	WiFi.begin(ssid, password);
	while (WiFi.status() != WL_CONNECTED) {
		delay(500);
		Serial.print(".");
	}
	Serial.print("\n\nIP address: ");
	Serial.println(WiFi.localIP());

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
```

## การบันทึกผลการทดลอง (พร้อมตัวอย่าง)

## อภิปรายผลการทดลอง (พร้อมตัวอย่าง)

## คำถามหลังการทดลอง (พร้อมตัวอย่างคำตอบ)
