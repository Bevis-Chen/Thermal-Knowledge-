# Working Point

### 目錄

- 前言
- 靜壓 (Static Pressure) 與 全壓 (Total Pressure)
- PQ 曲線與系統阻抗曲線
- 測量面 (Measurement Plane) 與邊界條件
- 工作點（Working Point）
- 範例：解析交點的簡單數學示範
- 實務建議與注意事項
- 參考資料與延伸閱讀

***

### 前言

我們知道了**Fan PQ**以及**System Impedance**的意義，進一步學習如何整合跟使用這兩個圖表。接下來的文章將一步步說明這兩個圖表的關係以及得到一個總結: 
> 在一般穩定且單調的 Fan–System characteristic 下，兩條曲線的交點會對應系統的穩態工作狀態、也就是 Working Point。

這個交點不是單純的數學巧合，而是代表在該流量下、風扇所提供之壓力增量與系統所需要克服之壓力損失達到平衡。

### 靜壓 (Static Pressure) 與 全壓 (Total Pressure)

在流體力學裡面，需要區分什麼是**Statis Pressure (靜壓)** 與 **Velocity Pressure (動壓 / 速度壓)**。定義上、對於**低速、可視為不可壓縮的流體**，可使用工程上常見的近似。若流體具有顯著可壓縮性，Total Pressure 的定義與能量關係需要使用相應的可壓縮模型，而不能直接套用上述簡化式。

P_t ≈ P_s + P_v
其中：
P_v = ρ*V²/2

- **P_s**：Static Pressure，靜壓
- **P_v**：Velocity Pressure，速度壓
- **P_t**：Total Pressure，全壓
- **ρ**：流體密度
- **V**：特徵流速

本文採用低速、不可壓縮流體的工程近似。
若流動具有顯著可壓縮性，Total Pressure 的定義與能量關係需要使用相應的可壓縮流模型，而不能直接套用上述簡化式。
***

##### PQ Curve 的繪製

在固定風扇轉速下，透過改變測試裝置的流動條件，使風量 Q 發生變化，並量測相應的壓力與流量，便可以得到風扇的 **Pressure-Flow characteristic，也就是 PQ Curve**。實際測試方法會依照風扇尺寸以及測試標準而不同。
> 在Fan PQ Curve 圖表裡面 P(縱軸) 的定義是 **Fan Static Pressure**，則 **PQ Curve 描述的是在某一固定轉速下，風扇在不同流量下所能建立的靜壓差**

在固定轉速下風扇因為當下條件，靜壓與流量的關係。風扇的出口逐漸受到限制、出口變小，使得流量下降。理想極限情況下當風扇出口受到完全阻塞時，系統流量趨近於零、此狀態對應於 shutoff condition。此時風扇之扇葉仍旋轉、持續對流體做功，建立壓力差的能力升高，形成性能曲線上的高壓、低流量端點。但:
> **Shutoff Condition 並不代表風扇"沒有對流體做功"**

風量Q 接近零，風扇內部仍可能存在複雜的循環流、旋轉流與損失，而且實際風扇的 Shutoff 狀態可能伴隨顯著的非穩態流動。因此，實際性能曲線的端點仍應依風扇製造廠商與測試標準的定義解讀。

**System Impedance Curve 的計算**：將實際系統（伺服器整機）放入測試，在系統前後的 Measurement Plane 上量測系統阻抗引起的壓力損失（Pressure Drop, ΔP），驗證公式 ΔP = K * Q² 中的阻抗係數 K。
> 在System Impedance Curve 圖表描述的 P 代表著壓力損失，在固定系統硬體配置及條件下，風通過系統所產生的流量與壓力損失的對應關係。在許多伺服器風道元件與管路系統中，壓力損失可近似與速度平方成正比，因此在幾何與流動條件固定時，常可將系統壓力損失近似表示為 ΔP_system ≈ (K_system) * Q²。

在本文採用的 Fan PQ 表示方式中，若縱軸定義為 Fan Static Pressure，則該曲線描述的是風扇在不同流量下所能建立的靜壓差。System Impedance Curve的P 則是指壓力損失，代表系統內部的摩擦與局部阻力等等。**System Impedance Curve 本身並不描述風扇提供多少能量，而是描述在特定系統配置下，維持不同流量所需要克服的壓力損失。** 

當風扇安裝於系統中並開始運轉時，風扇對流體做功，使流體**多了**壓力與速度相關的機械能；流體通過 Filter、Heatsink、Duct 等元件後，因摩擦與局部流動損失而消耗**部分機械能**。在適當的測試邊界與假設下，可以用：ΔP_fan ≈ ΔP_system，也就是描述前面所說的產生機械能與損耗機械能達成近似平衡。

| 曲線 | 描述 |
|---|---|
| **Fan PQ Curve** | 在某個流量下，Fan能提供多少壓力 |
| **System Impedance Curve** | 在某個流量下，System需要克服多少壓力損失 |
| **Working Point** | Fan 提供與 System 需求達到平衡的狀態 |

Fan PQ Curve 與 System Impedance Curve 雖然正是分析 Working Point 的兩個核心，但並非只要兩者的壓力單位同樣為 Pa，就能直接疊圖比較。必須確認兩者的壓力定義、流量定義、測量參考位置、測試條件，以及 Fan arrangement 與實際系統配置是否相容。

##### 邊界條件

Fan PQ Curve 與 System Impedance Curve 並不是只要單位同樣是 Pa，就可以直接疊圖比較。必須先確認 Fan PQ 的壓力定義、System Pressure Loss 的定義、Flow Rate 的定義、Measurement Plane，以及 Fan arrangement 與實際系統配置是否相容。當這些條件成立後，兩者才可以在同一個 Pressure–Flow framework 下比較，並透過兩條曲線的交會找出 Working Point。當然，若系統只有單顆風扇、且Pressure reference plane / Fan PQ / System Impedance 等等條件可對應跟滿足，那麼此時Fan PQ 以及 System Impedance 兩條曲線可以放在同一個pressure-flow chart做比較。拿來與 System Curve 比較的，必須是「整個 fan arrangement 對系統所提供的 pressure-flow characteristic」。Fan Laws、Fan arrangement、Series / Parallel Fan，之後都會影響 Working Point。到這裡會有疑問: 「既然 Fan PQ Curve 可能使用 Static Pressure，而 System Curve 描述的是 Pressure Loss，兩者到底憑什麼能放在同一張圖？」

Measurement Plane 是測試系統中被明確定義的測量截面，用來規定壓力、速度或流量等物理量「在哪裡、以什麼方式」被量測，使不同測試條件下取得的數據具有一致的參考基準。在風扇與系統阻抗測試（如 AMCA 210 或 ISO 5801 標準風洞測試）中，Measurement Plane（測量平面） 是指在測試風洞或管道系統中，專門指定用來架設傳感器並量測流體狀態（靜壓、動壓、風速）的特定截面。Measurement Plane 的位置會影響壓力定義，因此 Fan PQ 與 System Impedance 能否直接比較，不只是看單位都是 Pa，而要確認兩者的測量位置與 pressure definition 是否相容。流體在通過風扇、轉彎、縮管或障礙物時，流場是非常混亂且不均勻的（湍流與渦流）。量測結果可能受到局部速度分布、渦流與壓力梯度影響，降低量測的穩定性、代表性與可重現性。指定 Measurement Plane 的主要目的如下：

- 提高量測的穩定性與可重現性：測量平面通常設置在流場經過整流（Flow Straightener）後、流動相對平穩的直管段上。
- 定義量測參考位置與測試截面：明確定義量測位置與參考截面，使不同位置所量得的壓力與速度能夠按照測試方法進行比較或換算。
- 標準化數據：讓不同廠商、不同實驗室量測出來的 PQ Curve 與 System Impedance Curve 具備統一的比較基準。

### 工作點

當伺服器與風扇運轉，達到穩定狀態，整機風扇提供的壓差P1以及系統損失P2達到相等。也就是
```
ΔP_fan(Q_WP) = ΔP_system(Q_WP)
Q_fan = Q_system = Q_WP
```
Fan PQ Curve 與 System Impedance Curve 的交點，就是在相同 Flow Rate 下，Fan 所能提供的壓力與 System 所需克服的壓力損失達到平衡的位置。可以發現此時的PQ曲線以及系統阻抗曲線放在一起，在穩態條件下: 風扇對流體提供機械能，而系統中的流動阻力造成機械能的耗散。其實是兩件事。因此系統的平均流量不再隨時間持續變化。Working Point 並不是風扇或系統單獨決定的性能，而是 Fan 與 System 的 Pressure–Flow characteristics 互相匹配後所形成的實際運作狀態。

## 範例：簡單數學示範

假設以靜壓 Ps（單位 Pa）與流量 Q（單位 m³/s）表示，並用簡單二次模型逼近：
風扇靜壓（近似）：P_fan(Q) = P0 - k_f * Q² ，系統壓力損失（近似）：ΔP_system(Q) = k_s * Q²，工作點滿足： P0 - k_f * Q² = k_s * Q²，

→ P0 = (k_f + k_s) Q²
→ Q_WP = √( P0 / (k_f + k_s) )

範例數值（僅示範）：假設 Fan PQ Curve 可由簡化二次模型表示， P0 為 Q = 0 時的模型壓力。

P0 = 250 Pa（無流時的靜壓），k_f = 4000 (Pa·s²/m^6)（風扇模型係數），k_s = 6000 (Pa·s²/m^6)（系統阻抗係數），則 Q_working = √(250 / (4000 + 6000)) = √(250 / 10000) ≈ 0.158 m³/s（換算約 568 m³/h，334 CFM）

注意：以上係簡化模型。實務中曲線不是精確二次函數，需以實測數據擬合或直接繪圖找交點。且單位與密度需保持一致。

## 實務建議與注意事項

- 確認壓力定義：必須明確區分 Fan Static Pressure、Fan Total Pressure 與 System Pressure Loss。若資料來源的壓力定義不同，不能僅依據單位 Pa 直接比較，需確認參考截面與測試定義後，再進行適當的換算或重新量測。
- 標註測試條件：轉速、溫度、氣壓、測量面位置、流量單位、是否有分流/回路等。
- 測量裝置：使用靜壓孔靶、皮托管（測動壓）、熱式流量計或節流裝置時，注意儀器誤差與校正。
- 風扇定律（Fan Laws）：在不同轉速下，Q ∝ N，P ∝ N²，功率 ∝ N^3（近似），可用於不同轉速間的曲線換算（在相似條件下）。
- 系統變動：系統更改（加濾網、線路改動、散熱器堵塞）會改變系統曲線與工作點。
- 多風扇情形：多風扇的串聯或並聯會改變整體 Fan Assembly 的 Pressure–Flow characteristic，進而改變其與 System Impedance Curve 的交點。
- 安全邊際：在設計時，考慮風扇老化、灰塵堆積、環境變化帶來的流量/壓力衰減。

## 參考資料與延伸閱讀

- **ANSI/AMCA Standard 210-25 / ASHRAE 51-25**, *Laboratory Methods of Testing Fans for Certified Aerodynamic Performance Rating*. AMCA 官方資料指出，此標準用於以一致的實驗室方法取得風扇的 airflow rate、pressure developed、power、air density、speed 與 efficiency 等性能資料。
- **ISO 5801:2017**, *Fans — Performance testing using standardized airways*. ISO 官方資料顯示該版本於 2023 年確認仍為現行版本，並於 2025 年發布 Amendment 1。
- **ANSI/AMCA Standard 270-23**, *Laboratory Methods of Aerodynamic Testing Fan Arrays for Rating*. 用於 Fan Array 的氣動性能測試。
- **ISO/TR 16219:2024**, *Fans — System effects and system effect factors*. 討論標準化測試與實際系統安裝條件之間的 System Effect。
- ASHRAE Handbook、AMCA fan-system literature，以及相關 Fluid Mechanics / Internal Flow 教科書。

***
恐怕要一陣子之後，驀然回首、看看自己寫得文章，別有一番稚氣，一些風味，還有漏洞百出以及年少輕狂。


