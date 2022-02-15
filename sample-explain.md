# แลป 1 
#include <Arduino.h>

int cnt = 0;

void setup()
{
	Serial.begin(115200);
}

void loop()
{
	cnt++;
	Serial.printf("A:%d\n",cnt);
	delay(300);
}
