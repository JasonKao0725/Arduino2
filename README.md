# 109-2 HYIVS Arduino Practical Class
## 2021/03/02 TUE
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
