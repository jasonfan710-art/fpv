# AGENTS.md - ArduPilot 無人機開發與飛行測試日誌規範

## 1. 專案目的 (Project Purpose)
本專案為「ArduPilot 無人機開發與飛行測試日誌（UAV Build & Flight Test Log）」，用來系統化記錄無人機的機架設計、硬體配置、ArduPilot 飛控參數調校（EKF、震動抑制、GPS 定位）以及地面站實測影音紀錄，並透過 GitHub Pages 公開展示。
本文件旨在讓 AI 理解本專案的架構與設計邏輯，以便未來新增測試日誌或參數紀錄時，能自動維持一致的視覺風格與程式碼規範。

## 2. 整體視覺風格 (Design & Visual Style)
- **設計風格**：硬派航電工程風（Avionics & Telemetry Spec Sheet），強調參數規格清晰易讀與高對比度。
- **色彩配置**：
  - 背景主色：`#0F172A`（深空灰藍）
  - 卡片背景：`#1E293B`（石板灰，搭配細邊框 `1px solid #334155`）
  - 主要文字：`#F8FAFC`（亮白）
  - 次要說明文字：`#94A3B8`（冷灰）
  - 強調色（狀態燈號、重點數據）：`#F97316`（警戒橘）與 `#38BDF8`（遙測藍）
- **字體設定**：內文使用系統無襯線字體（`system-ui, -apple-system, "Noto Sans TC", sans-serif`），硬體規格、遙測狀態（如 `DISARMED`、`GPS Fixed`）與 ArduPilot 參數一律使用等寬字體（`monospace`）。
- **響應式設計 (RWD)**：支援手機與桌面端瀏覽，規格表格在手機版需支援橫向捲動（`overflow-x: auto`），不可破版。

## 3. 技術棧與頁面結構 (Tech Stack & Page Structure)
- **技術限制**：僅使用純前端技術（HTML5、CSS3），不依賴需要編譯的框架，確保可直接部署於 GitHub Pages。
- **全站共用結構**：
  1. `<header>`：頂部導覽列，左側為網站標題與飛控系統徽章（`ARDUPILOT / GPS`），右側包含「測試日誌列表」連結。
  2. `<main>`：主要內容區，最大寬度限制為 `920px` 並置中對齊（`margin: 0 auto`）。
  3. `<footer>`：頁尾版權宣告與「Check EKF, Vibe & GPS Before Arming」飛安標語。

## 4. 檔案命名與資料夾配置 (File Naming & Directory Structure)
新增任何檔案時，必須嚴格遵守以下目錄結構與全小寫連字號（kebab-case）命名規則：

```text
/ (專案根目錄)
├── AGENTS.md                                  # AI 開發規範文件 (本檔案)
├── index.html                                 # 網站首頁（顯示無人機專案總覽與最新測試日誌卡片）
├── css/
│   └── style.css                              # 全站共用樣式表（禁止在 HTML 內寫大量 inline style）
├── assets/                                    # 存放本地壓縮後的地面站截圖或照片
└── posts/                                     # 存放所有獨立裝機與實測紀錄頁面
    └── 2026-11-ardupilot-bench-test.html      # 命名格式：YYYY-MM-英文主題關鍵字.html