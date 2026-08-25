### 前言

我們知道了Fan PQ 以及System impednace 的意義，當然會想要知道如何使用這兩個神奇的圖表讓獨舞變成雙人華爾滋!
接下來便是一步步整合這兩個圖表以及最後得到working point: 為什麼兩條曲線的交點，物理上會成為系統唯一的穩態工作狀態？

### Static Pressure And Total Pressure

Static Pressure And Total Pressure
我們在Fan PQ Curve 圖表裡面描述 P是一個代表靜壓的參數，在固定轉速下風扇因為當下條件，靜壓與流量的關係。在此時所謂"最大靜壓"是因為風扇被完全封閉的
擋板或阻抗等等，導致風扇為了推動空氣產生靜壓、在風扇出口的地方為此刻為最大靜壓。也就是流體微元們堆積最多的時刻。

在System Impedance Curve 圖表描述的 P 代表著壓力損失，在固定系統硬體配置及條件下，風通過系統所產生的流量與壓力損失的對應關係。這條曲線可以近似二次曲線來說明，ΔPsystem ≈ Ksystem * Q²。當壓力損失越多、需要更多的流量克服。
- 在系統阻抗裡面，沒有特別說到壓力損失是指損失了靜壓，或是動壓，或是?
- 或是我們理解的壓力、方向是錯誤的?
- 兩條曲線的「壓力定義、測量截面與測試條件」必須具有可比性
那就變成，風扇給的靜壓是不是系統的壓力損失?要研究以及推論

PQ Curve 的繪製：固定風扇轉速，透過調整風洞出口的開度（改變系統阻抗），在 Measurement Plane 上同時記錄「風量 $Q$」與「靜壓 $P_s$」，將這些點連成曲線。

System Impedance Curve 的計算：將實際系統（如伺服器機殼）放入測試，在系統前後的 Measurement Plane 上量測系統阻抗引起的壓力損失（Pressure Drop, $\Delta P$），驗證公式 $\Delta P = K \cdot Q^2$ 中的阻抗係數 $K$。

### Measurement Plane（測量平面）

Measurement Plane（測量平面）
在風扇與系統阻抗測試（如 AMCA 210 或 ISO 5801 標準風洞測試）中，Measurement Plane（測量平面） 是指在測試風洞或管道系統中，專門指定用來架設傳感器並量測流體狀態（靜壓、動壓、風速）的特定截面。

流體在通過風扇、轉彎、縮管或障礙物時，流場是非常混亂且不均勻的（湍流與渦流）。如果隨意找一個位置量測壓力，量出來的數值會劇烈跳動且毫無參考價值。
指定 Measurement Plane 的主要目的如下：
- 確保流場穩定：測量平面通常設置在流場經過整流（Flow Straightener）後、流動相對平穩的直管段上。
- 定義系統邊界：它是計算風扇靜壓（Static Pressure, $P_s$） 與 全壓（Total Pressure, $P_t$） 的基準點。
- 標準化數據：讓不同廠商、不同實驗室量測出來的 PQ Curve 與 System Impedance Curve 具備統一的比較基準。
Measurement Plane 的實際位置與配置在標準的風量測試風洞（Wind Tunnel / Airflow Test Chamber）中，通常會有兩個關鍵的測量平面：
```
[風扇 / 待測物] ----> [整流段/靜壓箱] ----> [Measurement Plane 1] ----> [噴嘴 Nozzle] ----> [Measurement Plane 2]
```
1. 靜壓測量平面（Upstream/Plenum Measurement Plane）位置：位於風扇出風口（或進風口）後方的靜壓箱（Plenum Chamber）內，或是距離風扇一定倍數管徑的直管上。作用：量測風扇在該風量下所建立的 靜壓差（P_s）。量測方式：在此平面的管壁四周均勻開設 4 個靜壓孔（Static Pressure Taps），並將其連通（Ring Manifold）取平均值，以消除局部流動不均的誤差。

2. 風量測量平面（Nozzle Measurement Plane）位置：位於風洞內部校準過的噴嘴（Nozzle）前後兩側。作用：量測氣流通過噴嘴前後的壓差（$\Delta P_{nozzle}$），再透過伯努利定律計算出當前的 體積風量（Airflow Rate, $Q$）。
