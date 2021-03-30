# 109-2 HYIVS Arduino Practical Class
## 2021/03/02
### Project1：七段數字循環顯示
程式碼：
```c++
int a[10][7] ={
{1,1,1,1,1,1,0},
{0,1,1,0,0,0,0},
{1,1,0,1,1,0,1},
{1,1,1,1,0,0,1},
{0,1,1,0,0,1,1},
{1,0,1,1,0,1,1},
{1,0,1,1,1,1,1},
{1,1,1,0,0,0,0},
{1,1,1,1,1,1,1},
{1,1,1,1,0,1,1}
};
void setup() {
int i;
for (i = 2; i<13;i++)
  pinMode(i,OUTPUT);
}
void loop() {
for (int i = 9;i<13;i++)
  digitalWrite(i,HIGH);
for (int j = 0;j<10;j++)
  {for (int i = 2; i<9;i++)
  digitalWrite(i,a[j][i-2]);
  delay(200);}
}
```
成品圖：

![image](https://raw.githubusercontent.com/JasonKao0725/Arduino2/main/855D0CA8-6B8D-44D7-9892-E31C33284EBA.gif)
### Project2：四個七段顯示器顯示不同數字
程式碼：
```c++
int a[10][7] ={
{1,1,1,1,1,1,0},
{0,1,1,0,0,0,0},
{1,1,0,1,1,0,1},
{1,1,1,1,0,0,1},
{0,1,1,0,0,1,1},
{1,0,1,1,0,1,1},
{1,0,1,1,1,1,1},
{1,1,1,0,0,0,0},
{1,1,1,1,1,1,1},
{1,1,1,1,0,1,1}
};
float c;
int b[4][4] ={
  {1,0,0,0},
  {0,1,0,0},
  {0,0,1,0},
  {0,0,0,1},
};
int d[4] = {6,5,4,3};
void setup() {
int i;
for (i = 2; i<13;i++)
  pinMode(i,OUTPUT);
  c = millis();
  Serial.begin(9600);
}
void loop() {
for (int j = 0;j<4;j++){
for(int k=9;k<13;k++)
   digitalWrite(k,b[j][k-9]);
   for(int i=2;i<9;i++)
     digitalWrite(i,a[d[j]][i-2]);
   delay(5);
}
```
成品圖：

![image](https://github.com/JasonKao0725/Arduino/blob/master/1AAC3FD4-5878-4E8B-A56F-5D8F7E00D08C.jpeg)
## 2021/03/09
### Project1-1：LCD右移
程式碼：
```c++
#include <LiquidCrystal.h>
const int rs = 12, en = 11, d4 = 5, d5 = 4, d6 = 3, d7 = 2;
LiquidCrystal lcd(rs, en, d4, d5, d6, d7);
void setup() {
  lcd.begin(16, 2);
  lcd.print("hello,WORLD!");
}
void loop() {
  delay(3000);
  lcd.clear();
  lcd.setCursor(0,1);
  lcd.print("RRRRRRRRRRRR");
  lcd.scrollDisplayRight();
  lcd.noBlink();
  delay(3000);
}
```
成品圖：

![image](https://github.com/JasonKao0725/Arduino2/blob/main/E16BA290-2903-483C-829A-A90760870C95.gif)
### Project1-2：LCD顯示圖形
程式碼：
```c++
byte smiley[8] = {
  B00000,
  B10001,
  B00000,
  B00000,
  B10001,
  B01110,
  B00000,
};
#include <LiquidCrystal.h>
const int rs = 12, en = 11, d4 = 5, d5 = 4, d6 = 3, d7 = 2;
LiquidCrystal lcd(rs, en, d4, d5, d6, d7);
void setup() {
  lcd.begin(16, 2);
  lcd.print("hello,WORLD!");
}
void loop() {
  delay(3000);
  lcd.clear();
  lcd.setCursor(0,1);
  lcd.createChar(0, smiley);
  lcd.setCursor(0,1);
  lcd.write(byte(0));
  }
}
```
成品圖：

![image](https://github.com/JasonKao0725/Arduino2/blob/main/1C79A644-4478-4045-8A16-9C9816FE32D9.gif)
### Project1-3：LCD圖形循環顯示
程式碼：
```c++
byte smiley[8] = {
  B00000,
  B10001,
  B00000,
  B00000,
  B10001,
  B01110,
  B00000,
};
#include <LiquidCrystal.h>
const int rs = 12, en = 11, d4 = 5, d5 = 4, d6 = 3, d7 = 2;
LiquidCrystal lcd(rs, en, d4, d5, d6, d7);
void setup() {
  lcd.begin(16, 2);
  lcd.print("hello,WORLD!");
}
void loop() {
  delay(3000);
  lcd.clear();
  lcd.setCursor(0,1);
  lcd.createChar(0, smiley);
  for(int i=0;i<16;i++){
  delay(100);
  lcd.setCursor(i,1);
  lcd.write(byte(0));
  }
}
```
成品圖：

![image](https://github.com/JasonKao0725/Arduino2/blob/main/5734F181-8029-4243-9356-04E32647E54E.gif)
### Project2：按鈕控制LCD文字位置
程式碼：
```c++
#include <LiquidCrystal.h>
LiquidCrystal lcd(12,11,5,4,3,2);
byte smiley[8] = {
  B00000,
  B10001,
  B00000,
  B00000,
  B10001,
  B01110,
  B00000,
};
bool haha=1,haha2=1;
void setup() {
  Serial.begin(9600);
  pinMode(8,1);
  pinMode(9,1);
  lcd.begin(16,2);
  lcd.noCursor();
  lcd.createChar(0,smiley);
  lcd.clear();
  lcd.print("hahahaha");
}
void loop() {
  if(digitalRead(8))
  {
    while(digitalRead(8));{delay(20);}
    lcd.scrollDisplayLeft(); 
  }
  
  if(digitalRead(9))
  {
    while(digitalRead(9));{delay(20);}
    lcd.scrollDisplayRight(); 
  }
  Serial.print(digitalRead(8));
  Serial.print(digitalRead(9));
  Serial.println(haha);
}
```
成品圖：

![image](https://github.com/JasonKao0725/Arduino2/blob/main/11AEE55C-ACD2-49A7-9649-9A4154A1B9D9.gif)
## 2021/03/16
### Project1：風扇三段轉速控制
程式碼：
```c++
void setup() {
  pinMode(5,OUTPUT);//IN1
  pinMode(6,OUTPUT);//IN2
}
void loop() {
  for(int i=80;i<255;i+=86){
    analogWrite(5,i);
    analogWrite(6,0);
    delay(5000);
  }
}
```
成品圖：

![image](https://github.com/JasonKao0725/Arduino2/blob/main/1C88798E-BDB2-4CA0-9510-4C5DE0C8571F.gif)
### Project2：按鈕控制風扇轉速、開關
程式碼：
```c++
int i;
void setup() {
  pinMode(5,OUTPUT);
  pinMode(6,OUTPUT);
  pinMode(2,INPUT);
  Serial.begin(9600);
}
void motor(int i) {
  analogWrite(5,i);
  analogWrite(6,0);
}
void loop() {
  Serial.println(i);
  if(digitalRead(2)==LOW) {
    while(digitalRead(2)==LOW);
    i=i+35;
  }
  else if(digitalRead(3)==LOW) {
    while(digitalRead(3)==LOW);
    i=i-35;
  }
  else if(digitalRead(4)==LOW) {
    while(digitalRead(4)==LOW);
    i=80;
  }
  else if(digitalRead(7)==LOW) {
    while(digitalRead(7)==LOW);
    i=0;
  }
  if(i>=255) {
    i=255;
  }
  else if(i<=0) {
    i = 0;
  }
  motor(i);
}
```
成品圖：

![image](https://github.com/JasonKao0725/Arduino2/blob/main/37883E3E-F841-445B-B8D0-FE731D93C19C.gif)
## 2021/03/30
### Project1：溫濕度感應器，溫度達設定數值即使蜂鳴器作動
程式碼：
```c++
// DHT Temperature & Humidity Sensor
// Unified Sensor Library Example
// Written by Tony DiCola for Adafruit Industries
// Released under an MIT license.

// REQUIRES the following Arduino libraries:
// - DHT Sensor Library: https://github.com/adafruit/DHT-sensor-library
// - Adafruit Unified Sensor Lib: https://github.com/adafruit/Adafruit_Sensor

#include <Adafruit_Sensor.h>
#include <DHT.h>
#include <DHT_U.h>

#define DHTPIN 2     // Digital pin connected to the DHT sensor 
// Feather HUZZAH ESP8266 note: use pins 3, 4, 5, 12, 13 or 14 --
// Pin 15 can work but DHT must be disconnected during program upload.

// Uncomment the type of sensor in use:
//#define DHTTYPE    DHT11     // DHT 11
#define DHTTYPE    DHT22     // DHT 22 (AM2302)
//#define DHTTYPE    DHT21     // DHT 21 (AM2301)

// See guide for details on sensor wiring and usage:
//   https://learn.adafruit.com/dht/overview

DHT_Unified dht(DHTPIN, DHTTYPE);

uint32_t delayMS;
double a;
void setup() {
  pinMode(3,OUTPUT);
  pinMode(5,OUTPUT);
  pinMode(6,OUTPUT);
  Serial.begin(9600);
  // Initialize device.
  dht.begin();
  sensor_t sensor;
  /*Serial.println(F("DHTxx Unified Sensor Example"));
  // Print temperature sensor details.
  
  dht.temperature().getSensor(&sensor);
  Serial.println(F("------------------------------------"));
  Serial.println(F("Temperature Sensor"));
  Serial.print  (F("Sensor Type: ")); Serial.println(sensor.name);
  Serial.print  (F("Driver Ver:  ")); Serial.println(sensor.version);
  Serial.print  (F("Unique ID:   ")); Serial.println(sensor.sensor_id);
  Serial.print  (F("Max Value:   ")); Serial.print(sensor.max_value); Serial.println(F("°C"));
  Serial.print  (F("Min Value:   ")); Serial.print(sensor.min_value); Serial.println(F("°C"));
  Serial.print  (F("Resolution:  ")); Serial.print(sensor.resolution); Serial.println(F("°C"));
  Serial.println(F("------------------------------------"));
  // Print humidity sensor details.
  dht.humidity().getSensor(&sensor);
  Serial.println(F("Humidity Sensor"));
  Serial.print  (F("Sensor Type: ")); Serial.println(sensor.name);
  Serial.print  (F("Driver Ver:  ")); Serial.println(sensor.version);
  Serial.print  (F("Unique ID:   ")); Serial.println(sensor.sensor_id);
  Serial.print  (F("Max Value:   ")); Serial.print(sensor.max_value); Serial.println(F("%"));
  Serial.print  (F("Min Value:   ")); Serial.print(sensor.min_value); Serial.println(F("%"));
  Serial.print  (F("Resolution:  ")); Serial.print(sensor.resolution); Serial.println(F("%"));
  Serial.println(F("------------------------------------"));
  // Set delay between sensor readings based on sensor details.*/
  delayMS = sensor.min_delay / 1000;
}
void Motor(int a){
  if(a == 1){
      digitalWrite(5,HIGH);
      digitalWrite(6,LOW);
    }
    else{
      digitalWrite(5,HIGH);
      digitalWrite(6,HIGH);
    }
}
void loop() {
  // Delay between measurements.
  delay(delayMS);
  // Get temperature event and print its value.
  sensors_event_t event;
  dht.temperature().getEvent(&event);
  if (isnan(event.temperature)) {
    Serial.println(F("Error reading temperature!"));
  }
  else {
    Serial.print(F("Temperature: "));
    Serial.print(event.temperature);
    Serial.println(F("°C"));
    a = event.temperature;
  }
  // Get humidity event and print its value.
  dht.humidity().getEvent(&event);
  if (isnan(event.relative_humidity)) {
    Serial.println(F("Error reading humidity!"));
  }
  else {
    Serial.print(F("Humidity: "));
    Serial.print(event.relative_humidity);
    Serial.println(F("%"));
  }
  if(a>=27){
    tone(3,500);
    delay(500);
    noTone(3);
    delay(500);
    Motor(1);
  }
  Motor(0);
}
```
成品圖：

![image](https://github.com/JasonKao0725/Arduino2/blob/main/image.jpg)
