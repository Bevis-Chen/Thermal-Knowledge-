### 前言

我們知道了Fan PQ 以及System impednace 的意義，進一步會想知道使用這兩個神奇的圖表讓實務上的應用。接下來便是一步步整合這兩個圖表以及最後得到working point: 為什麼兩條曲線的交點，物理上會成為系統唯一的穩態工作狀態。

### Static Pressure And Total Pressure

**PQ Curve 的繪製**：固定風扇轉速，透過調整風洞出口的開度（改變系統阻抗），在 Measurement Plane 上同時記錄「風量 Q」與「靜壓 Ps」，將這些點連成曲線。
>我們在Fan PQ Curve 圖表裡面描述P是一個代表靜壓的參數，在固定轉速下風扇因為當下條件，靜壓與流量的關係。在此時所謂"最大靜壓"是因為風扇被完全封閉的擋板或阻抗等等，導致風扇為了推動空氣產生靜壓、在風扇出口的地方為此刻為最大靜壓。流量逐漸降低時，風扇對流體建立的壓力升高；當流量趨近於零時，對應到風扇的 shutoff condition，此時可得到其性能曲線上的最大壓力。

**System Impedance Curve 的計算**：將實際系統（如伺服器機殼）放入測試，在系統前後的 Measurement Plane 上量測系統阻抗引起的壓力損失（Pressure Drop, ΔP），驗證公式 ΔP = K * Q² 中的阻抗係數 K。
>在System Impedance Curve 圖表描述的 P 代表著壓力損失，在固定系統硬體配置及條件下，風通過系統所產生的流量與壓力損失的對應關係。這條曲線可以近似二次曲線來說明，ΔPsystem ≈ Ksystem * Q²，流量增加時，系統內部的摩擦與局部阻力通常會增加，因此維持該流量所需克服的壓力損失也會增加。

從PQ Curve的說明我們知道P 是代表靜壓、也就是產生壓差的能力; System Impedance Curve的P則是指壓力損失，代表系統內部的摩擦與局部阻力等等。System Impedance Curve所獲得的流量也是風扇提供的靜壓




Fan PQ Curve 與 System Impedance Curve 並不是只要單位同樣是 Pa，就可以直接疊圖比較。必須先確認 Fan PQ 的壓力定義、System Pressure Loss 的定義、Flow Rate 的定義、Measurement Plane，以及 Fan arrangement 與實際系統配置是否相容。當這些條件成立後，兩者才可以在同一個 Pressure–Flow framework 下比較，並透過兩條曲線的交會找出 Working Point。當然，若系統只有單顆風扇、且Pressure reference plane / Fan PQ / System Impedance 等等條件可對應跟滿足，那麼此時Fan PQ 以及 System Impedance兩條曲線可以放在同一個pressure-flow chart做比較。拿來與 System Curve 比較的，必須是「整個 fan arrangement 對系統所提供的 pressure-flow characteristic」。Fan Laws、Fan arrangement、Series / Parallel Fan，之後都會影響 Working Point。

到這裡會有疑問: 「既然 Fan PQ Curve 可能使用 Static Pressure，而 System Curve 描述的是 Pressure Loss，兩者到底憑什麼能放在同一張圖？」

##### Measurement Plane（測量平面）

Measurement Plane 是測試系統中被明確定義的測量截面，用來規定壓力、速度或流量等物理量「在哪裡、以什麼方式」被量測，使不同測試條件下取得的數據具有一致的參考基準。
在風扇與系統阻抗測試（如 AMCA 210 或 ISO 5801 標準風洞測試）中，Measurement Plane（測量平面） 是指在測試風洞或管道系統中，專門指定用來架設傳感器並量測流體狀態（靜壓、動壓、風速）的特定截面。

Measurement Plane 的位置會影響壓力定義，因此 Fan PQ 與 System Impedance 能否直接比較，不只是看單位都是 Pa，而要確認兩者的測量位置與 pressure definition 是否相容。


流體在通過風扇、轉彎、縮管或障礙物時，流場是非常混亂且不均勻的（湍流與渦流）。如果隨意找一個位置量測壓力，量出來的數值會劇烈跳動且毫無參考價值。
指定 Measurement Plane 的主要目的如下：
- 確保流場穩定：測量平面通常設置在流場經過整流（Flow Straightener）後、流動相對平穩的直管段上。
- 定義系統邊界：它是計算風扇靜壓（Static Pressure, Ps） 與 全壓（Total Pressure, Pt） 的基準點。
- 標準化數據：讓不同廠商、不同實驗室量測出來的 PQ Curve 與 System Impedance Curve 具備統一的比較基準。
Measurement Plane 的實際位置與配置在標準的風量測試風洞（Wind Tunnel / Airflow Test Chamber）中，通常會有兩個關鍵的測量平面：


### 工作點



***
參考資料
1. https://www.activa.com.tw/cn_tech_Test_System_Fan_Performance.html




