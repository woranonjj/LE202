# อธิบายโปรแกรม
### ในตัวโปรแกรมจะถูกแยกเป็นสองส่วนคือ ส่วน set-up(รันครั้งเดียว) ส่วนLoop(รันวนไปเรื่อยๆ)
## แลป 1 
#include <Arduino.h>


int cnt = 0;


void setup()


{


	Serial.begin(115200);         **set serial port ที่ความเร็ว 115200**
	
	
}


void loop()


{


	cnt++;
	
	
	Serial.printf("A:%d\n",cnt);
	
	
	delay(300);
	
	
}
