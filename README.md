# Bidirectional-visitor-counter
#include <LiquidCrystal.h>
LiquidCrystallcd(2,3,4,5,6,7);
#define in 8
#define out 9
#define led 10
int count=0;
void setup() {
lcd.begin(16,2);
lcd.print("People counter");
delay(2000);
pinMode(in, INPUT);
pinMode(out, INPUT);
pinMode(led, OUTPUT);
}
void loop() {
 int in_value = digitalRead(in);
  int out_value = digitalRead(out);
if(in_value == LOW)
 {
 count++;
lcd.clear();
lcd.setCursor(1,0);
lcd.print("Person in room : ");
lcd.setCursor(0,1);
lcd.print(count);
delay(1000);
 }
if(out_value == LOW)
 {
 count--;
lcd.clear();
lcd.setCursor(1,0);
lcd.print("Person in room : ");
lcd.setCursor(0,1);
lcd.print(count);
delay(1000); 
}
 if(count==0)
 {
lcd.clear();
digitalWrite(led,LOW);
lcd.clear();
lcd.print("Nobody in the Room");
lcd.setCursor(0,1);
lcd.print("Light is off");
delay(200);
 }
else{
digitalWrite(led, HIGH);
 }
 }
