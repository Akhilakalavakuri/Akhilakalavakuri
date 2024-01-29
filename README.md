//****** VOICE OPERATED ON OFF CONTROLS ***
String readString;
#define MOTOR
10
#define LIGHT 6
#define BUZZER 13
#define FAN 9
//**************************************
void setup()
{
pinMode(MOTOR,OUTPUT);
pinMode(LIGHT,OUTPUT);
pinMode(BUZZER,OUTPUT);
pinMode(FAN,OUTPUT);
Serial.begin(9600);
digitalWrite(BUZZER,1);
delay(500);
digitalWrite(BUZZER,0);
delay(500);
digitalWrite(BUZZER,1);
delay(500);
digitalWrite(BUZZER,0);
delay(500);
}
//***************************************
void loop()
{
while(Serial.available())
{
delay(3);
char c = Serial.read();
readString+=c;
}
//
if(readString.length() >0)
//
if(readString == "light on") {
digitalWrite(LIGHT,1);
delay(500); }
else if(readString == "light off") {
digitalWrite(LIGHT,0);
delay(500); }
//
else if(readString == "motor on") {
digitalWrite(MOTOR,1);
delay(500); }
else if(readString == "motor off") {
digitalWrite(MOTOR,0);
delay(500); }
//
else if(readString == "fan on") {
digitalWrite(FAN,1);
delay(500); }
else if(readString == "fan off") {
digitalWrite(FAN,0);
delay(500);
}
// 
else if(readString == "motor slow")
{
analogWrite(MOTOR,170);
delay(500);
}
else if(readString == "motor speed")
{
analogWrite(MOTOR,250);
delay(500);
}
// 
Else
{
delay(100);
}
readString = "";
}
}
//****************************************
