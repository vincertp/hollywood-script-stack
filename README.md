# Screenwriting from gStack

> 一個**思考機器，不是生產機器**。
>
> 幫助創作者在投入生產之前，知道這個故事值不值得生產。

[![Validate Skills](https://github.com/vincertp/hollywood-script-stack/actions/workflows/validate.yml/badge.svg)](https://github.com/vincertp/hollywood-script-stack/actions/workflows/validate.yml)

---

## 這個系統解決什麼問題

2026 年，AI 工具（小雲雀、Kling、Vidu）已經可以把劇本轉成成片。生產問題基本上被解決了。

但**爆款率仍然是 0.16%**。失敗的 99.84% 不是因為製作工具不夠好，是因為在生產之前，沒有人問過：**這個故事有沒有一個清晰的情感真相支撐它存在的理由？**

這個系統的唯一工作是：在你花錢生產之前，讓你看清楚你的故事的結構後果。

| 問題 | 誰解決 |
|---|---|
| 劇本 → 成片，視覺角色一致性 | 小雲雀 / Kling / Vidu |
| **這個概念值不值得做** | **本系統** |
| **這 80 集的情感架構是否成立** | **本系統** |
| **角色的心理一致性** | **本系統** |
| **為什麼第 30 集故事失去動力** | **本系統** |

---

## 微短劇人機協作編劇系統（v2）

靈感來源：[gstack](https://github.com/garrytan/gstack)。核心哲學相同——**把流程本身編碼為工具**，每個 Skill = 模式切換 + 對抗性提問 + 有立場的裁定。

### 三個思考模式，五個工具

```
DESIGN（設計）←→ EXECUTION（執行）←→ DIAGNOSTIC（診斷）
```

#### 設計模式

**[`/story-core`](micro-drama/story-core/SKILL.md)**
核心問題：這個故事有沒有存在的理由？

雙路線入口：
- **PREMIUM**：情感真相、角色創傷可見性、情感差異化
- **MARKET**：投流邏輯（3 秒截圖測試）、CPM 競爭、爽點時機

裁定：STORY CLEAR / STORY NEEDS PIVOT / STORY DEAD

---

**[`/story-architecture`](micro-drama/story-architecture/SKILL.md)**
核心問題：這部劇的五個決定命運的時刻是什麼？

輸出：
- 五個槓桿時刻（創傷暴露 → 第一次錯誤應對 → 表面勝利/內在失敗 → 不可逆代價 → 直面或毀滅）
- 資訊建築圖（誰知道什麼，何時揭示，戲劇性功能）

裁定：ARCHITECTURE LOCKED / INCOMPLETE / BROKEN

---

#### 執行模式

**[`/episode`](micro-drama/episode/SKILL.md)**
核心問題：這一集在架構裡是什麼位置？它的情感交易是什麼？

每集寫作前必須確認：在五個時刻裡的位置、資訊狀態變化、上一集 Cliffhanger 溫度（三溫度：熱/冷/溫）

格式：9:16，90-120 秒，60-80% 特寫

裁定：EPISODE READY / EPISODE BROKEN

---

#### 診斷模式

**[`/diagnose`](micro-drama/diagnose/SKILL.md)**
核心問題：故事從哪集開始失去動力？

三個根本原因：
1. **Character Drift** — 角色行動與核心創傷脫節
2. **Escalation Stagnation** — 賭注沒有升級
3. **Information Collapse** — 資訊不對稱已消解

---

**[`/develop`](micro-drama/develop/SKILL.md)** — 完整流程總覽

---

### 核心框架

**情感交易**：每集 90 秒 = 承諾（0-15s）→ 交付（15-75s）→ 驚喜 → 欠債（最後 15s）

**Scene Spine**：[角色] 想要 [X]，但 [阻礙，連結核心創傷]，所以 [行動]，結果 [一個維度變好，另一個變更壞]。不能只輸，不能只贏。

**Cliffhanger 三溫度**：
- 🔥 熱（Hot）：立即外部威脅。腎上腺素，衰減快。
- 🧊 冷（Cold）：安靜揭示，改寫前面所有事件的意義。恐懼感，付費衝動最強。
- 💛 溫（Tender）：意外連結，讓觀眾害怕接下來失去它。焦慮感，最被低估。

規則：不能連續三集使用同一溫度。

---

## Hollywood Script Stack（基礎）

好萊塢開發流程的 AI 協作工具，為長片和劇集設計：

```
/pitch → /showrunner → /structure → /story-edit → /draft → /script-doctor → /table-read → /production-lock
```

這套工具的原理——sequential gatekeeping、opinionated verdicts、handoff artifacts——是微短劇系統的設計基礎。詳見 [`docs/workflow.md`](docs/workflow.md)

---

## 人機協作原則

**AI 做的事**：挑戰假設、維護敘事狀態、翻譯結構框架

**人做的事**：所有故事決定（角色、情感、動機）、文化判斷、創意突破

**AI 永遠不告訴你寫什麼。AI 讓你清楚地看到你寫的東西的結構後果。**

---

## 使用方式

在支援 Claude 的環境（Claude Code、Cowork）中呼叫 Skill：

```
/story-core          # 從這裡開始——概念驗證
/story-architecture  # 五個槓桿時刻 + 資訊建築圖
/episode             # 逐集寫作
/diagnose            # 故事失去動力時進入
/develop             # 完整流程導引
```

---

## 參考

- [gstack](https://github.com/garrytan/gstack) — 本系統的哲學來源
- [小雲雀 AI](https://xyq.jianying.com/) — 解決生產問題的工具（本系統不重複）
- [WGA Basic Agreement 2023](https://www.wga.org/contracts/contracts/mba)
