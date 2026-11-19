# 📝 企業級新員工入職培訓考核及問卷系統
### Enterprise Onboarding Assessment & Feedback System (`EnterpriseDemo-OnboardingQuiz`)

[![Interactive Demo](https://img.shields.io/badge/Interactive%20Demo-GitHub%20Pages-0078D4?logo=github)](https://jackylawck.github.io/EnterpriseDemo-OnboardingQuiz/)
[![Streamlit](https://img.shields.io/badge/Built%20with-Streamlit-FF4B4B?logo=streamlit&logoColor=white)](https://streamlit.io/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Compliance: ISO 27001 | 9001 | 45001](https://img.shields.io/badge/Compliance-ISO%2027001%20%7C%209001%20%7C%2045001-107c41.svg)](SECURITY_COMPLIANCE.md)
[![Privacy: Zero-Data-Retention](https://img.shields.io/badge/Privacy-Zero--Data--Retention-orange.svg)](PRIVACY_POLICY.md)
[![AI Governance: Non-AI Deterministic](https://img.shields.io/badge/AI%20Governance-Non--AI%20Deterministic-teal.svg)](SECURITY_COMPLIANCE.md)

> **線上互動模擬器 / Live Interactive Simulator**：無需配置郵件伺服器，直接透過 [GitHub Pages 互動展示頁](https://jackylawck.github.io/EnterpriseDemo-OnboardingQuiz/) 體驗完整三階段考核、問卷與受控 PDF 生成閉環。

---

## 🌐 項目簡介 / System Overview

**EnterpriseDemo-OnboardingQuiz** 是一套專為現代企業設計的無紙化入職培訓考核與員工意見調查參考架構（Governance-as-Code Demo）。系統基於 Python 與 Streamlit 構建，在**不架設外置資料庫、零個人資料持久化（Zero-Data-Retention）**的前提下，將「規章知識考核」、「培訓滿意度與 ESG 活動調研」及「受控 PDF 報告自動歸檔（`DEMO-HR-REC-2026-V1`）」整合為端對端自動化閉環，兼顧 **ISO/IEC 27001 資訊安全**與**香港《個人資料（私隱）條例》(Cap. 486)** 合規要求。

**EnterpriseDemo-OnboardingQuiz** is a reference implementation for paperless enterprise onboarding assessments and employee engagement surveys built with Python and Streamlit. Operating with **zero external databases and strict Zero-Data-Retention**, it unifies policy knowledge testing, training satisfaction & ESG engagement surveys, and in-memory controlled PDF synthesis (`DEMO-HR-REC-2026-V1`) with encrypted TLS SMTP delivery—aligned with **ISO/IEC 27001**, **ISO 9001/45001**, and **Hong Kong PDPO (Cap. 486)**.

---

## 🛠️ 核心特色與合規工程 / Key Features & Governance Controls

| 核心維度 / Pillar | 繁體中文說明 | English Description |
| :--- | :--- | :--- |
| **零資料留存架構**<br>`Privacy-by-Design` | PDF 報告純於伺服器記憶體（RAM）即時繪製並透過 TLS 加密傳輸，關閉分頁即刻釋放，不在雲端留下任何個人識別資訊（PII）。 | Controlled PDFs are synthesized strictly in volatile RAM and dispatched over TLS; zero PII or files are persisted on disk or cloud storage. |
| **動態 Secrets 隔離**<br>`ISO/IEC 27001` | 通行金鑰、試題題庫、標準答案與 SMTP 憑證全數封裝於後端 `st.secrets`，公開原始碼零硬編碼機密，支援熱更新題庫。 | Access codes, quiz answer keys, and SMTP credentials reside solely in `st.secrets`—zero hardcoded secrets with hot-swappable quiz banks. |
| **確定性多題型評分**<br>`Non-AI Deterministic` | 支援**單選、多選與群組配對**三種題型（滿分 20 分，≥15 分／75% 合格）。採用純規則精確比對，明確排除於 EU AI Act 監管範圍外。 | Supports **single, multiple, and group-matching** items (20 pts max; ≥15 pts / 75% pass) via deterministic rule matching, scoped out of EU AI Act. |
| **受控 PDF 存證引擎**<br>`ISO 9001 / 45001` | 自動校準香港標準時間（UTC+8 HKT），嵌入受控編號 `DEMO-HR-REC-2026-V1`、誠信聲明與 PDPO 法定宣告，滿足審計調閱要求。 | Normalizes timestamps to HKT (UTC+8) and embeds controlled ID `DEMO-HR-REC-2026-V1`, integrity consent, and PDPO notices for audit readiness. |
| **一鍵加密發信與分流**<br>`Automated Closure` | 後端透過 `SMTP + STARTTLS (Port 587)` 直送 HR 信箱並附防重複發送鎖，配套 `Flow1` 與 `Flow2` 自動化歸檔及 7 天補考追蹤藍圖。 | Dispatches reports via `SMTP + STARTTLS (Port 587)` with deduplication locks, paired with `Flow1` & `Flow2` blueprints for archiving and retraining. |

---

## 🚀 系統運作閉環 / Application Workflow

```text
[0. Secrets 門禁驗證] ➔ [1. 第一部分：20分制考核] ➔ [2. 第二部分：滿意度與ESG問卷] ➔ [3. 第三部分：受控PDF生成與TLS寄送]
   Access Gate             Part I: Policy Quiz           Part II: Engagement Survey         Part III: SMTP Dispatch & Backup
```

1. **門禁核對 (Access Verification)**  
   透過專屬 URL 參數（`?key=...`）或手動輸入通行碼，與後端 `ACCESS_CODE` 比對放行。  
   *Authenticate via URL parameter (`?key=...`) or manual passcode verified against backend `ACCESS_CODE`.*
2. **第一部分：入職培訓測驗 (Part I: Onboarding Quiz)**  
   填寫姓名、職員編號及所屬組別，完成單選、多選及配對測驗並勾選誠信與 PICS 私隱聲明。  
   *Enter staff details, complete single/multiple/group-matching questions, and check the integrity & PICS declaration.*
3. **第二部分：問卷及興趣調查 (Part II: Feedback & Engagement Survey)**  
   即時檢視考核得分（達 15/20 分即 75% 為合格），填寫 1–5 分培訓評估、康體／義工活動意願及開放式建議。  
   *Review instant quiz results (≥15/20 or 75% to pass) and submit 1–5 training ratings, wellness/volunteering preferences, and culture feedback.*
4. **第三部分：一鍵加密送出與備份 (Part III: Dispatch & Archiving)**  
   點擊 **「🚀 一鍵自動送出報告至 HR 電郵」** 經 TLS 寄送受控 PDF，並可下載個人副本或使用備用通知通道。  
   *Trigger one-click TLS SMTP delivery with the attached controlled PDF, download a local backup, or use the alternative notification option.*

---

## 📂 專案結構與合規文件 / Repository Structure & Artifacts

```text
EnterpriseDemo-OnboardingQuiz/
├── app.py                                      # Streamlit 核心應用程式（門禁、三階段流程、PDF 渲染與 SMTP）
├── index.html                                  # GitHub Pages 雙語互動模擬器與企業管治技術文件頁
├── PRIVACY_POLICY.md                           # 個人資料收集聲明 (PICS) 與零留存私隱政策 (HK PDPO Cap. 486)
├── SECURITY_COMPLIANCE.md                      # 資訊安全白皮書 (ISO 27001 / 9001 / 45001 與非 AI 邊界聲明)
├── schemas/
│   └── onboarding_assessment_schema.json       # JSON Schema (Draft-07) 資料結構與防注入校驗規範
├── flows/
│   ├── Flow1_WorkerSubmissionToHR.json         # 第一階段：員工提交、記憶體合成 PDF 與 TLS 加密傳輸工作流
│   └── Flow2_HRAuditAndRecordRetention.json    # 第二階段：HR 受控歸檔與不合格（<75%）7 天補考追蹤工作流
├── NotoSansTC-Regular.ttf                      # 繁體中文向量 PDF 嵌入字型
├── requirements.txt                            # Python 依賴套件 (streamlit, fpdf2)
├── .gitignore                                  # 排除 .streamlit/ 本機機密目錄
└── LICENSE                                     # MIT 開源授權條款
```

---

## ⚙️ 快速部署與環境變數 / Quick Start & Secrets Configuration

### 1. 本機安裝與啟動 / Local Installation

```bash
git clone [https://github.com/jackylawck/EnterpriseDemo-OnboardingQuiz.git](https://github.com/jackylawck/EnterpriseDemo-OnboardingQuiz.git)
cd EnterpriseDemo-OnboardingQuiz
pip install -r requirements.txt
streamlit run app.py
```

### 2. 設定機密環境變數 / Configure `.streamlit/secrets.toml`

請於本機 `.streamlit/secrets.toml` 或 Streamlit Community Cloud 後台設定以下參數（**切勿將實際密碼提交至 Git**）：  
*Configure the variables below in `.streamlit/secrets.toml` or Streamlit Cloud Secrets (**never commit credentials to Git**):*

```toml
# 1. 員工通行碼 / Internal Access Passcode
ACCESS_CODE = "your_demo_passcode"

# 2. HR 接收電郵 / HR Destination Mailbox
HR_RECEIVER = "hr@example.com"

# 3. 郵件伺服器設定 (M365 SMTP STARTTLS) / SMTP Server Settings
SMTP_SERVER = "smtp.office365.com"
SMTP_PORT = 587
SENDER_EMAIL = "system@example.com"
SENDER_PASSWORD = "your_smtp_app_password"

# 4. 受控題庫 JSON（支援 single / multiple / group_single 三種題型）
QUESTIONS_JSON = '''[
  {
    "id": 1,
    "type": "single",
    "question": "1. 企業核心管治原則為何？",
    "options": ["誠信合規 (Integrity)", "僅追求速度", "無須紀錄"],
    "answer": ["誠信合規 (Integrity)"]
  },
  {
    "id": 2,
    "type": "multiple",
    "question": "2. 以下哪些屬於資訊安全日常守則？（每項 1 分）",
    "options": ["離開座位鎖定螢幕", "啟用雙重驗證 (MFA)", "將密碼貼在螢幕上"],
    "answer": ["離開座位鎖定螢幕", "啟用雙重驗證 (MFA)"]
  },
  {
    "id": 3,
    "type": "group_single",
    "question": "3. 請為以下事項配對負責部門：",
    "sub_questions": [
      {
        "sub_id": "3_1",
        "label": "入職培訓紀錄與假期查詢",
        "options": ["請選擇", "人力資源組", "會計組"],
        "answer": "人力資源組"
      }
    ]
  }
]'''
```

---

## ⚠️ 免責聲明 / Disclaimer

本專案為展示企業級人力資源數位化與零資料留存架構而設之通用示範（Enterprise Demo），所有受控編號（`DEMO-HR-REC-2026-V1`）、電郵端點及測試資料均為脫敏佔位符。

*This repository is a generic enterprise demo created for HR governance and zero-data-retention architectural showcase. All document IDs (`DEMO-HR-REC-2026-V1`), email endpoints, and sample payloads are sanitized placeholders.*

