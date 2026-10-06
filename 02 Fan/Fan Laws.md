# Fan Laws

## 目錄

- 前言
- Fan Performance 風扇性能
  - Flow Rate
  - Pressure
  - Power
- Fan PQ Curve
- 為什麼需要 Fan Laws？
  - Fan Laws
  - Speed
  - Fan Diameter
  - Air Density
- Fan Laws 的推導與物理意義
  - Similarity Conditions
  - Geometric Similarity
  - Reynolds Number
- Mach Number
- Fan Laws 與 PQ Curve
- Fan Laws 與 System Impedance
- Fan Laws 與 Working Point
- Server Fan 的實務應用
- 適用限制與注意事項

### 前言 

伺服器系統裡面常常有風扇的存在，不同的風扇尺寸、或是不同的廠商提供的風扇都會是工程師驗證測試時考慮的因素。本文除了解釋Fan Laws之外，也會盡作者的能力去結合實務與學術、讓Fan Laws直觀理解: 在風扇幾何尺寸與葉片設計固定的情況下，風扇所能提供的流量與壓力能力具有其物理尺度；在風扇轉速、風扇配置與流體密度固定時，風扇可以根據此條件描述壓力-流量的對應性能範圍，也就是PQ Curve、表示風扇在固定條件下的流量與壓力之間的關係。Fan Laws 描述的不是「風扇有多少 CFM」，而是風扇的幾何尺寸、轉速與空氣密度如何共同決定其可提供的流量、壓力與功率尺度；而 PQ Curve 則把這些能力具體呈現在風扇的性能邊界上。在滿足適當相似條件下，Fan Laws 可以用來描述風扇轉速、幾何尺寸與流體密度改變時，流量、壓力與功率的尺度變化，並可進一步將轉換後的風扇性能與系統阻抗曲線結合，以分析新的 Working Point。
應用面上，Fan laws可以幫助工程師或風扇的使用者在不同轉速變化，PQ 曲線會怎麼變化。PQ曲線的變化也影響在適當條件下跟系統阻抗疊圖的Working-Pint位置，不過要注意Fan laws的使用有著條件的限制，並不是可以任意使用。

### Fan PQ Curve

風扇的 PQ Curve 大多來自單體風扇架設在風洞上，且固定轉速下測量出靜壓從最大到最小時，風扇能夠吹出的對應的流量數值。PQ Curve 可以幫助工程師在適當條件下透過與系統阻抗的曲線疊圖找出適合系統的流量，但如果風扇因為外在需求而需要改變轉速、或是調整流量呢？

### 為什麼需要 Fan Laws？

Fan Laws不是萬靈丹，可以解決所有跟風扇有關的議題。風扇相似定律描述著在適當條件下，可以透過轉速、流量、功耗之間的比例關係來推估風扇性能。風扇性能會是PQ Curve以及進一步找出適合的工作點。
  - Speed： 風扇轉速與流量、壓力以及電功率有著各自的互動關係，若轉速改變則在相似條件下、Fan laws可以用來推估流量、壓力以及電功率的縮放比例。
（還要確認： 風扇轉速是由轉子功率決定，也就是有多少電力可以轉多少速度。不過在理想情況下（風扇在stall area以及失速區以外，還有克服系統阻抗）風扇轉的變化流量也會隨之影響，不過這時現實使用者或是有外在條件影響讓轉速需要更高或低，就可以透過Fan Laws推估。）
   - Fan Diameter ： 風扇的外框尺寸在工程實務上可能因為限制區域改變而需要改變風扇的外框尺寸，這時候需要Fan laws來協助判斷外框與流量的變化。
   - Air density ： 環境的不同，比如高海拔地區的空氣密度相較低海拔來的小，風扇的能夠產生的空氣流量也變少。

### Fan Laws 的推導與物理意義

- Similarity Condition： 風扇的相似條件判斷影響著下一步推導。風扇的互相放大或縮小的部分在於外框尺寸、風扇轉速、還有空氣的密度。並不是簡單的風扇外框剛好1：2，那麼兩者的性能表現就是1：2；同樣的是風扇轉速甚至其他。以下會簡述兩個判斷風扇是否相似的特徵。
- Geometry Similarty: 幾何相似。風扇的尺寸。還有風扇扇葉、馬達、轉子等等幾何。
- Reynolds Number: 雷諾數是描述慣性效應與黏性效應相對重要程度的無因次參數，與流體密度、流體黏滯係數、管路長度、流體速度有關，流體當下的物理狀態與熱傳機制（是層流的黏滯傳導，還是湍流的強烈對流）。

### Mach Number 馬赫數

### Fan Laws 與 PQ Curve

可以作為在適當條件下，當得到一個風扇在固定轉速下的PQ，進而推估這個風扇其他轉速的PQ


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
