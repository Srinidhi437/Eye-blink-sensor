# Eye-blink-sensor
The eye blink sensor constantly sends infrared waves which are reflected and detected by the receiver
coding:
const int blinkPin=2;
const int motorPin=13;
const int buzzerPin=12;
long time;
void setup()
{
pinMode(blinkPin,OUTPUT);
pinMode(motorPin,OUTPUT);
pinMode(buzzerPin,OUTPUT);
digitalWrite(motorPin,HIGH);
}
void loop()
{
if(!digitalRead(blinkPin))
{
time=millies();
while(!digitalRead(blinkPin))
{
digitalWrite(buzzerPin,LOW);
digitalWrite(motorPin,LOW);
delay(1000);
}
}
else
{
if(TimeDelay()>=3)digitalWrite(buzzerPin,HIGH);
if(TimeDelay()>=4)digitalWrite(motorPin,HIGH);
}
}
int TimeDelay()
{
longt t=millis()-time;
t=t/1000;
return t;
}
