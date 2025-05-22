
# 🛡️ CyberScan

**AI-powered automated vulnerability scanner built using n8n + Nessus.**

CyberScan is a modular, open-source cybersecurity automation tool that simulates vulnerability scans, asset discovery, AI risk triage, and automated alerts for modern security teams and learners.

It is inspired by the NIST Cybersecurity Framework (CSF) and supports best practices outlined in current threat intelligence and vulnerability management white papers. CyberScan enables small-to-mid-sized organizations (SMEs) to build practical, AI-assisted detection and triage workflows aligned with real-world SOC operations — without relying on expensive commercial platforms.

Designed to foster learning, automation, and compliance-readiness, CyberScan demonstrates how structured risk evaluation and alerting can be codified into scalable n8n workflows.

---

## 🚀 Features

- 🔍 Network segment definition via environment configuration  
- 🤖 Simulated asset discovery and scan workflows  
- 📊 AI-based risk scoring and triage logic  
- 📧 Automated vulnerability alerting via email  
- 📄 Summary reports exported to Google Sheets  
- 🧱 Clean and extensible n8n JSON workflows  
- 🔐 Fully stripped of secrets and hardcoded infrastructure details  

---

## 🧠 Node Documentation

### 🌐 DISC – Initialize Network Segments
Defines network ranges to be scanned. Uses environment variable:

```env
NETWORK_SEGMENTS=["192.168.1.0/24", "10.0.0.0/24"]
````

---

### 🧪 AI – Process Assets

Simulates internal asset discovery using placeholder asset data:

```json
[
  { "id": "asset-001", "ipAddress": "10.0.0.1", "hostName": "host-a" },
  { "id": "asset-002", "ipAddress": "10.0.0.2", "hostName": "host-b" }
]
```

---

### 🧠 AI – Risk Evaluation

Evaluates vulnerabilities and assigns AI Risk Score + LEV path.
Logic only, no static inputs.

---

### 📍 AI – Triage Vulnerabilities

Classifies vulnerabilities into self-healing, expert-review, or monitor groups.
No sensitive data.

---

### 🚨 ALERT – LEV Trigger

Detects critical vulnerabilities (AI Risk ≥ 8).
Condition only, fully safe.

---

### 📊 UTILS – Field Editor

Adds timestamped group counts.
Pure logic, no sensitive content.

---

### 🧮 Code

Unpacks summary data for report/export formatting.
Safe to publish.

---

### 📝 Summary Node

Generates formatted HTML vulnerability report.
No tokens, IPs, or PII exposed.

---

### 📧 Security Team Alert

Sends HTML alert emails to internal teams using this format:

```html
🔔 Critical Vulnerability Alert  
Triggered by: {{ $workflow.name }}  
Timestamp: {{ new Date().toISOString() }}
```

---

### 📤 EXPORT – Save to Sheet

Appends summary to Google Sheets with fields:

* timestamp
* self
* expert
* monitor
* total
* maxLEV
* topCVE

---

### 📬 Send Email

Sends full HTML vulnerability report to team inbox. Uses environment variables:

```env
EMAIL_FROM=your_sender@example.com  
EMAIL_TO=security_team@example.com
```

---

## 🛠️ Setup

1. **Clone the repository**
2. Create a `.env` file in your local environment:

```env
NESSUS_USER=your_nessus_username  
NESSUS_PASS=your_nessus_password  
NESSUS_API_URL=https://your-nessus-server:8834  
NESSUS_SCAN_UUID=your-template-id  
NETWORK_SEGMENTS=["192.168.1.0/24", "10.0.0.0/24"]  
EMAIL_FROM=your_sender@example.com  
EMAIL_TO=security_team@example.com
```

3. Import `CyberScan_n8n.json` into your n8n instance
4. Connect:

   * Google Sheets credential
   * SMTP email credential

---

## 🔐 Security Notes

* No IPs, tokens, usernames, or secrets are included in the workflow
* Environment variables are used for all sensitive config
* `.env.example` is provided for guidance

---

## 📂 Project Structure

```
CyberScan/
├── workflows/
│   └── CyberScan_n8n.json
├── .env.example
├── LICENSE
└── README.md
```

---

## 🤝 Contributing

Fork this repo to adapt it to your environment. PRs are welcome for logic improvements, integrations, or optimizations.

---

## 🔧 Built With

* [n8n](https://n8n.io)
* [Tenable Nessus](https://www.tenable.com/products/nessus)
* JavaScript (Node Functions)

---

## 📬 Contact

📧 [cyberpulse.solutions41@gmail.com](mailto:cyberpulse.solutions41@gmail.com) (placeholder)

🔗 Project by Adnan Tariq – CyberPulse

---

© 2025 CyberPulse | MIT License

```
