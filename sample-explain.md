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
	
	
	pinMode(0, OUTPUT);		//set ใหเ port 0 เป็น port output
	
	
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

int cnt = 0;

void setup()
{
	Serial.begin(115200);
	pinMode(0, INPUT);
	pinMode(2, OUTPUT);
	Serial.println("\n\n\n");
}

void loop()
{
	int val = digitalRead(0);
	Serial.printf("======= read %d\n", val);
	if(val==1) {
		digitalWrite(2, LOW);
	} else {
		digitalWrite(2, HIGH);
	}
	delay(100);
}





