# อธิบายโปรแกรม
### ในตัวโปรแกรมจะถูกแยกเป็นสองส่วนคือ ส่วน set-up(รันครั้งเดียว) ส่วนLoop(รันวนไปเรื่อยๆ)
## แลป 1 
#include <Arduino.h>


int cnt = 0;			//สร้างตัวแปร cnt โดยให้มีค่า = 0


void setup()


{


	Serial.begin(115200);			//set serial port ที่ความเร็ว 115200 B/s
	
	
}


void loop()


{


	cnt++;			//ให้ cnt +1
	
	
	Serial.printf("A:%d\n",cnt);			//แสดงค่าของตัวแปร cnt 
	
	
	delay(300);			//ให้หน่วงเวลา 300 ms
	
	
}
## แลป 2
#include <Arduino.h>


#include <ESP8266WiFi.h>


int cnt = 0;		//สร้างตัวแปร cnt โดยให้มีค่า = 0


void setup()


{


	Serial.begin(115200);		//ตั้งความเร็วสื่อสารที่ 115200 และสั่งให้เริ่มทำงาน
	
	
	WiFi.mode(WIFI_STA);	// ตั้งค่า WiFi เป็นโหมดสถานีและตัดการเชื่อมต่อจากเครื่อข่ายหากเชื่อมต่อไว้ก่อนหน้านี้	
	
	
	WiFi.disconnect();
	
	
	delay(100);
	
	
	Serial.println("\n\n\n");			//เว้น 3 บรรทัด
	
	
}


void loop()


{


	Serial.println("========== เริ่มต้นแสกนหา Wifi ===========");
	
	
	int n = WiFi.scanNetworks();			//แสดงจำนวนเครื่อยข่ายที่พบในรูปตัวแปร n
	
	
	if(n == 0) {
	
	
		Serial.println("NO NETWORK FOUND");			//กรณีไม่เจอ wifi
		
		
	} else {
	
	
		for(int i=0; i<n; i++) { 		// Print SSID และ RSSI ของเครื่อยข่ายที่มีสัญญาน
		
		
			Serial.print(i + 1);
			
			
			Serial.print(": ");
			
			
			Serial.print(WiFi.SSID(i));
			
			
			Serial.print(" (");
			
			
			Serial.print(WiFi.RSSI(i));
			
			
			Serial.print(")");
			
			
			Serial.println((WiFi.encryptionType(i) == ENC_TYPE_NONE)?" ":"*");
			
			
			delay(10);			 หน่วงเวลาในการแสกนทุกๆ 10ms
			
			
		}
		
		
	}
	
	
	Serial.println("\n\n");
	
	
}
## แลป 3
#include <Arduino.h>


#include <ESP8266WiFi.h>


int cnt = 0;		//สร้างตัวแปร cnt โดยให้มีค่า = 0


void setup()


{


	Serial.begin(115200);		//set serial port ที่ความเร็ว 115200 B/s
	
	
	pinMode(0, OUTPUT);		//set ให้ port 0 เป็น port output
	
	
	Serial.println("\n\n\n");			//เว้น 3 บรรทัด
	
	
}



void loop()			//เมื่อ cnt เป็นเลขคี่ให้ on และเมื่อเป็นเลขคู่ให้off


{


	cnt++;				//ตัวแปร cnt +1
	
	
	if(cnt % 2) {
	
	
		Serial.println("========== ON ===========");
		
		
		digitalWrite(0, HIGH);
		
		
	} else {
	
	
		Serial.println("========== OFF ===========");
		
		
		digitalWrite(0, LOW);
		
		
	}
	
	
	delay(500);			//หน่วงเวลา 500 ms
	
	
}
## แลป4
		#include <Arduino.h>
		#include <ESP8266WiFi.h>

		int cnt = 0;		//สร้างตัวแปร cnt โดยให้มีค่า = 0

		void setup()
		{
			Serial.begin(115200);		//set serial port ที่ความเร็ว 115200 B/s
			pinMode(0, INPUT);		//กำหนดport 0 เป็นโหมด INPUT
			pinMode(2, OUTPUT);		//กำหนดport 2 เป็นโหมด OUTPUT
			Serial.println("\n\n\n");	//เว้น3บรรทัด
		}

		void loop()
		{
			int val = digitalRead(0);			//อ่านค่าจากport 0 ไปเก็บในตัวแปร val ซึ่งจะมีค่าเป็น 0 หรือ 1 เท่านั้น
			Serial.printf("======= read %d\n", val);			//แสดง val
			if(val==1) {			//ถ้า val = 1 ให้่ port 2 ไฟดับ
				digitalWrite(2, LOW);
			} else {			//ถ้า val = 0 ให้่ port 2 ไฟติด
				digitalWrite(2, HIGH);
			}
			delay(100);		หน่วงเวลา 100 ms
		}

## แลป 5
		#include <ESP8266WiFi.h>
		#include <ESP8266WiFiMulti.h>
		#include <ESP8266WebServer.h>

		const char* ssid = "HI_BMFWIFI_2.4G";		//ชื่อ SSID  ของตัวเอง
		const char* password = "0819110933";		//ชื่อ password ของตัวเอง

		ESP8266WiFiMulti wifiMulti;
		ESP8266WebServer server(80);

		int cnt = 0;

		void setup(void){
			Serial.begin(115200);		//set serial port ที่ความเร็ว 115200 B/s

			wifiMulti.addAP(ssid, password);

			Serial.println("Connecting ...");
			int i = 0;
			while (wifiMulti.run() != WL_CONNECTED) { 			//connect กับ wifi ที่เราเลือกไว้
				delay(1000);			//หน่วงเวลา 1000 ms
				Serial.print(++i); Serial.print(' ');
			}
			Serial.println("");
			Serial.print("IP address: ");
			Serial.println(WiFi.localIP());

			server.onNotFound([]() {
				server.send(404, "text/plain", "Path Not Found");
			});

			server.on("/", []() {			//set up web serverของเราถ้ามีการเชื่อมโยงแสดง Hello cnt
				cnt++;			//cnt +1
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


## แลป 6
		#include <ESP8266WiFi.h>
		//#include <WiFiClient.h>
		#include <ESP8266WebServer.h>

		const char* ssid = "MY-ESP8266";		//ชื่อ SSID  ของตัวเอง
		const char* password = "choompol";		//ชื่อ password ของตัวเอง
		IPAddress local_ip(192, 168, 1, 1);			// กำหนดค่าตัวแปร local_ip ให้มีค่าเท่ากับ 192.168.1.1
		IPAddress gateway(192, 168, 1, 1);			//กำหนดค่าตัวแปร gateway ให้มีค่าเท่ากับ 192.168.1.1
		IPAddress subnet(255, 255, 255, 0);			 กำหนดค่าตัวแปร subnet ให้มีค่าเท่ากับ 255.255.255.0

		ESP8266WebServer server(80);		//เปิดweb server ที่ port 80

		int cnt = 0;

		void setup(void){
			Serial.begin(115200);			//  ใช้งานฟังก์ชัน Serial โดยตั้งค่าอัตราเร็ว Baud rate ของ Serial อยู่ที่ 115200 บิตต่อวินาที

			WiFi.softAP(ssid, password);			//ใช้งานฟังก์ชัน WiFi.softAP เพื่อให้ AP เริ่มทำงาน
			WiFi.softAPConfig(local_ip, gateway, subnet);			 //ใช้งานฟังก์ชัน WiFi.softAPConfig เพื่อตั้งค่า IP , gateway , subnet ให้ AP
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
