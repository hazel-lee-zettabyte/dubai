# MaaS 使用者操作手冊 v1.24（繁體中文）

## 文件資訊

| 項目 | 內容 |
| --- | --- |
| 文件版本 | v1.24 |
| 發布日期 | 2026-06-30 |
| 適用產品版本 | MaaS v1.24 |
| 文件類型 | 使用者操作手冊 |
| 目標角色 | 開發者／一般使用者 |
| 語言 | 繁體中文 |

## 目錄

1. 產品概述
   - 1.1 產品定位
   - 1.2 核心價值
   - 1.3 目標使用者
   - 1.4 v1.24 功能範圍
2. 快速入門
   - 2.1 環境要求
   - 2.2 登入平台
   - 2.3 平台介面概覽
   - 2.4 典型使用流程
3. 功能詳解
   - 3.1 模型市場
   - 3.2 線上體驗（Playground）
   - 3.3 APIKey 管理
   - 3.4 用量
   - 3.5 預算提醒
   - 3.6 帳單查看
   - 3.7 帳戶設定
4. 操作指南
   - 4.1 場景一：開發者首次介接 MaaS 平台 API
   - 4.2 場景二：設定預算提醒與成本控制
   - 4.3 場景三：透過 Playground 線上調校模型參數
   - 4.4 場景四：多 APIKey 管理與用量監控
5. 常見問題（FAQ）
6. 附錄
   - 6.1 術語表
   - 6.2 錯誤碼說明
   - 6.3 速率限制層級參考
   - 6.4 API 呼叫程式碼範例

---

## 1. 產品概述

### 1.1 產品定位

ZettaByte MaaS Platform（Model as a Service，模型即服務）是 ZettaByte 融合平台的核心組成部分，為企業使用者提供統一的大型模型 API 閘道與模型服務化平台。平台整合了模型市場、多模型 API 呼叫、線上體驗、計量計費、速率限制、用量監控等能力，協助企業與開發者快速介接並使用大型模型服務，降低 AI 應用開發門檻，加速業務創新。

### 1.2 核心價值

- **統一模型市場**：匯集自部署模型與第三方通路模型（如 OpenAI、百煉、火山引擎等），一站式瀏覽、體驗與呼叫
- **開箱即用**：只需建立 APIKey 即可透過標準 API 呼叫各類大型模型，無需關心底層基礎設施
- **線上體驗**：內建 Playground 線上測試環境，支援串流對話、參數調節、費用估算、程式碼生成
- **精細計費**：支援輸入／輸出 Token 差異化定價，即時顯示費用消耗
- **多層級流量限制**：平台統一層級範本，APIKey 級速率限制，保障服務穩定性
- **成本可控**：預算提醒、用量頁面、帳單明細，全方位掌控費用支出
- **安全合規**：多因素驗證（MFA）、APIKey 安全保障

### 1.3 目標使用者

本手冊適用於以下角色：

| 角色 | 描述 | 典型使用場景 |
| --- | --- | --- |
| 開發者／一般使用者 | AI 應用開發人員或一般使用者 | 瀏覽模型市場、線上體驗模型效果、建立與使用 APIKey、在應用程式中整合模型 API、查看個人用量 |

> **說明：** 本手冊以一般使用者／開發者視角撰寫。租戶管理員相關的組織管理、團隊使用者管理等功能不在本手冊範圍內。

> **說明：** 一般使用者／開發者視角與租戶管理員大致相同，主要區別在於資料權限範圍：一般使用者／開發者只能查看與管理自己的 APIKey、用量、帳單及預算提醒，無法查看團隊其他成員的資料，也看不到「組織管理」選單。

### 1.4 v1.24 功能範圍

支援的功能模組：

| 功能模組 | 一般使用者／開發者 | 說明 |
| --- | :---: | --- |
| 模型市場 | ✓ | 瀏覽模型卡片、搜尋篩選排序、查看模型詳情 |
| 線上體驗（Playground） | ✓ | 選 APIKey、調參數、串流對話、費用估算、複製程式碼、匯出對話 |
| APIKey 管理 | ✓ | 建立／編輯／刪除，速率限制基於預設層級，可向下調整 |
| 用量 | ✓ | Token 消耗與 API 呼叫統計，依時間／模型／APIKey 篩選，匯出 CSV |
| 預算提醒 | ✓ | 建立提醒規則，設定預算與門檻值，設定通知管道 |
| 帳單查看 | ✓ | 預付費／後付費帳單，消費明細 |
| 帳戶設定 | ✓ | MFA 綁定、通知偏好 |

> **說明：** 租戶端不顯示「推理服務」選單，推理服務部署屬於平台供應端能力，不在此手冊範圍內。

---

## 2. 快速入門

### 2.1 環境要求

| 項目 | 要求 |
| --- | --- |
| 瀏覽器 | Chrome 90+、Firefox 88+、Edge 90+、Safari 14+ |
| 網路 | 能夠存取平台部署的網域或 IP 位址 |
| 帳號 | 由平台管理員建立並指派的使用者帳號（租戶管理員 或 開發者／演算法使用者 角色） |

### 2.2 登入平台

操作步驟：

1. 在瀏覽器中前往平台網址（請聯絡平台管理員取得），進入登入頁面
2. 輸入使用者名稱與密碼
3. 若已啟用 MFA 多因素驗證，輸入動態驗證碼
4. 點選「登入」按鈕進入平台

> **預期結果：** 登入成功後進入平台首頁，左側顯示導覽選單，右側顯示主內容區。

### 2.3 平台介面概覽

登入成功後，MaaS 平台主介面包含以下區域：

- **左側導覽列**：依功能模組顯示選單入口，包含模型市場、API KEY、用量、帳戶、預算提醒等。一般使用者／開發者視角不顯示「組織管理」選單
- **頂端資訊列**：顯示平台 Logo（ZSTUDIO）、目前使用者名稱、租戶資訊、語言切換入口、頁面最上方的全域通知列
- **主內容區**：顯示目前選取頁面的內容

### 2.4 典型使用流程

開發者典型使用流程：

```text
瀏覽模型市場 → 線上體驗模型 → 建立 APIKey → 整合 API 呼叫 → 查看用量
```

1. **瀏覽模型市場**：在模型市場中瀏覽可用模型，依類型、提供者等條件篩選，查看模型詳情與定價
2. **線上體驗模型**：透過 Playground 線上測試模型效果，調整參數，觀察輸出品質
3. **建立 APIKey**：建立 APIKey 作為 API 呼叫憑證
4. **整合 API 呼叫**：使用 APIKey 在應用程式中呼叫模型 API（詳見 §4.1）
5. **查看用量**：在「用量」頁面監控 Token 消耗與 API 呼叫情況

---

## 3. 功能詳解

### 3.1 模型市場

#### 3.1.1 功能說明

模型市場是使用者瀏覽、發現與選擇 AI 模型的核心入口。平台匯集了自部署模型與第三方通路模型（如 OpenAI 等），使用者可在模型市場中一站式瀏覽模型資訊、查看定價、閱讀 API 文件，並直接進入線上體驗。

#### 3.1.2 模型卡片瀏覽

模型市場以卡片網格形式顯示所有可用模型。每個模型卡片顯示以下資訊：

| 欄位 | 說明 |
| --- | --- |
| 模型名稱 | 模型的顯示名稱 |
| 輸入 Token 價格（每 1M tokens） | 每 1M Token 的輸入價格 |
| 輸出 Token 價格（每 1M tokens） | 每 1M Token 的輸出價格 |
| 上下文長度 | 模型支援的最大上下文 Token 數 |
| 快取命中價格（1M） | 命中快取時的每 1M Token 價格 |
| 快取建立價格（1M） | 建立快取時的每 1M Token 價格 |
| 參數量 | 模型參數規模 |
| 上架狀態 | 模型目前狀態，如「已上架」 |
| 發布時間 | 模型上架時間 |

#### 3.1.3 搜尋、篩選與排序

操作步驟：

1. **搜尋模型**：在頁面上方的搜尋框中輸入模型名稱或提供者關鍵字，系統即時顯示符合的結果
2. **分類篩選**：點選篩選列中的類型標籤（如「對話」、「文字生成」、「程式碼生成」），縮小顯示範圍
3. **排序切換**：使用排序下拉式選單切換排序方式，可選：
   - 熱門優先：依呼叫量排序，預設選項
   - 最新上架：依上架時間從新到舊
   - 價格遞增：依輸入 Token 單價從低到高
   - 價格遞減：依輸入 Token 單價從高到低

注意事項：

- 搜尋支援模糊比對，不區分大小寫
- 篩選條件可疊加使用（如同時篩選「對話」類型與「OpenAI」提供者）
- 切換排序後，篩選條件保持不變

#### 3.1.4 模型詳情頁

點選模型卡片進入模型詳情頁，包含以下四個標籤頁：

**總覽（Overview）** — 顯示模型的基本資訊與使用說明：

- 模型名稱、提供者、來源、類型
- 上下文長度、最大輸出 Token
- 模型能力描述與適用場景介紹
- 模型版本資訊

**定價（Pricing）** — 顯示模型的計費資訊：

| 定價項 | 說明 |
| --- | --- |
| 輸入 Token 價格 | 請求中 Prompt 部分每 1M tokens 的價格 |
| 輸出 Token 價格 | 回應中 Completion 部分每 1M tokens 的價格 |

**API 文件（API Docs）** — 顯示模型 API 的呼叫資訊：

- API 端點 URL
- 請求方式（POST）
- 請求參數說明
- 請求／回應範例（cURL、Python、Node.js）
- 驗證方式說明

**線上體驗（Playground）** — 直接跳轉至 Playground 線上體驗頁面，詳見 3.2。

#### 3.1.5 注意事項

- 模型市場中顯示的模型均為平台已上架且可呼叫的模型
- 不同模型的定價可能不同，請在呼叫前確認定價資訊
- 模型詳情頁的 API 文件提供了完整的呼叫範例，可直接複製使用
- 如未找到需要的模型，請聯絡平台管理員

### 3.2 線上體驗（Playground）

#### 3.2.1 功能說明

線上體驗（Playground）是一個瀏覽器端的模型互動測試環境，使用者無需撰寫程式碼即可線上測試模型效果。Playground 支援串流輸出、參數調節、多輪對話、費用估算與程式碼匯出等功能，協助使用者在正式介接前快速評估模型效果。

#### 3.2.2 主要功能

| 功能 | 說明 |
| --- | --- |
| 選擇 APIKey | 選擇一個狀態正常且有權限的 APIKey 進行呼叫 |
| 串流輸出 | 支援 SSE（Server-Sent Events）串流逐 Token 渲染模型輸出 |
| 參數調節 | 可調節 Temperature、Top P、Top K、最大 Token、重複懲罰等推理參數 |
| 系統提示詞 | 支援設定系統提示詞（System Prompt），定義模型行為 |
| 多輪對話 | 支援連續多輪對話，保持上下文 |
| 費用估算 | 即時顯示目前對話的輸入／輸出 Token 數與預估費用 |
| 程式碼複製 | 一鍵複製目前對話的 API 呼叫程式碼（cURL、Python、Node.js 格式） |
| 對話匯出 | 匯出對話記錄為 Markdown 或 JSON 格式 |

#### 3.2.3 可調參數詳解

| 參數 | 取值範圍 | 預設值 | 說明 |
| --- | --- | --- | --- |
| Temperature | 0–2，間隔 0.1 | 0.7 | 控制輸出的隨機性。值越高，輸出越隨機、多樣；值越低，輸出越確定、保守。0 近似貪婪解碼（每次選擇機率最高的 Token） |
| Top P | 0–1，間隔 0.1 | 1.0 | 核心採樣（Nucleus Sampling）機率門檻值。模型從累積機率達到 Top P 的候選 Token 中隨機選擇。值越小，候選集越小，輸出越集中；值越大，候選集越大，輸出越多樣。當 Top P = 1.0 時，不限制候選集 |
| Top K | 1–100，間隔 1 | 50 | 限制每一步候選 Token 的數量。模型僅從機率最高的 K 個 Token 中選擇。值越小，輸出越保守；值越大，輸出越多樣 |
| 最大 Token | 1–模型上下文上限 | 2048 | 單次生成的最大 Token 數量。設定過小可能導致回答被截斷；設定過大可能增加回應延遲 |
| 重複懲罰 | 1.0–2.0，間隔 0.1 | 1.0 | 抑制重複輸出。值越大，模型越傾向於避免重複已生成的 Token。設定為 1.0 時無懲罰效果 |
| 系統提示詞 | 文字，≤ 4000 字元 | 空 | 注入為 system 角色的訊息，用於定義模型的行為、角色、語氣與回答風格。例如：「你是一個專業的技術文件寫手，回答應當簡潔、準確。」 |
| 串流輸出 | 開／關 | 開 | 開啟時，模型逐 Token 即時回傳結果（SSE 串流）；關閉時，模型一次性回傳完整結果 |

參數調校建議：

| 場景 | 推薦設定 |
| --- | --- |
| 創意寫作、腦力激盪 | Temperature: 0.8–1.2, Top P: 0.9–1.0 |
| 程式碼生成、精確回答 | Temperature: 0–0.3, Top P: 0.1–0.5 |
| 日常對話、客服 | Temperature: 0.5–0.7, Top P: 0.8–0.9 |
| 翻譯、摘要 | Temperature: 0.2–0.4, Top P: 0.5–0.8 |

#### 3.2.4 操作步驟

**步驟一：進入 Playground** — 透過以下任一方式進入：

- 在模型市場點選模型卡片的「立即體驗」按鈕
- 在模型詳情頁點選「線上體驗」標籤頁
- 在左側導覽列直接點選「Playground」入口

**步驟二：選擇 APIKey**

1. 在右側參數面板的「APIKey」下拉式選單中，選擇一個可用的 APIKey
2. 系統會驗證 APIKey 的狀態與有效性
3. 如無可用的 APIKey，點選「建立 APIKey」跳轉至 APIKey 管理頁面建立

> **預期結果：** APIKey 選擇成功後，參數面板下方顯示 APIKey 的速率限制資訊。

**步驟三：設定推理參數**

1. 在參數面板中依序調整各參數：
   - 拖曳 Temperature 滑桿或直接輸入數值
   - 拖曳 Top P 滑桿或直接輸入數值
   - 拖曳 Top K 滑桿或直接輸入數值
   - 輸入最大 Token 數量
   - 拖曳重複懲罰滑桿或直接輸入數值
2. 在「系統提示詞」文字方塊中輸入角色設定（可選）
3. 確認「串流輸出」開關狀態（預設開啟）

> **預期結果：** 參數調整後即時生效，面板顯示目前各參數的值。

**步驟四：發起對話**

1. 在頁面下方的輸入框中輸入訊息內容
2. 點選「傳送」按鈕或按 Enter 鍵送出
3. 觀察左側對話區的串流輸出效果

> **預期結果：** 模型開始逐 Token 生成回覆，即時顯示在對話區中。費用估算區同步更新 Token 數與預估費用。

**步驟五：查看費用估算**

1. 每次對話完成後，費用估算區自動更新
2. 顯示資訊包括：
   - 目前對話輸入 Token 數
   - 目前對話輸出 Token 數
   - 目前對話預估費用
   - 累計 Token 數（多輪對話）

> **預期結果：** 費用資訊即時更新，協助使用者了解每次呼叫的成本。

**步驟六：複製程式碼**

1. 對話完成後，點選上方工具列的「複製程式碼」按鈕
2. 在彈出的選單中選擇程式碼格式：cURL、Python、Node.js
3. 程式碼已複製到剪貼簿，可直接貼上到程式碼編輯器中使用

> **預期結果：** 複製成功，程式碼包含完整的 API 端點、APIKey、模型名稱與請求參數。

**步驟七：匯出對話**

1. 點選上方工具列的「匯出對話」按鈕
2. 選擇匯出格式：Markdown 或 JSON
3. 檔案自動下載到本機

> **預期結果：** 匯出檔案包含完整的對話歷史與參數設定資訊。

#### 3.2.5 注意事項

- Playground 中的呼叫是真實的 API 呼叫，會產生 Token 消耗與費用
- 請確保選擇的 APIKey 狀態正常
- 系統提示詞設定過長會影響模型有效上下文長度，建議控制在 500 字元以內
- 多輪對話會累積 Token 消耗，長時間對話後建議清空對話重新開始
- 複製的程式碼中不包含實際的 APIKey 字串，需替換為 YOUR_API_KEY 後使用

### 3.3 APIKey 管理

#### 3.3.1 功能說明

APIKey 是呼叫 MaaS 平台模型 API 的驗證憑證。使用者透過 APIKey 管理頁面建立、編輯與刪除自己的 APIKey，並查看每個 APIKey 的速率限制資訊。一般使用者／開發者只能管理自己建立的 APIKey，無法查看或操作其他使用者的 APIKey。

#### 3.3.2 APIKey 屬性說明

| 屬性 | 說明 |
| --- | --- |
| 名稱 | APIKey 的顯示名稱，用於識別與管理，建議使用有意義的命名（如「生產環境-聊天機器人」、「測試環境-王小明」） |
| 金鑰 | 系統生成的唯一金鑰字串，建立後僅顯示一次，請立即儲存 |
| 狀態 | 正常（Active）／ 已停用（Disabled） |
| 速率限制 | 建立時基於預設層級向下調整，顯示目前 RPM／TPM 上限 |
| 所屬使用者 | APIKey 歸屬的使用者 |
| 建立時間 | APIKey 的建立時間 |
| 最近使用時間 | APIKey 最近一次使用時間 |

#### 3.3.3 操作說明

**建立 APIKey：**

1. 進入「APIKey」頁面，點選「建立 APIKey」按鈕
2. 在彈出的建立對話方塊中填寫名稱（必填）
3. 設定速率限制（可選）：可基於目前預設層級向下調整 RPM／TPM 值，但不能超過預設層級上限
4. 在彈出的金鑰顯示視窗中，立即複製並儲存金鑰

> **預期結果：** APIKey 建立成功，在清單中可見。金鑰僅在建立時顯示一次。

> ⚠️ **安全警告：** 金鑰僅在建立成功時顯示一次，關閉彈出視窗後將無法再次查看完整金鑰。請立即複製並妥善儲存到安全的地方（如金鑰管理工具、環境變數檔案）。不要在程式碼中硬編碼或提交到版本控制系統。

**編輯 APIKey：**

1. 在 APIKey 清單中找到目標 Key
2. 點選操作欄的「編輯」按鈕
3. 修改 APIKey 的名稱
4. 點選「儲存」

> **預期結果：** APIKey 資訊更新成功。注意：金鑰本身不可編輯，如需更換金鑰請刪除後重新建立。

**刪除 APIKey：**

1. 在 APIKey 清單中找到目標 Key
2. 點選操作欄的「刪除」按鈕
3. 在確認彈出視窗中點選「確認刪除」

> **預期結果：** APIKey 被刪除，已刪除的 Key 立即失效，無法繼續用於 API 呼叫。已產生的計費歷史保留。

#### 3.3.4 APIKey 清單

APIKey 清單顯示目前使用者已建立的 APIKey，包含以下資訊：

| 清單欄位 | 說明 |
| --- | --- |
| 名稱 | APIKey 的名稱 |
| 狀態 | 正常 / 已停用 |
| 速率限制 | 基於預設層級向下調整後的 RPM／TPM 值 |
| 所屬使用者 | APIKey 歸屬的使用者 |
| 建立時間 | APIKey 的建立時間 |
| 最近使用時間 | APIKey 最近一次使用時間 |
| 操作 | 編輯、刪除 |

#### 3.3.5 速率限制說明

APIKey 的速率限制基於預設層級設定。建立 APIKey 時可基於目前預設層級向下調整 RPM／TPM 值（不能超過預設層級上限）；若平台管理員修改預設層級，未修改過速率的 APIKey 自動跟隨變更，已修改過速率的 APIKey 保持不變（但若手動上調後的值大於新預設層級，則自動降低至新層級值）。

| 概念 | 說明 |
| --- | --- |
| RPM（Requests Per Minute） | 每分鐘允許的最大 API 請求次數 |
| TPM（Tokens Per Minute） | 每分鐘允許的最大 Token 消耗量（輸入 + 輸出） |
| 預設層級 | 平台管理員在層級範本中統一設定的速率上限（T0–T5） |
| 速率限制觸發 | 當超出 RPM 或 TPM 限制時，API 回傳 HTTP 429 狀態碼，請求被拒絕 |

#### 3.3.6 注意事項

- 金鑰建立後僅顯示一次，請務必妥善儲存
- 建議為不同環境（生產、測試、開發）建立獨立的 APIKey
- 定期檢查 APIKey 清單，及時刪除不再使用的 Key
- APIKey 狀態變為「已停用」後，無法繼續使用。如需繼續使用，請聯絡租戶管理員啟用或建立新的 APIKey
- 不要在用戶端程式碼（如瀏覽器 JavaScript、行動 App）中直接暴露 APIKey

### 3.4 用量

#### 3.4.1 功能說明

用量頁面為使用者提供 Token 消耗與 API 呼叫統計的視覺化檢視，協助使用者了解模型使用情況、監控消耗趨勢、分析成本組成。使用者可依時間、模型、APIKey 等維度篩選與查看用量資料，並支援匯出 CSV 檔案。一般使用者／開發者只能查看自己的 APIKey 產生的用量資料。

#### 3.4.2 功能組成

「用量」頁面由以下部分組成：

| 組成部分 | 說明 |
| --- | --- |
| 總覽用量 | 顯示關鍵指標卡片與用量趨勢 |
| Token 使用趨勢 | 依日／依週／依月顯示 Token 消耗趨勢 |
| 依 API 統計 | 依 API 維度彙整顯示用量 |
| 依模型統計 | 依模型維度彙整顯示用量 |
| 即時明細 | 顯示呼叫明細記錄，支援篩選與匯出 |

#### 3.4.3 總覽用量

總覽用量區域顯示以下關鍵指標與趨勢：

- **關鍵指標卡片：**
  - 總 Token 消耗量（輸入 + 輸出）
  - 總 API 呼叫次數
  - 活躍 APIKey 數量
- **趨勢圖表：**
  - Token 消耗趨勢圖
  - API 呼叫次數趨勢圖
  - 模型消耗佔比圖

#### 3.4.4 Token 使用趨勢

Token 使用趨勢支援依 日 / 週 / 月 三個維度顯示 Token 消耗走勢，協助使用者分析不同時間粒度下的使用變化。

#### 3.4.5 依 API 統計與依模型統計

- **依 API 統計**：依 API 維度彙整顯示呼叫量、Token 消耗與費用分佈
- **依模型統計**：依模型維度彙整顯示呼叫量、Token 消耗與費用分佈

#### 3.4.6 即時明細

即時明細以表格形式顯示詳細的呼叫記錄，包含以下欄位：

| 欄位 | 說明 |
| --- | --- |
| 時間 | 呼叫發生的時間 |
| 模型 | 呼叫的模型名稱 |
| APIKey | 使用的 APIKey 名稱 |
| 輸入 Token | 請求消耗的輸入 Token 數 |
| 輸出 Token | 回應生成的輸出 Token 數 |
| 總 Token | 輸入 Token + 輸出 Token |
| 費用 | 本次呼叫的預估費用 |

操作步驟：

1. 進入「用量」頁面
2. 切換到「即時明細」標籤頁
3. 設定篩選條件：
   - 時間範圍：選擇要查看的時間段
   - 模型：選擇特定模型或「全部模型」
   - APIKey：選擇特定 APIKey 或「全部 APIKey」
4. 查看篩選後的明細清單
5. （可選）點選「匯出 CSV」按鈕，下載篩選範圍內的用量資料

> **預期結果：** 明細清單根據篩選條件更新；CSV 檔案下載成功，包含篩選範圍內的所有用量記錄。

#### 3.4.7 注意事項

- 用量資料有一定的統計延遲（通常為 5-10 分鐘），非即時資料
- 費用為預估值，實際計費以帳單為準
- 匯出 CSV 時，資料量較大可能耗時較長，請耐心等待
- 時間範圍選擇「自訂」時，最長支援查詢 90 天內的資料

### 3.5 預算提醒

#### 3.5.1 功能說明

預算提醒功能協助使用者控制 API 呼叫成本，避免意外超支。使用者可以建立提醒規則，設定每月預算金額與提醒門檻值，當用量達到門檻值時，系統自動透過指定管道傳送提醒通知。當預算用盡（達到 100%）時，系統可自動暫停 API 呼叫，防止進一步產生費用。一般使用者／開發者只能管理自己的預算提醒規則。

#### 3.5.2 提醒規則要素

| 要素 | 說明 |
| --- | --- |
| 規則名稱 | 提醒規則的名稱，便於識別 |
| 範圍 | 預算的作用範圍：全域預算（所有模型）或指定模型預算 |
| 門檻值 | 觸發提醒的預算使用百分比，如 50%、80%、95%、100% |
| 管道 | 接收提醒通知的管道：站內信、郵件 |
| 啟用 | 提醒規則是否啟用 |
| 上次觸發 | 最近一次觸發提醒的時間 |

#### 3.5.3 操作步驟

**建立提醒規則：**

1. 進入「預算提醒」頁面，點選「建立提醒規則」按鈕
2. 在彈出的設定對話方塊中填寫規則資訊：
   - 規則名稱（必填）：輸入一個易於識別的名稱，如「每月預算提醒」
   - 範圍（必填）：選擇「全域預算」或「指定模型」（選擇指定模型後，從下拉式選單中選擇目標模型）
   - 門檻值（必填）：勾選需要提醒的百分比門檻值，支援多選（如同時勾選 50%、80%、95%、100%）
   - 管道（必填）：勾選至少一個通知管道（站內信 / 郵件）
3. 點選「儲存」提交

> **預期結果：** 提醒規則建立成功，在規則清單中可見。規則立即生效，系統開始監控用量。

**管理提醒規則：**

1. 在提醒規則清單中找到目標規則
2. 可執行的操作：
   - 編輯：修改規則設定（預算金額、門檻值、通知管道）
   - 啟用／停用：暫時關閉或重新啟用提醒規則
   - 刪除：刪除不再需要的提醒規則

> **預期結果：** 操作即時生效，規則狀態更新。

**提醒通知範例：** 當預算使用達到門檻值時，系統傳送如下格式的通知：

```text
[預算提醒 - 80%]
您的每月預算已使用 80%（NT$800 / NT$1,000）。
目前 Token 消耗：1,200,000。
請關注用量，避免超出預算。
```

```text
[預算提醒 - 100%]
您的每月預算已用盡（NT$1,000 / NT$1,000）。
API 呼叫已被暫停。如需繼續使用，請調整預算上限或等待下個計費週期。
```

#### 3.5.4 注意事項

- 提醒規則建立後立即生效，從目前計費週期開始監控
- 建議至少設定 80% 與 95% 兩個門檻值，以便在預算用盡前有充足時間調整
- 通知管道至少需要選擇一個，否則無法收到提醒通知
- 達到 100% 門檻值後，API 呼叫自動暫停，需手動調整預算上限才能恢復
- 每月 1 日預算用量重設，提醒規則持續生效
- 刪除的提醒規則無法復原，如需重新監控請新增規則

### 3.6 帳單查看

#### 3.6.1 功能說明

帳單查看功能為使用者提供預付費與後付費帳單的查詢服務，協助使用者清楚了解費用組成與消費明細。使用者可依時間範圍篩選帳單，查看每筆消費的詳細資訊。一般使用者／開發者只能查看自己 APIKey 產生的帳單資料。

#### 3.6.2 帳單類型

| 帳單類型 | 說明 |
| --- | --- |
| 預付費帳單 | 餘額儲值記錄、Token 消費明細、餘額變動記錄 |
| 後付費帳單 | 依量計費的消費彙整與明細 |

#### 3.6.3 帳單資訊

帳單概覽：

- 目前計費週期總費用
- 費用趨勢圖（依日）
- 模型消費佔比

消費明細：

| 欄位 | 說明 |
| --- | --- |
| 時間 | 消費發生的時間 |
| 模型 | 使用的模型名稱 |
| APIKey | 使用的 APIKey 名稱 |
| 消費類型 | 輸入 Token 消費 / 輸出 Token 消費 |
| Token 數量 | 消耗的 Token 數量 |
| 單價 | 每 1M tokens 的單價 |
| 金額 | 本次消費金額 |

#### 3.6.4 操作步驟

**查看帳單概覽：**

1. 進入「帳單」頁面
2. 預設顯示帳單概覽檢視，包含總費用、費用趨勢圖與模型消費佔比
3. 使用時間範圍選擇器切換統計週期（本月、上月、最近 3 個月、自訂範圍）

> **預期結果：** 帳單概覽根據選擇的時間範圍更新。

**查看消費明細：**

1. 在帳單頁面切換到「消費明細」標籤頁
2. 設定篩選條件：
   - 時間範圍：選擇要查看的時間段
   - 模型：選擇特定模型或「全部模型」
   - APIKey：選擇特定 APIKey 或「全部 APIKey」
3. 查看篩選後的消費明細清單

#### 3.6.5 注意事項

- 帳單資料有一定的統計延遲（通常為 1 小時），非即時資料
- 費用以實際計費為準，用量頁面的費用為預估值
- 建議定期（如每週）查看帳單，及時了解費用情況
- 如有帳單疑問，請聯絡平台管理員

### 3.7 帳戶設定

#### 3.7.1 功能說明

帳戶設定提供使用者個人資訊管理功能，包括多因素驗證（MFA）綁定與通知偏好設定。

#### 3.7.2 MFA 設定

多因素驗證（MFA）為帳戶安全提供額外防護。啟用 MFA 後，登入時除密碼外還需輸入動態驗證碼。

**綁定 MFA：**

1. 進入「帳戶設定 > MFA 設定」頁面
2. 點選「啟用 MFA」按鈕
3. 系統顯示一個 QR Code
4. 使用驗證器 App（如 Google Authenticator、Microsoft Authenticator、Authy 等）掃描 QR Code
5. 在驗證器 App 中取得 6 位動態驗證碼
6. 在頁面中輸入驗證碼，點選「驗證並啟用」
7. 系統生成備用復原碼，請下載並妥善儲存

> **預期結果：** MFA 啟用成功，下次登入時將要求輸入動態驗證碼。

**解除綁定 MFA：**

1. 進入「帳戶設定 > MFA 設定」頁面
2. 點選「解除綁定 MFA」
3. 輸入目前 MFA 動態驗證碼進行身分驗證
4. 確認解除綁定操作

> **預期結果：** MFA 解除綁定成功，登入時不再要求輸入動態驗證碼。

注意事項：

- 備用復原碼用於 MFA 裝置遺失時登入帳號，請妥善儲存
- 如 MFA 裝置與備用復原碼均遺失，請聯絡平台管理員處理
- 建議為所有使用者啟用 MFA，增強帳戶安全性

#### 3.7.3 通知偏好

設定使用者接收通知的管道偏好。

操作步驟：

1. 進入「帳戶設定 > 通知偏好」頁面
2. 勾選希望接收通知的管道：
   - 站內信：在平台內接收通知
   - 郵件：傳送通知到註冊信箱
3. 選擇需要接收通知的類型：
   - 預算提醒
   - 系統通知
   - 帳單提醒
4. 點選「儲存」

> **預期結果：** 通知偏好設定儲存成功，後續通知將依設定傳送。

> 📷 **截圖佔位符：** MaaS-使用者-帳戶設定-通知偏好

| 屬性 | 說明 |
| --- | --- |
| 截圖內容 | 通知偏好設定頁面 |
| 場景 | 使用者設定通知管道與類型 |
| 重點展示元素 | ①通知管道核取方塊（站內信／郵件）②通知類型核取方塊（預算提醒／系統通知／帳單提醒）③「儲存」按鈕 |
| 截圖角度 | 擷取通知偏好設定頁面的完整內容 |

---

## 4. 操作指南

### 4.1 場景一：開發者首次介接 MaaS 平台 API

**目標：** 作為開發者，完成從瀏覽模型到呼叫 API 的完整串接流程。

**前置條件：** 已擁有 開發者／演算法使用者 角色帳號，已登入平台。

**操作步驟**

**步驟一：瀏覽並選擇模型**

1. 進入「模型市場」頁面
2. 使用搜尋框輸入關鍵字（如「對話」）或透過類型篩選找到合適的模型
3. 點選感興趣的模型卡片，進入模型詳情頁
4. 在「總覽」標籤頁查看模型能力介紹
5. 在「定價」標籤頁了解費用標準
6. 在「API 文件」標籤頁查看 API 端點 URL 與參數說明

**步驟二：線上體驗模型效果**

1. 在模型詳情頁點選「線上體驗」標籤頁，或直接點選「立即體驗」按鈕
2. 選擇一個可用的 APIKey（如沒有，先執行步驟三建立）
3. 調整推理參數（Temperature、最大 Token 等，詳見 3.2.3）
4. 輸入測試訊息，觀察模型回覆效果
5. 確認模型效果滿足需求後，點選「複製程式碼」取得呼叫程式碼

**步驟三：建立 APIKey**

1. 進入「APIKey」頁面，點選「建立 APIKey」
2. 輸入名稱（如「我的應用-生產環境」）
3. 點選「確定」
4. 立即複製並儲存金鑰

**步驟四：整合 API 呼叫**

以下為完整的 API 呼叫程式碼範例。

Python 範例（使用 OpenAI 相容 SDK）：

```python
from openai import OpenAI

# 初始化用戶端，指向 MaaS 平台 API 端點
client = OpenAI(
    api_key="YOUR_API_KEY",  # 替換為您的 APIKey
    base_url="https://api.zettabyte.com/v1"  # 替換為實際的平台 API 端點
)

# 發起對話請求
response = client.chat.completions.create(
    model="gpt-4o",  # 替換為實際模型名稱
    messages=[
        {"role": "system", "content": "你是一個有幫助的助理。"},
        {"role": "user", "content": "請用一句話介紹人工智慧。"}
    ],
    temperature=0.7,
    max_tokens=2048,
    stream=True  # 串流輸出
)

# 處理串流回應
for chunk in response:
    if chunk.choices[0].delta.content:
        print(chunk.choices[0].delta.content, end="", flush=True)
print()
```

Python 範例（使用 requests 函式庫）：

```python
import requests
import json

url = "https://api.zettabyte.com/v1/chat/completions"
headers = {
    "Authorization": "Bearer YOUR_API_KEY",
    "Content-Type": "application/json"
}
payload = {
    "model": "gpt-4o",
    "messages": [
        {"role": "system", "content": "你是一個有幫助的助理。"},
        {"role": "user", "content": "請用一句話介紹人工智慧。"}
    ],
    "temperature": 0.7,
    "max_tokens": 2048
}

# 非串流請求
response = requests.post(url, headers=headers, json=payload)
if response.status_code == 200:
    result = response.json()
    print(result["choices"][0]["message"]["content"])
else:
    print(f"請求失敗: {response.status_code} - {response.text}")

# 串流請求
payload["stream"] = True
response = requests.post(url, headers=headers, json=payload, stream=True)
for line in response.iter_lines():
    if line:
        line = line.decode("utf-8")
        if line.startswith("data: "):
            data = line[6:]
            if data != "[DONE]":
                chunk = json.loads(data)
                if chunk["choices"][0]["delta"].get("content"):
                    print(chunk["choices"][0]["delta"]["content"], end="", flush=True)
print()
```

cURL 範例：

```bash
# 非串流請求
curl https://api.zettabyte.com/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -d '{
    "model": "gpt-4o",
    "messages": [
      {"role": "system", "content": "你是一個有幫助的助理。"},
      {"role": "user", "content": "請用一句話介紹人工智慧。"}
    ],
    "temperature": 0.7,
    "max_tokens": 2048
  }'

# 串流請求
curl https://api.zettabyte.com/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -d '{
    "model": "gpt-4o",
    "messages": [
      {"role": "system", "content": "你是一個有幫助的助理。"},
      {"role": "user", "content": "請用一句話介紹人工智慧。"}
    ],
    "temperature": 0.7,
    "max_tokens": 2048,
    "stream": true
  }'
```

Node.js 範例：

```javascript
// 使用 fetch API（Node.js 18+）
const url = "https://api.zettabyte.com/v1/chat/completions";

const payload = {
  model: "gpt-4o",
  messages: [
    { role: "system", content: "你是一個有幫助的助理。" },
    { role: "user", content: "請用一句話介紹人工智慧。" }
  ],
  temperature: 0.7,
  max_tokens: 2048
};

const response = await fetch(url, {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
    "Authorization": "Bearer YOUR_API_KEY"
  },
  body: JSON.stringify(payload)
});

const data = await response.json();
console.log(data.choices[0].message.content);
```

**步驟五：監控用量**

1. 進入「用量」頁面
2. 查看 Token 消耗趨勢與 API 呼叫次數
3. 切換到「即時明細」標籤頁，依 APIKey 篩選查看詳細呼叫記錄
4. 定期匯出 CSV 資料進行歸檔分析

> **完成標誌：** API 呼叫成功回傳模型回覆，用量頁面可看到呼叫記錄。

### 4.2 場景二：設定預算提醒與成本控制

**目標：** 作為一般使用者／開發者，設定每月預算提醒，控制個人 API 呼叫成本。

**前置條件：** 已擁有 開發者／演算法使用者 角色帳號，已登入平台。

**操作步驟**

**步驟一：分析歷史用量**

1. 進入「用量」頁面
2. 設定時間範圍為「最近 30 天」
3. 查看總 Token 消耗量與費用趨勢
4. 記錄日均 Token 消耗量，作為預算設定的參考依據

**步驟二：建立預算提醒規則**

1. 進入「預算提醒」頁面，點選「建立提醒規則」
2. 填寫規則設定：
   - 規則名稱：輸入「每月 API 呼叫預算控制」
   - 範圍：選擇「全域預算」
   - 預算金額：輸入 NT$500
   - 提醒門檻值：勾選 50%、80%、95%、100%
   - 通知管道：勾選「站內信」與「郵件」
3. 點選「儲存」

**步驟三：為模型建立獨立預算（可選）**

1. 再次點選「建立提醒規則」
2. 填寫規則設定：
   - 規則名稱：輸入「高成本模型預算控制」
   - 範圍：選擇「指定模型」，然後選擇消耗量最大的模型
   - 預算金額：輸入 NT$500
   - 提醒門檻值：勾選 80%、95%、100%
   - 通知管道：勾選「站內信」與「郵件」
3. 點選「儲存」

**步驟四：管理個人 APIKey**

1. 進入「APIKey」頁面，點選「建立 APIKey」
2. 輸入名稱（如「王小明-開發環境」）
3. 點選「確定」，複製金鑰
4. 將金鑰透過安全方式（如加密訊息、金鑰管理工具）分發給對應團隊成員
5. 重複以上步驟為每個團隊成員建立 APIKey

**步驟五：定期檢查帳單**

1. 進入「帳單」頁面
2. 每週查看一次帳單概覽與消費明細
3. 關注各 APIKey 的費用分佈，識別異常消費
4. 收到提醒通知後，及時分析原因並調整預算

**提醒通知處理流程：**

```text
收到提醒通知 → 查看用量頁面分析原因 → 決策：
  ├─ 正常消耗 → 調整預算上限
  ├─ 異常消耗 → 檢查 APIKey 使用情況
  └─ 預算不足 → 聯絡平台管理員
```

> **完成標誌：** 提醒規則建立成功，在規則清單中可見。首次達到門檻值時收到提醒通知。

### 4.3 場景三：透過 Playground 線上調校模型參數

**目標：** 作為開發者，透過 Playground 線上調整模型參數，找到最適合業務場景的設定。

**前置條件：** 已擁有 開發者／演算法使用者 角色帳號，已登入平台，已建立至少一個 APIKey。

**操作步驟**

**步驟一：進入 Playground 並選擇模型**

1. 進入「模型市場」頁面
2. 搜尋並選擇目標模型（如「GPT-4o」）
3. 點選「立即體驗」進入 Playground

**步驟二：設定系統提示詞**

在右側參數面板的「系統提示詞」文字方塊中輸入角色設定：

```text
你是一個專業的客服助理，你需要：
- 用友善、耐心的語氣回答客戶問題
- 回答簡潔準確，不超過 200 字
- 如果遇到無法解決的問題，引導客戶聯絡真人客服
```

**步驟三：調整參數進行對比測試**

*測試一：低溫度精確回答*

1. 設定參數：
   - Temperature: 0.2
   - Top P: 0.5
   - 最大 Token: 500
2. 輸入測試訊息：「請問如何重設密碼？」
3. 觀察回覆是否簡潔、準確

*測試二：中等溫度平衡回答*

1. 設定參數：
   - Temperature: 0.7
   - Top P: 0.9
   - 最大 Token: 500
2. 輸入同樣的測試訊息：「請問如何重設密碼？」
3. 觀察回覆是否在準確的基礎上增加了友善度

*測試三：高溫度創造性回答*

1. 設定參數：
   - Temperature: 1.2
   - Top P: 1.0
   - 最大 Token: 800
2. 輸入測試訊息：「請為我們的產品寫一段宣傳文案」
3. 觀察回覆是否更具創意與多樣性

**步驟四：多輪對話測試**

1. 在同一個對話中連續傳送多條訊息，測試上下文保持能力
2. 觀察模型是否正確理解前文內容
3. 注意費用估算區顯示的累計 Token 消耗

**步驟五：選擇最佳設定並匯出**

1. 對比各次測試的結果，選擇效果最好的參數組合
2. 記錄關鍵參數值：
   - Temperature: 0.7
   - Top P: 0.9
   - Top K: 50
   - 最大 Token: 2048
   - 系統提示詞：（已設定）
3. 點選「複製程式碼」，選擇 Python 格式，貼上到程式碼編輯器中
4. 點選「匯出對話」，選擇 Markdown 格式，儲存測試記錄

> **完成標誌：** 確定最佳參數組合，複製程式碼到專案中，匯出對話記錄作為參考文件。

### 4.4 場景四：多 APIKey 管理與用量監控

**目標：** 為不同應用或環境建立獨立的 APIKey，並分別監控用量。

**前置條件：** 已擁有 開發者／演算法使用者 角色帳號，已登入平台。

**操作步驟**

**步驟一：規劃 APIKey 命名規範**

訂定統一的 APIKey 命名規範，例如：

| 命名格式 | 範例 | 用途 |
| --- | --- | --- |
| {專案}-{環境}-{使用者} | 電商平台-生產-王小明 | 生產環境 APIKey |
| {專案}-{環境}-{使用者} | 電商平台-測試-王小明 | 測試環境 APIKey |
| {專案}-{環境}-{使用者} | 資料分析-生產-李美華 | 資料分析專案 APIKey |

**步驟二：批次建立 APIKey**

1. 進入「APIKey」頁面
2. 依規劃依序建立 APIKey：
   - 點選「建立 APIKey」
   - 輸入名稱（依命名規範）
   - 點選「確定」
   - 複製並儲存金鑰
3. 重複以上步驟，建立所有需要的 APIKey

**步驟三：分發 APIKey**

1. 將每個 APIKey 透過安全方式分發給對應團隊成員
2. 建議使用以下方式傳遞金鑰：
   - 加密的內部通訊工具
   - 金鑰管理系統的共享功能
   - 一次性閱讀連結
3. 不要透過郵件、即時通訊以明文傳送金鑰

**步驟四：依 APIKey 查看用量**

1. 進入「用量」頁面
2. 切換到「即時明細」標籤頁
3. 在「APIKey」篩選下拉式選單中選擇目標 APIKey
4. 設定時間範圍為「最近 7 天」
5. 查看該 APIKey 的 Token 消耗與呼叫次數
6. 重複以上步驟，逐一檢查各 APIKey 的用量

**步驟五：識別異常用量**

1. 對比各 APIKey 的用量資料，關注以下異常情況：
   - 用量突然暴增（可能是程式碼 bug 或濫用）
   - 某個 APIKey 長期未使用（可能已廢棄）
   - 非工作時間的呼叫（可能外洩）
2. 對異常 APIKey 採取相應措施：
   - 聯絡使用者確認情況
   - 刪除不再使用的 APIKey
   - 如懷疑外洩，立即刪除並建立新 Key

**步驟六：定期維護**

建議執行以下維護週期：

| 週期 | 任務 |
| --- | --- |
| 每日 | 檢查預算提醒通知 |
| 每週 | 檢查各 APIKey 用量，匯出 CSV 歸檔 |
| 每月 | 查看帳單，清理廢棄 APIKey，更新命名規範 |

> **完成標誌：** 所有 APIKey 建立完成並分發，用量監控機制建立，定期維護流程就緒。

---

## 5. 常見問題（FAQ）

### 5.1 模型市場

**Q1：如何找到適合我需求的模型？**

A：進入模型市場後，您可以透過以下方式快速定位模型：

1. 使用上方搜尋框輸入關鍵字（如「對話」、「程式碼」、「翻譯」）
2. 使用類型篩選標籤縮小範圍
3. 點選模型卡片進入詳情頁，查看模型能力描述與適用場景
4. 使用 Playground 線上測試模型效果，直觀評估是否滿足需求

**Q2：模型市場中看不到某個模型怎麼辦？**

A：模型市場僅顯示已上架的模型。如未找到需要的模型，可能原因：

1. 該模型尚未上架，請聯絡平台管理員確認
2. 搜尋關鍵字不符，請嘗試其他關鍵字
3. 篩選條件限制了結果，請清除篩選條件後重新搜尋

**Q3：如何查看模型的定價資訊？**

A：點選模型卡片進入模型詳情頁，切換到「定價」標籤頁即可查看：

- 輸入 Token 價格
- 輸出 Token 價格

### 5.2 線上體驗（Playground）

**Q4：Playground 中傳送的訊息會產生費用嗎？**

A：是的。Playground 中的呼叫是真實的 API 呼叫，會產生 Token 消耗與費用。費用估算區會即時顯示目前對話的預估費用，請留意控制測試成本。

**Q5：如何調整模型輸出讓回答更準確？**

A：建議從以下方面調整：

1. 降低 Temperature（如 0.1–0.3），使輸出更確定
2. 降低 Top P（如 0.3–0.5），縮小候選集
3. 設定詳細的系統提示詞，明確模型行為規則
4. 增加最大 Token 值，避免回答被截斷

**Q6：Playground 中複製的程式碼可以直接使用嗎？**

A：複製的程式碼中包含了完整的 API 端點、模型名稱與請求參數，但 APIKey 欄位為佔位符 YOUR_API_KEY。您需要將佔位符替換為實際的 APIKey 後即可使用。

**Q7：串流輸出與非串流輸出有什麼區別？**

A：

- **串流輸出（stream=true）**：模型逐 Token 即時回傳結果，使用者體驗更好，延遲感知更低，適合聊天場景
- **非串流輸出（stream=false）**：模型一次性回傳完整結果，適合批次處理、不需要即時回饋的場景

### 5.3 APIKey 管理

**Q8：APIKey 建立後能否再次查看完整金鑰？**

A：不能。金鑰僅在建立成功時顯示一次，關閉彈出視窗後無法再次查看。請務必在建立時立即複製並儲存。如金鑰遺失，請刪除舊 Key 並建立新 Key。

**Q9：APIKey 被停用了怎麼辦？**

A：被停用的 APIKey 無法繼續使用。如需繼續使用，請聯絡租戶管理員啟用或建立新的 APIKey，並更新應用程式中的金鑰設定。

**Q10：一個租戶可以建立多少個 APIKey？**

A：v1.24 中未對單一使用者的 APIKey 數量做硬性限制。建議依需求建立，為不同專案與環境使用獨立的 APIKey，便於用量監控與安全管理。

**Q11：如何安全地儲存與使用 APIKey？**

A：建議遵循以下安全實踐：

1. 將 APIKey 儲存在環境變數中，而非硬編碼在程式碼中
2. 使用金鑰管理工具（如 HashiCorp Vault、AWS Secrets Manager）
3. 不要在用戶端程式碼中暴露 APIKey
4. 不要將 APIKey 提交到版本控制系統（如 Git）
5. 定期輪換 APIKey，刪除不再使用的 Key

### 5.4 用量與計費

**Q12：用量頁面的資料是即時的嗎？**

A：不是完全即時的。用量資料通常有 5-10 分鐘的統計延遲。如需查看最新的呼叫情況，可參考 API 呼叫的即時回傳結果。

**Q13：為什麼用量頁面的費用與帳單中的費用不一致？**

A：用量頁面顯示的是預估值，基於目前定價計算。帳單中的費用為實際計費結果，以帳單為準。兩者可能存在微小差異，原因包括：

1. 定價策略變更
2. 統計週期差異

**Q14：如何降低 API 呼叫成本？**

A：建議從以下方面著手：

1. 最佳化 Prompt 長度，減少不必要的輸入 Token
2. 設定合理的最大 Token 值，避免輸出過長
3. 使用快取功能（如有），減少重複計算
4. 設定預算提醒，及時控制用量
5. 定期分析用量資料，識別高成本模型與呼叫

### 5.5 預算提醒

**Q15：設定了預算提醒但沒有收到通知怎麼辦？**

A：請檢查以下內容：

1. 確認提醒規則狀態為「已啟用」
2. 確認通知管道已正確設定（站內信／郵件）
3. 確認帳戶設定中的通知偏好已開啟對應類型
4. 檢查信箱的垃圾郵件匣
5. 確認用量是否確實達到了提醒門檻值

**Q16：預算達到 100% 後，API 呼叫被暫停了，如何恢復？**

A：請執行以下操作：

1. 進入「預算提醒」頁面
2. 編輯對應的提醒規則，提高預算金額上限
3. 儲存後，API 呼叫自動恢復
4. 如預算有限，可等待下個計費週期自動重設（每月 1 日）

**Q17：可以為不同的模型設定不同的預算嗎？**

A：可以。建立提醒規則時，在「範圍」中選擇「指定模型」，然後選擇目標模型，即可為該模型單獨設定預算與提醒門檻值。

### 5.6 API 呼叫

**Q18：API 呼叫回傳 401 錯誤是什麼原因？**

A：HTTP 401 表示驗證失敗。請檢查：

1. APIKey 是否正確（注意不要有多餘空格）
2. Authorization 請求標頭格式是否正確（應為 Bearer YOUR_API_KEY）
3. 如仍無法解決，請建立新 APIKey 重試

**Q19：API 呼叫回傳 429 錯誤是什麼原因？**

A：HTTP 429 表示觸發了速率限制（錯誤碼 rate_limit_exceeded）。這意味著您的 API 呼叫超過了 APIKey 的 RPM（每分鐘請求數）或 TPM（每分鐘 Token 數）上限。解決方法：

1. 降低請求頻率，在請求之間增加間隔
2. 實作指數退避重試機制
3. 聯絡平台管理員了解目前預設層級配額

**Q20：API 呼叫回傳 500 錯誤怎麼辦？**

A：HTTP 500 表示伺服器內部錯誤（錯誤碼 model_not_found 或 internal_error）。建議：

1. 等待片刻後重試（平台會自動重試伺服器錯誤）
2. 如持續出現，請記錄請求時間與內容，聯絡平台管理員
3. 在程式碼中實作重試邏輯，處理暫時性錯誤

---

## 6. 附錄

### 6.1 術語表

| 術語 | 全稱／說明 |
| --- | --- |
| MaaS | Model as a Service，模型即服務 |
| Token | 文字處理的最小單位，也是計費的基礎單元。一個 Token 約等於一個英文單字或一個漢字 |
| 輸入 Token | 請求中 Prompt（使用者輸入）部分的 Token 數量 |
| 輸出 Token | 回應中 Completion（模型輸出）部分的 Token 數量 |
| APIKey | 呼叫平台 API 的驗證憑證 |
| RPM | Requests Per Minute，每分鐘請求次數上限 |
| TPM | Tokens Per Minute，每分鐘 Token 消費量上限 |
| 租戶配額 | 租戶級別的 RPM／TPM 上限，該租戶下所有 APIKey 共享 |
| Tier | 速率限制層級（T0–T5），由平台管理員統一設定 |
| Playground | 線上模型體驗環境，可在瀏覽器中直接測試模型效果 |
| 串流輸出（Streaming） | 模型逐 Token 即時回傳結果的方式，基於 SSE（Server-Sent Events）協定 |
| 系統提示詞（System Prompt） | 注入為 system 角色訊息的文字，用於定義模型的行為與角色 |
| Temperature | 控制輸出隨機性的參數，值越高輸出越隨機 |
| Top P | 核心採樣機率門檻值，控制候選 Token 範圍 |
| Top K | 限制候選 Token 數量的參數 |
| MFA | Multi-Factor Authentication，多因素驗證 |
| SSE | Server-Sent Events，伺服器推送事件，用於串流輸出 |
| 預算提醒 | 當 API 呼叫費用達到設定門檻值時自動傳送通知的功能 |

### 6.2 錯誤碼說明

API 呼叫回傳的錯誤回應格式為：

```json
{
  "error": {
    "code": "錯誤碼",
    "message": "錯誤描述資訊",
    "type": "api_err"
  }
}
```

常見 HTTP 狀態碼及錯誤碼：

| HTTP 狀態碼 | error.code（範例） | 說明 | 處理建議 |
| --- | --- | --- | --- |
| 200 | - | 請求成功 | — |
| 400 | invalid_request | 請求參數錯誤 | 檢查請求主體格式、參數名稱與取值範圍 |
| 401 | unauthorized | 驗證失敗 | 檢查 APIKey 是否正確（格式：以 sk- 開頭） |
| 403 | forbidden | 權限不足 | 檢查 APIKey 是否有權限存取目標模型 |
| 429 | rate_limit_exceeded | 速率限制觸發 | 降低請求頻率，實作指數退避重試 |
| 500 | model_not_found / internal_error | 模型無法使用或服務內部錯誤 | 檢查模型是否已下架，或等待後重試 |

> **說明：** 以上為 API 閘道的典型錯誤碼，實際回傳的錯誤碼與訊息取決於上游模型服務的具體實作。

### 6.3 速率限制層級參考

MaaS 平台使用 T0–T5 六個層級作為速率限制的預設範本，由平台管理員在層級範本頁面統一管理。建立 APIKey 時可基於目前預設層級向下調整速率，但不能超過預設層級上限。

| 層級 | 名稱 | RPM | TPM | 適用場景 |
| --- | --- | --- | --- | --- |
| T0 | Trial | 100 | 300 | 個人試用 |
| T1 | Standard | 300 | 300,000 | 個人開發者 |
| T2 | Business | 1,000 | 1,500,000 | 小型團隊 |
| T3 | Enterprise | 3,000 | 5,000,000 | 中型團隊 |
| T4 | Flagship | 8,000 | 12,000,000 | 大型企業 |
| T5 | Custom | 30,000 | 50,000,000 | 關鍵業務 |

說明：

- 以上為層級範本參考值，實際值以平台管理員的設定為準
- 超出 RPM／TPM 限制時，API 回傳 HTTP 429 狀態碼
- 建立 APIKey 時只能基於預設層級向下調整；如需調整速率上限，請聯絡平台管理員在層級範本中修改預設層級

### 6.4 API 呼叫程式碼範例

#### 6.4.1 通用請求格式

- **API 端點：** `https://api.zettabyte.com/v1/chat/completions`
- **請求方式：** POST

請求標頭：

| 請求標頭 | 值 | 說明 |
| --- | --- | --- |
| Content-Type | application/json | 請求主體格式 |
| Authorization | Bearer YOUR_API_KEY | APIKey 驗證 |

請求主體參數：

| 參數 | 類型 | 必填 | 說明 |
| --- | --- | :---: | --- |
| model | string | 是 | 模型名稱，如「gpt-4o」 |
| messages | array | 是 | 對話訊息陣列，每條訊息包含 role（system／user／assistant）與 content（文字內容） |
| temperature | number | 否 | 溫度參數，取值範圍 0–2，預設 0.7 |
| top_p | number | 否 | 核心採樣參數，取值範圍 0–1，預設 1.0 |
| max_tokens | integer | 否 | 最大輸出 Token 數，預設 2048 |
| stream | boolean | 否 | 是否串流輸出，預設 false |

回應主體格式（非串流）：

```json
{
  "id": "chatcmpl-xxx",
  "object": "chat.completion",
  "created": 1700000000,
  "model": "gpt-4o",
  "choices": [
    {
      "index": 0,
      "message": {
        "role": "assistant",
        "content": "模型回覆內容"
      },
      "finish_reason": "stop"
    }
  ],
  "usage": {
    "prompt_tokens": 50,
    "completion_tokens": 100,
    "total_tokens": 150
  }
}
```

#### 6.4.2 Python SDK 範例

```python
# 安裝：pip install openai
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_API_KEY",
    base_url="https://api.zettabyte.com/v1"
)

# 非串流呼叫
response = client.chat.completions.create(
    model="gpt-4o",
    messages=[
        {"role": "system", "content": "你是一個有幫助的助理。"},
        {"role": "user", "content": "你好，請介紹一下自己。"}
    ],
    temperature=0.7,
    max_tokens=2048
)
print(response.choices[0].message.content)
print(f"Token 用量: {response.usage.total_tokens}")

# 串流呼叫
stream = client.chat.completions.create(
    model="gpt-4o",
    messages=[
        {"role": "user", "content": "寫一首關於春天的詩。"}
    ],
    temperature=0.8,
    max_tokens=500,
    stream=True
)
for chunk in stream:
    if chunk.choices[0].delta.content:
        print(chunk.choices[0].delta.content, end="", flush=True)
```

#### 6.4.3 Python requests 範例

```python
import requests
import json

API_KEY = "YOUR_API_KEY"
BASE_URL = "https://api.zettabyte.com/v1"

def chat_completion(model, messages, **kwargs):
    """傳送對話請求"""
    url = f"{BASE_URL}/chat/completions"
    headers = {
        "Authorization": f"Bearer {API_KEY}",
        "Content-Type": "application/json"
    }
    payload = {
        "model": model,
        "messages": messages,
        **kwargs
    }

    response = requests.post(url, headers=headers, json=payload)

    if response.status_code == 200:
        return response.json()
    elif response.status_code == 429:
        print("速率限制，請稍後重試")
        return None
    else:
        print(f"請求失敗: {response.status_code} - {response.text}")
        return None

# 使用範例
result = chat_completion(
    model="gpt-4o",
    messages=[
        {"role": "user", "content": "什麼是機器學習？"}
    ],
    temperature=0.5,
    max_tokens=1000
)

if result:
    print(result["choices"][0]["message"]["content"])
    print(f"Token 用量: {result['usage']['total_tokens']}")
```

#### 6.4.4 cURL 範例

```bash
# 設定環境變數
export API_KEY="YOUR_API_KEY"
export BASE_URL="https://api.zettabyte.com/v1"

# 非串流請求
curl -s "$BASE_URL/chat/completions" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $API_KEY" \
  -d '{
    "model": "gpt-4o",
    "messages": [
      {"role": "system", "content": "你是一個有幫助的助理。"},
      {"role": "user", "content": "請解釋什麼是雲端運算？"}
    ],
    "temperature": 0.7,
    "max_tokens": 2048
  }' | python -m json.tool

# 串流請求
curl -N "$BASE_URL/chat/completions" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $API_KEY" \
  -d '{
    "model": "gpt-4o",
    "messages": [
      {"role": "user", "content": "寫一首五言絕句。"}
    ],
    "temperature": 0.8,
    "max_tokens": 500,
    "stream": true
  }'
```

#### 6.4.5 Node.js 範例

```javascript
// 使用 fetch API（Node.js 18+）
const API_KEY = "YOUR_API_KEY";
const BASE_URL = "https://api.zettabyte.com/v1";

async function chatCompletion(model, messages, options = {}) {
  const url = `${BASE_URL}/chat/completions`;
  const payload = {
    model,
    messages,
    temperature: options.temperature ?? 0.7,
    max_tokens: options.maxTokens ?? 2048,
    stream: options.stream ?? false
  };

  const response = await fetch(url, {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
      "Authorization": `Bearer ${API_KEY}`
    },
    body: JSON.stringify(payload)
  });

  if (!response.ok) {
    throw new Error(`請求失敗: ${response.status} - ${await response.text()}`);
  }

  return response.json();
}

// 使用範例
(async () => {
  try {
    const result = await chatCompletion(
      "gpt-4o",
      [
        { role: "system", content: "你是一個有幫助的助理。" },
        { role: "user", content: "什麼是人工智慧？" }
      ],
      { temperature: 0.5, maxTokens: 500 }
    );
    console.log(result.choices[0].message.content);
    console.log(`Token 用量: ${result.usage.total_tokens}`);
  } catch (error) {
    console.error(error.message);
  }
})();
```

#### 6.4.6 錯誤處理最佳實踐

```python
import time
import requests

def call_with_retry(url, headers, payload, max_retries=3):
    """帶重試機制的 API 呼叫"""
    for attempt in range(max_retries):
        try:
            response = requests.post(url, headers=headers, json=payload)

            if response.status_code == 200:
                return response.json()
            elif response.status_code == 429:
                # 速率限制，指數退避重試
                wait_time = 2 ** attempt
                print(f"速率限制，等待 {wait_time} 秒後重試...")
                time.sleep(wait_time)
                continue
            elif response.status_code in [500, 502, 503]:
                # 伺服器錯誤，退避重試
                if attempt < max_retries - 1:
                    wait_time = 2 ** attempt
                    print(f"伺服器錯誤 {response.status_code}，等待 {wait_time} 秒後重試...")
                    time.sleep(wait_time)
                    continue
                else:
                    raise Exception(f"伺服器錯誤: {response.status_code}")
            else:
                raise Exception(f"請求失敗: {response.status_code} - {response.text}")
        except requests.exceptions.RequestException as e:
            if attempt < max_retries - 1:
                wait_time = 2 ** attempt
                print(f"網路錯誤，等待 {wait_time} 秒後重試...")
                time.sleep(wait_time)
                continue
            else:
                raise e

    raise Exception("達到最大重試次數")

# 使用範例
url = "https://api.zettabyte.com/v1/chat/completions"
headers = {
    "Authorization": "Bearer YOUR_API_KEY",
    "Content-Type": "application/json"
}
payload = {
    "model": "gpt-4o",
    "messages": [{"role": "user", "content": "Hello!"}]
}

try:
    result = call_with_retry(url, headers, payload)
    print(result["choices"][0]["message"]["content"])
except Exception as e:
    print(f"呼叫失敗: {e}")
```

---

> **文件結束**
>
> 本文件基於 MaaS v1.24 版本撰寫，適用於開發者／一般使用者角色。如有疑問或建議，請聯絡平台技術支援團隊。
