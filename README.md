# 📝 企業級新員工入職培訓考核及問卷系統 (Enterprise Demo)
# Enterprise Onboarding Assessment & Feedback System (Demo)

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](#)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Compliance: ISO 27001](https://img.shields.io/badge/Compliance-ISO%2027001-green.svg)](SECURITY_COMPLIANCE.md)
[![Privacy: Privacy-by-Design](https://img.shields.io/badge/Privacy-Privacy--by--Design-brightgreen.svg)](PRIVACY_POLICY.md)

---

## 🌐 項目簡介 / System Overview

**(中文)**  
**EnterpriseDemo-OnboardingQuiz** 是一個基於 Streamlit 開發的獨立企業級 Web 系統示範 (Demo)。本系統為企業展示如何整合「入職培訓考核測驗」、「培訓滿意度評估」及「員工興趣調查」，並能即時動態繪製受控繁體中文 PDF 報告 (`DEMO-HR-REC-2026-V1`)。員工完成後只需一鍵點擊，後端即透過 Python SMTP 自動將報告及 PDF 附件直接加密寄送至 HR 部門，實現完全無紙化與零資料滯留的自動化管治。

**(English)**  
**EnterpriseDemo-OnboardingQuiz** is a standalone, enterprise-grade web application demo built with Streamlit. This system demonstrates how to integrate "Onboarding Knowledge Quizzes," "Training Satisfaction Surveys," and "Employee Engagement Surveys" into a seamless workflow. It dynamically generates an IMS-controlled PDF report (`DEMO-HR-REC-2026-V1`). With a single click, the backend automatically dispatches the report and PDF attachment directly to the HR department via Python SMTP (TLS), achieving a fully paperless and zero-data-retention automated governance process.

---

## 🛠️ 核心特色 / Key Features

- **全自動一鍵後端提交 (One-Click Automated Email Submission via SMTP)**
  - *中文*：員工完成測驗與問卷後，點擊按鈕即可由後端自動打包 PDF 報告並直接以電郵發送至 HR，無需開啟任何外部郵件軟體。
  - *English*：Users simply click a button upon completion, and the backend automatically bundles the PDF report and sends it directly to HR via email, without launching any external email clients.
  
- **機密題庫後端隔離保護 (Secure Secrets Management)**
  - *中文*：題目、正確答案及敏感驗證金鑰完全儲存於 Streamlit Secrets 後端，前端不暴露任何題庫代碼與評分邏輯。
  - *English*：Questions, answer keys, and sensitive access tokens are strictly encapsulated within Streamlit Secrets. The frontend source code exposes no grading logic or internal questionnaires.

- **即時自動評分機制 (Real-time Automated Grading)**
  - *中文*：支援單選、多選及條款配對題，提交後即時動態計算得分狀態。
  - *English*：Supports single-choice, multiple-choice, and matching questions with real-time dynamic scoring and pass/fail evaluation upon submission.

- **合規受控 PDF 報告生成 (Compliant IMS Controlled PDF Generation)**
  - *中文*：整合個人資料、答題成績、滿意度分數及開放式建議，即時繪製成標準向量 PDF 文件，符合 ISO 文件審計要求。
  - *English*：Integrates personal info, quiz scores, survey results, and open-ended feedback into a standard vector PDF document instantly, fulfilling ISO document auditing requirements.

- **跨平台響應式體驗 (Responsive Mobile & Desktop Friendly)**
  - *中文*：完美適應電腦寫字樓環境與手機流動端操作，問卷滑塊、多選框與版面自動對齊。
  - *English*：Optimized for both desktop workstations and mobile touch devices, ensuring a seamless user experience across all form controls and sliders.

---

## 🚀 系統流程 / Application Workflow

```text
[1. 登入 / Login] ➔ [2. 考核測驗 / Quiz] ➔ [3. 滿意度調查 / Survey] ➔ [4. 一鍵發送 / Submit & Download]

```

1. **登入驗證 (Access Verification)**
* 透過 URL Key 或手動輸入員工通行碼進入系統。
* Authenticate via URL parameters or manual passcode entry.


2. **第一部分：入職培訓測驗 (Part I: Onboarding Quiz)**
* 填寫基本資料，完成規章制度測驗並勾選誠信聲明。
* Fill in basic details, complete compliance questions, and acknowledge the integrity declaration.


3. **第二部分：問卷及興趣調查 (Part II: Feedback & Engagement Survey)**
* 檢視測驗即時得分，填寫滿意度評估、活動愛好及開放式建議。
* Review quiz scores instantly, and provide feedback on training satisfaction and corporate engagement.


4. **第三部分：一鍵提交與備份 (Part III: Submit & Archiving)**
* 點擊 **「🚀 一鍵自動送出報告」**，後端即時打包 PDF 報告並寄送給 HR。
* 提供 **「💾 下載 PDF 報告」** 供員工自行備份。
* Click the submit button to dispatch the PDF via the backend, and optionally download a local backup.



---

## ⚙️ 環境變數設定 / Secrets Configuration (`.streamlit/secrets.toml`)

**(中文)** 請在本地端 `.streamlit` 資料夾下或雲端部署平台 (如 Streamlit Community Cloud) 設定以下 Secrets。**切勿將此檔案上傳至 GitHub！**

**(English)** Please configure the following variables in your `.streamlit/secrets.toml` locally or in your cloud deployment platform's secrets management. **DO NOT commit this file to version control!**

```toml
# 1. 員工通行碼 (自訂內部驗證密鑰) / Custom Access Passcode
ACCESS_CODE = "your_demo_passcode"

# 2. HR 接收電郵 / HR Destination Email
HR_RECEIVER = "hr@example.com"

# 3. 郵件伺服器與寄件帳號設定 (M365 SMTP 範例) / SMTP Configuration
SMTP_SERVER = "smtp.office365.com"
SMTP_PORT = 587
SENDER_EMAIL = "system@example.com"
SENDER_PASSWORD = "your_smtp_app_password"

# 4. 完整題庫 JSON (字串格式) / Encapsulated Quiz JSON
QUESTIONS_JSON = '''[
  {
    "id": 1,
    "type": "single",
    "question": "1. 企業核心價值為何？ (What is our core value?)",
    "options": ["Integrity", "Profit", "Speed"],
    "answer": ["Integrity"]
  }
]'''

```

---

## 📄 文件與數據規範 / Document Standards & Compliance

* **管控編號 (Document ID)**: `DEMO-HR-REC-2026-V1`
* **合規標準 (Compliance Frameworks)**:
* 本系統展示之架構設計符合 **零資料滯留 (Privacy-by-Design)** 原則。
* 符合 **ISO/IEC 27001** 資訊安全架構之存取隔離與傳輸加密精神。
* The architecture is designed to comply with Privacy-by-Design principles and ISO/IEC 27001 information security standards regarding data transmission and secrets isolation.

