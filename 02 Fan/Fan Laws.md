# Fan Laws

## 目錄


### 前言 

伺服器系統裡面常常有風扇的存在，不同的風扇尺寸、或是不同的廠商提供的風扇都會是工程師驗證測試時考慮的因素。本文除了解釋Fan Laws之外，也會盡作者的能力去結合實務與學術、讓Fan Laws直觀理解。

### 風扇尺寸






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
