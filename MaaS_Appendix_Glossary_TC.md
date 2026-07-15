# 術語表

> Dubai Hybrid Cloud · 公有雲文件中心
> 路徑：模型即服務 MaaS › 附錄 › 術語表
> 最後更新：2026-06-30

---

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
