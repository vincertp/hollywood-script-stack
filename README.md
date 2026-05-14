# Hollywood Script Stack

> 借鑑 [gstack](https://github.com/garrytan/gstack) 的 specialist-role 架構，為好萊塢劇本開發工作流程打造的 AI 協作系統。

[![Validate Skills](https://github.com/vincertp/hollywood-script-stack/actions/workflows/validate.yml/badge.svg)](https://github.com/vincertp/hollywood-script-stack/actions/workflows/validate.yml)

gstack 的核心洞察：**把流程本身編碼為提示詞**。23 個 specialist skill 的力量不在於工具，在於**結構化交接（structured handoffs）**——每個 skill 的輸出直接成為下一個 skill 的輸入，形成不可跳過的 review 鏈。

好萊塢開發流程天然就有相同的 gate 結構。它只是從來沒有被形式化過。這個 repo 解決這個問題。

---

## 完整工作流程

```
/pitch → /showrunner → /structure → /story-edit → /draft → /script-doctor → /table-read → /production-lock
```

或者，一個指令串聯全部：

```
/develop
```

---

## 角色映射：gstack → Hollywood

| gstack 角色 | Hollywood 對應 | Skill | 職責 |
|---|---|---|---|
| CEO Review | Executive Producer / Showrunner | `/showrunner` | IP 可行性、市場象限、串流平台 fit |
| Office Hours | Pitch Room | `/pitch` | 原始概念 → 可賣出的 logline + premise |
| Design Review | Story Editor | `/story-edit` | 抓「劇本 slop」：陳詞濫調、被動主角、說教 |
| Eng Manager | Story Architect | `/structure` | 結構鎖定：三幕、Blake Snyder beats、轉折點 |
| Build | Screenwriter | `/draft` | WGA 格式場景初稿，每頁 = 1 分鐘 |
| Code Review | Script Doctor | `/script-doctor` | 手術式修復：根源問題診斷，不全面改寫 |
| QA (Playwright) | Table Read | `/table-read` | 模擬桌讀，找死場景，kill/fix/keep 裁定 |
| Ship | Production Lock | `/production-lock` | 格式合規、法律清理、製作草稿鎖定 |
| Autoplan | Full Development Chain | `/develop` | 串聯完整開發流程 |

---

## 為什麼這套邏輯可以移植？

詳見 [`docs/workflow.md`](docs/workflow.md)

---

## Skill 清單

### `/pitch`
**角色**：CAA/WME 等級的故事分析師，讀過一萬個 logline。  
**作用**：把粗糙的想法煉成可賣出的概念。輸出：logline、premise、comp titles、中心戲劇問題。

### `/showrunner`
**角色**：在 Netflix 和 HBO 各有三部作品過的 EP。  
**作用**：以商業與創作的雙重標準審視概念。輸出：可行性報告、平台建議、受眾象限、預算等級。

### `/structure`
**角色**：輔導過奧斯卡入圍作品的結構顧問。熟悉 Blake Snyder、Syd Field、John Truby。  
**作用**：鎖定劇本架構。輸出：三幕分解、15 個 Blake Snyder beats（附頁碼）、五個轉折點。

### `/story-edit`
**角色**：待過五部重量級影集 writers' room 的故事編輯。  
**作用**：在桌讀前抓出「劇本 slop」。輸出：逐項檢查清單 + 修改建議。

### `/draft`
**角色**：WGA 掛名編劇。  
**作用**：以標準格式寫場景初稿。規則：動作行三行以內、台詞有潛台詞、1 頁 = 1 分鐘。

### `/script-doctor`
**角色**：週薪五萬美金的劇本醫生。手術式介入，不全面改寫。  
**作用**：診斷根源問題（結構 → 場景功能 → 對白，依序處理）。

### `/table-read`
**角色**：主持過 200 場以上桌讀的主持人，見識過劇本在房間裡死透的每一種方式。  
**作用**：模擬桌讀，逐場裁定 kill / fix / keep。

### `/production-lock`
**角色**：劇本統籌兼製片主管。  
**作用**：格式合規審查、法律清理、頁數達標，交出製作草稿。

---

## 關鍵設計原則（借自 gstack）

1. **Sequential gatekeeping** — 不能跳過結構鎖定直接寫初稿，就像不能跳過 architecture review 直接 build。
2. **Opinionated, not neutral** — 每個 skill 都有觀點，不是「這兩種都可以」的軟回應。
3. **Handoff artifacts** — 每個 skill 產出格式化的輸出，可以直接被下一個 skill 讀取。
4. **Kill gate** — `/showrunner` 和 `/story-edit` 都可以 hard stop 整個開發流程。
