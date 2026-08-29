### 前言

我們知道了Fan PQ 以及System impednace 的意義，進一步會想知道使用這兩個神奇的圖表讓實務上的應用。接下來便是一步步整合這兩個圖表以及最後得到working point: 為什麼兩條曲線的交點，物理上會成為系統唯一的穩態工作狀態。

### Static Pressure And Total Pressure

我們在Fan PQ Curve 圖表裡面描述P是一個代表靜壓的參數，在固定轉速下風扇因為當下條件，靜壓與流量的關係。在此時所謂"最大靜壓"是因為風扇被完全封閉的擋板或阻抗等等，導致風扇為了推動空氣產生靜壓、在風扇出口的地方為此刻為最大靜壓。流量逐漸降低時，風扇對流體建立的壓力升高；當流量趨近於零時，對應到風扇的 shutoff condition，此時可得到其性能曲線上的最大壓力。

在System Impedance Curve 圖表描述的 P 代表著壓力損失，在固定系統硬體配置及條件下，風通過系統所產生的流量與壓力損失的對應關係。這條曲線可以近似二次曲線來說明，ΔPsystem ≈ Ksystem * Q²，流量增加時，系統內部的摩擦與局部阻力通常會增加，因此維持該流量所需克服的壓力損失也會增加。大多數的伺服器不僅僅擁有一顆風扇，我們也無法僅透過系統一顆風扇的單體PQ Curve以及整機系統的System Impedance Curve放在同一個Flow-Pressure圖表，然後說兩條曲線交會就是工作點。當然，若系統只有單顆風扇、且Pressure reference plane / Fan PQ / System Impedance 等等條件可對應跟滿足，那麼此時Fan PQ 以及 System Impedance兩條曲線可以放在同一個pressure-flow chart做比較。拿來與 System Curve 比較的，必須是「整個 fan arrangement 對系統所提供的 pressure-flow characteristic」。

PQ Curve 的繪製：固定風扇轉速，透過調整風洞出口的開度（改變系統阻抗），在 Measurement Plane 上同時記錄「風量 Q」與「靜壓 Ps」，將這些點連成曲線。
System Impedance Curve 的計算：將實際系統（如伺服器機殼）放入測試，在系統前後的 Measurement Plane 上量測系統阻抗引起的壓力損失（Pressure Drop, ΔP），驗證公式 ΔP = K * Q² 中的阻抗係數 K。

到這裡會有疑問: 「既然 Fan PQ Curve 可能使用 Static Pressure，而 System Curve 描述的是 Pressure Loss，兩者到底憑什麼能放在同一張圖？」

### Measurement Plane（測量平面）

在風扇與系統阻抗測試（如 AMCA 210 或 ISO 5801 標準風洞測試）中，Measurement Plane（測量平面） 是指在測試風洞或管道系統中，專門指定用來架設傳感器並量測流體狀態（靜壓、動壓、風速）的特定截面。

流體在通過風扇、轉彎、縮管或障礙物時，流場是非常混亂且不均勻的（湍流與渦流）。如果隨意找一個位置量測壓力，量出來的數值會劇烈跳動且毫無參考價值。
指定 Measurement Plane 的主要目的如下：
- 確保流場穩定：測量平面通常設置在流場經過整流（Flow Straightener）後、流動相對平穩的直管段上。
- 定義系統邊界：它是計算風扇靜壓（Static Pressure, Ps） 與 全壓（Total Pressure, Pt） 的基準點。
- 標準化數據：讓不同廠商、不同實驗室量測出來的 PQ Curve 與 System Impedance Curve 具備統一的比較基準。
Measurement Plane 的實際位置與配置在標準的風量測試風洞（Wind Tunnel / Airflow Test Chamber）中，通常會有兩個關鍵的測量平面：
**以下為概念示意，實際測試配置依測試標準與 apparatus arrangement 而異。**
```
[風扇 / 待測物] ----> [整流段/靜壓箱] ----> [Measurement Plane 1] ----> [噴嘴 Nozzle] ----> [Measurement Plane 2]
```

1. 靜壓測量平面（Upstream/Plenum Measurement Plane）位置：位於風扇出風口（或進風口）後方的靜壓箱（Plenum Chamber）內，或是距離風扇一定倍數管徑的直管上。作用：量測風扇在該風量下所建立的 靜壓差（ΔP_s）。量測方式：在此平面的管壁四周均勻開設 4 個靜壓孔（Static Pressure Taps），並將其連通（Ring Manifold）取平均值，以消除局部流動不均的誤差。

2. 風量測量平面（Nozzle Measurement Plane）位置：位於風洞內部校準過的噴嘴（Nozzle）前後兩側。作用：量測氣流通過噴嘴前後的壓差（ΔPnozzle），再透過伯努利定律計算出當前的 體積風量（Airflow Rate, Q）。

### 工作點



***
參考資料
1. https://www.activa.com.tw/cn_tech_Test_System_Fan_Performance.html




