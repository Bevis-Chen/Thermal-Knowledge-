# Fan Laws

## 目錄

- 前言
- Fan Performance 風扇性能

### 前言 

伺服器系統裡面常常有風扇的存在，不同的風扇尺寸、或是不同的廠商提供的風扇都會是工程師驗證測試時考慮的因素。本文除了解釋Fan Laws之外，也會盡作者的能力去結合實務與學術、讓Fan Laws直觀理解: 在風扇幾何尺寸與葉片設計固定的情況下，風扇所能提供的流量與壓力能力具有其物理尺度；在轉速與空氣密度固定時，其 PQ Curve 也會受到限制，因此風扇存在一個最大壓差與最大流量的性能邊界。Fan Laws 描述的不是「風扇有多少 CFM」，而是風扇的幾何尺寸、轉速與空氣密度如何共同決定其可提供的流量、壓力與功率尺度；而 PQ Curve 則把這些能力具體呈現在風扇的性能邊界上。Fan Laws 協助工程應用端在不同風扇可以知道PQ的變化、進而跟系統阻抗做疊圖。

### Fan Performance 風扇性能 

風扇提供壓力差的能力，能夠給予系統流量。風扇與另一個不同的尺寸或規格的風扇、也會有不同的轉速以及電流需求--功率。風扇本體的流量Q，其公式 Q = A * V ，在固定截面積下的流體流速。這個是第一個要記下的事。接下來是風扇能夠建立的壓差的能力、也就是 P ，可以連結到博努力定律: 流動中的流體全壓等於 流體本身靜壓 + 流體額外得到得機械能而有的動壓。這是第二個。





***





***
# 筆記一下
###### Fan Laws & Fan Performance Explained

[https://fluidflowinfo.com/fan-performance-and-fan-laws/]

Fan Laws 是描述一個定律或是規則，用來預測固定系統內的風扇性能。









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
