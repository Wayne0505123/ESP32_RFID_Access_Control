# Arduino RFID 智慧門鎖系統

本專案為一套基於 **ESP32 + Arduino Framework** 開發的 RFID 智慧門鎖系統，整合 **RFID 身分驗證、OLED 顯示回饋與伺服馬達控制**，用以模擬實際應用於智慧門禁與物聯網裝置的嵌入式系統。

本專案展示了**韌體開發能力、感測器整合、通訊協定應用與即時控制設計**。

---

## 專案簡介

本系統透過 **MFRC522 RFID 模組** 讀取卡片 UID，並與系統內建的 **白名單資料進行比對**。  
若為授權卡片，系統將控制 **伺服馬達旋轉模擬門鎖開啟**，並透過 **OLED 顯示成功訊息**；  
若為未授權卡片，則顯示失敗訊息並拒絕存取。

此系統可應用於：

- 智慧家庭門禁系統  
- 辦公室門禁控制裝置  
- IoT 身分驗證設備  
- 嵌入式自動化控制專案  

---

## 系統功能

- RFID 卡片 UID 身分驗證  
- 白名單存取控制機制  
- 伺服馬達門鎖開關控制  
- OLED 即時狀態顯示  
- 未授權卡片存取拒絕  
- Serial Monitor 除錯資訊輸出  
- 模組化韌體設計  

---

## 硬體設備

- ESP32 開發板  
- MFRC522 RFID 讀卡模組  
- Servo 伺服馬達  
- Seeed Studio OLED 顯示器（I2C）  
- RFID 卡片 / Tag  
- 麵包板與跳線  

---

## 腳位配置

| 裝置 | ESP32 腳位 |
|------|-----------|
| RFID SS (SDA) | GPIO 5 |
| RFID RST | GPIO 27 |
| RFID SCK | GPIO 18 |
| RFID MISO | GPIO 19 |
| RFID MOSI | GPIO 23 |
| OLED SDA | GPIO 21 |
| OLED SCL | GPIO 22 |
| Servo 訊號 | GPIO 16 |

---

## 系統運作流程

1. 系統初始化 RFID 模組、OLED 顯示器與 Servo 馬達  
2. OLED 顯示待機畫面 **PLEASE SCAN**  
3. 當偵測到 RFID 卡片時：
   - 讀取 UID 並輸出至 Serial Monitor  
   - 與白名單資料進行比對  
4. 若為授權卡片：
   - OLED 顯示 **SUCCESS / WELCOME**
   - Servo 旋轉至開鎖角度  
   - 延遲後自動回到上鎖位置  
5. 若為未授權卡片：
   - OLED 顯示 **FAILURE**
   - 拒絕開鎖  

---

## 軟體架構

### RFID 驗證模組
- SPI 通訊讀取 UID
- 白名單比對演算法

### 顯示控制模組
- 待機畫面函式
- 成功畫面函式
- 失敗畫面函式

### 執行元件控制模組
- Servo PWM 控制
- 門鎖開關邏輯

### 主控制流程
- 卡片事件觸發
- 狀態式系統回應設計

---

## Serial Monitor 範例輸出
```
UID: 85 D2 88 5E
Access Granted
```

```
UID: 11 22 33 44
Access Denied
```


---

## 技能

- 嵌入式系統設計  
- 韌體程式開發（Arduino / ESP32）  
- SPI / I2C 通訊整合  
- 感測器與致動器控制  
- 即時系統控制邏輯  
- IoT 原型系統開發  
- 硬體除錯與系統整合  
