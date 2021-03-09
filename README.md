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
