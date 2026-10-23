***

### Fan Performance 風扇性能 

風扇透過葉輪對對空氣流體輸入機械能，使得流體的機械能增加、並在特定量測條件下的表現為風扇兩側壓力提升。當風扇與系統連結之後，風扇讓流體壓力提升的能力與系統壓力損失共同決定實際系統的流量。風扇與另一個不同的尺寸或規格的風扇、也會有不同的轉速以及電流需求(功率)。
  - Flow Rate ： 風扇本體的流量可以表示為 Q = A * V ，這個公式的含義是體積流率可以由通過某一截面的平均速度與截面積的乘積。
  - Pressure ： 風扇能夠建立的壓差的能力，其中要注意的是壓差是指風扇吸入風與推出風的兩側之壓力差。（至於全壓，意思是因為有額外的機械能所增加的動壓再加上靜壓。）
  - Power ： 提供風扇轉動的電功率，直接影響風扇轉速。

```
實際上至少要區分：
Electrical Power> Motor馬達功率> Shaft Power軸功率> Fan aerodynamic Power

而且風扇實際 RPM 是由：
motor torque、load torque、controller、operating condition
```



***
# 筆記一下
###### Fan Laws & Fan Performance Explained

[https://fluidflowinfo.com/fan-performance-and-fan-laws/]

Fan Laws 是描述一個定律或是規則，用來預測固定系統內的風扇性能。

可以知道 一個風扇的PQ之後，推估其他rpm 的PQ

其實蠻神的



***
喃喃低語 : fan laws也適用 Pump(CDU水冷機)、也就是 Pump Laws

***
問題 1：為什麼可以 Scale？
→ Similarity

問題 2：為什麼 Flow 是 `N * D³`？
→ 幾何尺度＋速度尺度

問題 3：為什麼 Pressure 是 `N² * D² `
→ 速度平方尺度與壓力/動壓尺度

問題 4：為什麼 Power 是 ` N³ * D⁵ `？
→ Flow × Pressure 的尺度關係

***
```
Fan Laws
│
├─ 1. 為什麼需要 Fan Laws？
│
├─ 2. Fan Performance 是什麼？
│   ├─ Flow
│   ├─ Pressure
│   └─ Power
│
├─ 3. Fan Laws 的基本 Scaling
│   ├─ Speed
│   ├─ Diameter
│   └─ Density
│
├─ 4. 為什麼會出現 N、D³、N²、D⁵？
│
├─ 5. Similarity Conditions
│   ├─ Geometric Similarity
│   ├─ Reynolds Number
│   └─ Mach Number
│
├─ 6. Fan Laws 與 PQ Curve
│
├─ 7. Fan Laws 與 Working Point
│
├─ 8. Server Fan / PWM / RPM 實務
│
└─ 9. Fan Laws 的適用限制


```
