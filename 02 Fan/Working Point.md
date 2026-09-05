### 目錄
- 前言
- 靜壓 (Static Pressure) 與 全壓 (Total Pressure)
- PQ 曲線與系統阻抗曲線
- 測量面 (Measurement Plane) 與邊界條件
- 工作點（Working Point）
- 範例：解析交點的簡單數學示範
- 實務建議與注意事項
- 參考資料與延伸閱讀
  
### 前言

我們知道了Fan PQ 以及System Impedance 的意義，進一步會使用這兩個圖表。接下來的文章將整合這兩個圖表以及最後得到結論: 為什麼兩條曲線的交點，會成為系統的穩態工作狀態。

### 靜壓 (Static Pressure) 與 全壓 (Total Pressure)

壓力是垂直作用於物體表面的力，在流體裡面:
靜壓 P_s（Static Pressure）是流體的壓力狀態；動壓 P_v（Velocity Pressure）則與流體速度所對應的動能項有關，可表示為 (½)ρ*v²。在低速、不可壓縮流體的簡化分析中，總壓 P_total 可表示為靜壓與動壓之和：P_total = P_s + (½)ρ*v²。

**PQ Curve 的繪製**：固定風扇轉速，透過調整風洞出口的開度（改變系統阻抗），在 Measurement Plane 上同時記錄「風量 Q」與「靜壓 P_s」，將這些點連成曲線。
> 我們在Fan PQ Curve 圖表裡面描述P是一個代表靜壓的參數，在固定轉速下風扇因為當下條件，靜壓與流量的關係。在此時所謂"最大靜壓"是因為風扇被完全封閉的擋板或阻抗等等，導致風扇為了推動空氣產生靜壓、在風扇出口的地方為此刻為最大靜壓。流量逐漸降低時，風扇對流體建立的壓力升高；當流量趨近於零時，對應到風扇的 shutoff condition，此時可得到其性能曲線上的最大壓力。

**System Impedance Curve 的計算**：將實際系統（伺服器整機）放入測試，在系統前後的 Measurement Plane 上量測系統阻抗引起的壓力損失（Pressure Drop, ΔP），驗證公式 ΔP = K * Q² 中的阻抗係數 K。
> 在System Impedance Curve 圖表描述的 P 代表著壓力損失，在固定系統硬體配置及條件下，風通過系統所產生的流量與壓力損失的對應關係。這條曲線可以近似二次曲線來說明，ΔP_system ≈ (K_system) * Q²，流量增加時，系統內部的摩擦與局部阻力通常會增加，因此維持該流量所需克服的壓力損失也會增加。

從PQ Curve的說明我們知道P 大部分是代表靜壓、也就是產生壓差的能力; System Impedance Curve的P 則是指壓力損失，代表系統內部的摩擦與局部阻力等等。System Impedance Curve 本身並不描述風扇提供多少能量，而是描述在特定系統配置下，維持不同流量所需要克服的壓力損失。當風扇安裝於系統中並開始運轉時，風扇對流體做功，使流體獲得壓力與速度相關的機械能；流體通過 Filter、Heatsink、Duct 等元件後，因摩擦與局部流動損失而消耗部分機械能。最終在穩態下，風扇提供的壓力增量與系統所需克服的壓力損失達到平衡，形成 Working Point。

| 曲線 | 描述 |
|---|---|
| **Fan PQ Curve** | 在某個流量下，Fan能提供多少壓力 |
| **System Impedance Curve** | 在某個流量下，System需要克服多少壓力損失 |
| **Working Point** | Fan 提供與 System 需求達到平衡的狀態 |

不過風扇PQ以及系統阻抗雖然有著密切關係，但仍不能直接說兩個可以放在一起討論，也必須確認這條 PQ curve 是 fan static pressure 還是 fan total pressure 、以及需要進一步規範跟預設條件。

##### 邊界條件

Fan PQ Curve 與 System Impedance Curve 並不是只要單位同樣是 Pa，就可以直接疊圖比較。必須先確認 Fan PQ 的壓力定義、System Pressure Loss 的定義、Flow Rate 的定義、Measurement Plane，以及 Fan arrangement 與實際系統配置是否相容。當這些條件成立後，兩者才可以在同一個 Pressure–Flow framework 下比較，並透過兩條曲線的交會找出 Working Point。當然，若系統只有單顆風扇、且Pressure reference plane / Fan PQ / System Impedance 等等條件可對應跟滿足，那麼此時Fan PQ 以及 System Impedance 兩條曲線可以放在同一個pressure-flow chart做比較。拿來與 System Curve 比較的，必須是「整個 fan arrangement 對系統所提供的 pressure-flow characteristic」。Fan Laws、Fan arrangement、Series / Parallel Fan，之後都會影響 Working Point。到這裡會有疑問: 「既然 Fan PQ Curve 可能使用 Static Pressure，而 System Curve 描述的是 Pressure Loss，兩者到底憑什麼能放在同一張圖？」

Measurement Plane 是測試系統中被明確定義的測量截面，用來規定壓力、速度或流量等物理量「在哪裡、以什麼方式」被量測，使不同測試條件下取得的數據具有一致的參考基準。在風扇與系統阻抗測試（如 AMCA 210 或 ISO 5801 標準風洞測試）中，Measurement Plane（測量平面） 是指在測試風洞或管道系統中，專門指定用來架設傳感器並量測流體狀態（靜壓、動壓、風速）的特定截面。Measurement Plane 的位置會影響壓力定義，因此 Fan PQ 與 System Impedance 能否直接比較，不只是看單位都是 Pa，而要確認兩者的測量位置與 pressure definition 是否相容。流體在通過風扇、轉彎、縮管或障礙物時，流場是非常混亂且不均勻的（湍流與渦流）。如果隨意找一個位置量測壓力，量出來的數值會劇烈跳動且毫無參考價值。指定 Measurement Plane 的主要目的如下：

- 提高量測的穩定性與可重現性：測量平面通常設置在流場經過整流（Flow Straightener）後、流動相對平穩的直管段上。
- 定義系統邊界：它是計算風扇靜壓（Static Pressure, Ps） 與 全壓（Total Pressure, Pt） 的基準點。
- 標準化數據：讓不同廠商、不同實驗室量測出來的 PQ Curve 與 System Impedance Curve 具備統一的比較基準。

### 工作點

當伺服器與風扇運轉，達到穩定狀態，整機風扇提供的壓差P1以及系統損失P2達到相等。也就是
```
ΔP_fan(Q_working-point) = ΔP_system(Q_working-point)
Q_fan = Q_system = Q_working-point
```
Fan PQ Curve 與 System Impedance Curve 的交點，就是在相同 Flow Rate 下，Fan 所能提供的壓力與 System 所需克服的壓力損失達到平衡的位置。

我可以發現此時的PQ曲線以及系統阻抗曲線放在一起，在該 Q 下，風扇能提供的壓力正好等於系統需要的壓力損失，因此沒有淨力推動流量變化，系統進入穩態。Working Point 並不是風扇或系統單獨決定的性能，而是 Fan 與 System 的 Pressure–Flow characteristics 互相匹配後所形成的實際運作狀態。

## 範例：簡單數學示範

假設以靜壓 Ps（單位 Pa）與流量 Q（單位 m³/s）表示，並用簡單二次模型逼近：
風扇靜壓（近似）：P_fan(Q) = P0 - k_f * Q² 
系統壓力損失（近似）：ΔP_system(Q) = k_s * Q²
工作點滿足： P0 - k_f * Q² = k_s * Q²
→ P0 = (k_f + k_s) Q²
→ Q_working = √( P0 / (k_f + k_s) )

範例數值（僅示範）：

P0 = 250 Pa（無流時的靜壓）
k_f = 400 (Pa·s²/m^6)（風扇模型係數）
k_s = 200 (Pa·s²/m^6)（系統阻抗係數）
則 Q_working = √(250 / (400 + 200)) = √(250 / 600) ≈ 0.646 m³/s
（換算約 2326 m³/h）

注意：以上係簡化模型。實務中曲線不是精確二次函數，需以實測數據擬合或直接繪圖找交點。且單位與密度需保持一致。

## 實務建議與注意事項

- 確認壓力定義：同時使用 Ps 或 Pt；若資料來源混用，必須先換算或重新量測。
- 標註測試條件：轉速、溫度、氣壓、測量面位置、流量單位、是否有分流/回路等。
- 測量裝置：使用靜壓孔靶、皮托管（測動壓）、熱式流量計或節流裝置時，注意儀器誤差與校正。
- 風扇定律（Fan Laws）：在不同轉速下，Q ∝ N，P ∝ N²，功率 ∝ N^3（近似），可用於不同轉速間的曲線換算（在相似條件下）。
- 系統變動：系統更改（加濾網、線路改動、散熱器堵塞）會改變系統曲線與工作點。
- 多風扇情形：風扇並聯/串聯會改變等效系統曲線與單機工作點，需用等效曲線或逐步模擬/測量。
- 安全邊際：在設計時，考慮風扇老化、灰塵堆積、環境變化帶來的流量/壓力衰減。

## 參考資料與延伸閱讀

- ASHRAE、AMCA 或風機製造商的 PQ 曲線與測試標準文件。
- 風扇定律（Fan Laws）與管網流體力學教材。
