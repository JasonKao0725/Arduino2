# HYIVS Arduino Practical Class 2
# 2020/03/02 TUE
# Project1：七段數字循環顯示
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

