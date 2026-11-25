# Perform-Gap-Analysis
* **Objective:** Perform a security gap analysis on a Windows Server 2019 system (`PC10`) by comparing its live configuration against a Microsoft Security Compliance Toolkit baseline using **Policy Analyzer**.
* **Environment & OS Verification:**
  * Logged into `PC10` as `.\admin` and verified the OS version via `winver` as **Windows Server 2019, Version 1809 (OS Build 17763.4377)** to match the required baseline templates.
* **Lab Setup & Extraction:**
  * Launched **Windows PowerShell** as Administrator and copied `PolicyAnalyzer.zip` and `Windows 10 Version 1809 and Windows Server 2019 Security Baseline.zip` from `D:\` to `C:\LABFILES`.
  * Extracted both archives using `Expand-Archive`, adjusted VM resolution to `1920x1080` for UI visibility, and launched `PolicyAnalyzer.exe`.
* **Baseline Inspection (`View / Compare`):**
  * Loaded the policy rules from `C:\LABFILES\Windows 10 Version 1809 and Windows Server 2019 Security Baseline\Documentation` and inspected **`MSFT-Win10-v1809-RS5-WS2019-FINAL`**:
    * `LockoutBadCount` baseline value: **`10`**
    * `MinimumPasswordLength` baseline value: **`14`**
* **Gap Analysis (`Compare to Effective State`):**
  * Compared the baseline template against `PC10`'s live effective state, revealing non-compliant settings highlighted in yellow:
    * `LockoutBadCount` effective state: **`0`** *(Non-compliant)*
    * `MinimumPasswordLength` effective state: **`7`** *(Non-compliant)*
  * **Compliance Verdict:** **No** — `PC10` fails to meet the baseline security requirements.
* **Key Takeaway:** Policy Analyzer streamlines configuration drift detection, though third-party security templates must always be tailored to match an organization's specific risk profile and business requirements.
