# MaaS 使用者操作手冊 — Mintlify 文件網站

本目錄為 MaaS v1.24 使用者操作手冊的 **Mintlify** 文件網站原始碼（`docs.json` + MDX）。

## 目錄結構

```
docs.json                     # Mintlify 設定（導覽、主題、顏色）
maas/
  index.mdx                   # 首頁
  product-overview/           # 產品概述
  quick-start/                # 快速入門
  features/                   # 功能詳解（7 頁）
  guides/                     # 操作指南（4 個場景）
  faq.mdx                     # 常見問題
  appendix/                   # 附錄（術語表、錯誤碼、速率限制層級、程式碼範例）
```

## 本機預覽

```bash
npm i -g mint      # 安裝 Mintlify CLI
mint dev           # 在專案根目錄（docs.json 所在處）啟動本機預覽
```

預設開啟 http://localhost:3000。

## 說明

- 內容取自校正版手冊 `MaaS_使用者操作手冊_v1.24_繁體中文.md`（已將中國用詞改為繁體中文用詞）。
- 頁面使用 Mintlify 元件：`<Note>`、`<Warning>`、`<Check>`、`<Info>`、`<Card>`、`<CardGroup>`。
- `docs.json` 中的 `logo`、`favicon` 為佔位路徑，請放入實際檔案（`/logo/light.svg`、`/logo/dark.svg`、`/favicon.svg`）。
