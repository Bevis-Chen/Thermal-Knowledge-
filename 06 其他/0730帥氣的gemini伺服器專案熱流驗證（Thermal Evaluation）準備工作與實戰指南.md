# 伺服器專案熱流驗證（Thermal Evaluation）準備工作與實戰指南

## 一、 Gerber out 之後的專案時程與熱流空窗期
Gerber out（出圖）至 Mock-up（樣機）測試中間通常有 2 到 3 週的空窗期，硬體需經歷：
1. PCB 製作（洗板子，約 7-14 天）
2. SMT 備料與打件組裝（完成後為 PCBA）
3. 機構件、散熱模組（Heatsink、風扇、導風罩）加工
4. 系統組裝（Assembly）與上電點亮（Bring-up）

---

## 二、 熱電偶貼線點位規劃（Sensor Profile Plan）
點位佈置邏輯：由風道上游至下游，緊抓高功耗與耐溫低的元件（通常使用 40-80 條 36 AWG 或更細的熱電偶）。

### 1. 環境控制基準
* **Inlet T/C**：機殼前方面板（Bezel）進風口（配置上、中、下、左、右以計算平均進風溫）。
* **Outlet T/C**：後方出風口（鎖定 Heatsink 後方與電源供應器 PSU 出風處）。

### 2. 高功耗與主核心元件
* **CPU / GPU**：量測 Tcase/Tjunction。CPU 可在散熱片底部剖溝貼線；SXM GPU 禁剖溝，以軟體 DTS（如 `nvidia-smi`）為主，硬體則貼在晶片四周基板（Substrate）邊緣。
* **Memory (DIMM)**：挑選風道末端（最熱）以及緊鄰 Heatsink 下游的記憶體，貼在正反面中心顆粒。
* **VRM (Mosfet / Choke)**：挑選風速最弱、功耗最高相位的 Mosfet 軀體表面。

### 3. 周邊與敏感元件
* **PCIe / OCP Card**：網卡/加速卡控制器晶片、光纖模組（Transceiver）。
* **Storage**：NVMe SSD 控制晶片、HDD 表面（最下游、風阻最大處）。
* **IC / 電容**：主機板晶片組（PCH）、靠近熱源的電解電容。

---

## 三、 多節點 Blade 伺服器的兩大測試階段與致命考驗

### 階段 1：散熱片與風道驗證（純硬體極限測試）
* **做法**：風扇強制鎖定 100% PWM（Manual Mode），跑壓力軟體（如 Stress_ng/PTU）拉滿功耗，計算極限熱阻 $R_{ca}$。
* **Blade 考驗**：
  * **熱尾流（Thermal Shadowing）**：前方節點熱風直吹後方節點，需所有節點「同時滿載」驗證。
  * **風量分配（Flow Distribution）**：多節點共用後方風扇牆（Fan Wall），需檢查各層 Sled 是否均勻分到風量。
  * **跨節點熱串流（Thermal Cross-talk）**：即使有金屬隔板，熱量仍會透過結構熱傳導/輻射，以及風扇牆搶風產生的文氏效應（風道真空/迴流）互相干擾。

### 階段 2：系統自動風扇控制曲線（Fan Table / Thermal Policy 驗證）
* **做法**：開啟自動模式（Smart Fan），系統功耗從 Idle 漸進式上升至 100%，驗證風扇演算法（Step / Ramp）與遲滯現象（Hysteresis）。
* **Blade 考驗**：
  * **共享風扇控制（Shared Fan Control）**：當單一節點滿載、其餘閒置時，需驗證「就高不就低」的風扇 Policy，避免閒置節點過冷或浪費能耗。
  * **通訊與讀取（Sensor Reading）**：驗證個別節點溫度訊號能否透過中介板（Midplane）即時、無延遲地傳給主機箱 BMC。

---

## 四、 打樣空窗期必備測試治具與風扇指令

### 1. 治具與材料準備
* **Dummy Card / Dummy DIMM**：模擬真實系統風阻與發熱量。
* **Fujifilm 壓力感測貼紙**：準備超低壓（LLLW）或低壓（LL）規格，夾在晶片與散熱片間，檢查散熱片底座平面度與扣具壓力量測。
* **散熱膏壓痕測試（TIM Impression Test）**：實機到手鎖緊後拆卸，觀察散熱膏厚度（BLT），抓出散熱片翹曲（Warpage）或鑊底效應。
* **消耗品**：高溫膠帶（Kapton）、專用快乾（454 快乾與藍色催化劑）。

### 2. BMC 風扇控制指令（IPMI Command）
* **切換手動模式（Manual Mode）**：
  `ipmitool raw 0x30 0x30 0x01 0x00`
* **設定全速（100% PWM / 0x64）**：
  `ipmitool raw 0x30 0x30 0x02 0xff 0x64`
* **自動化腳本**：建議使用 Python/Shell 將「拉載 -> 記錄溫度 -> 切換轉速 -> 等待熱平衡 -> 擷取數據」流程自動化。
