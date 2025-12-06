# RedCalibur 🗡️

> "Forged at the intersection of artificial intelligence and offensive cybersecurity."

**RedCalibur** is a professional, AI-powered red teaming toolkit designed to automate and enhance various phases of penetration testing, with a primary focus on comprehensive OSINT (Open Source Intelligence) reconnaissance. It leverages machine learning and large language models (LLMs) to supercharge ethical hacking workflows.

This project serves both as a practical cybersecurity tool and as a demonstration of applying neural networks and AI in cybersecurity for academic purposes.

---
## 🚀 Quickstart (cloned repo)
       
Prerequisites
- Python 3.10+ (3.11/3.12/3.13 supported)
- Node.js 18+ and npm

1) Clone and enter the folder
```bash
git clone https://github.com/PraneeshRV/RedCalibur.git
cd RedCalibur
```

2) Create and activate a virtual environment, install deps
```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -U pip setuptools wheel
python -m pip install -r requirements.txt
python -m pip install -r api/requirements.txt
```

3) Configure environment variables (optional but recommended)
```bash
cp .env.example .env
# edit .env and add keys as needed: SHODAN_API_KEY, VIRUSTOTAL_API_KEY, GEMINI_API_KEY
```

4) Start the backend API (runs in background)
```bash
chmod +x scripts/*.sh
./scripts/start_api.sh
# Health check: http://127.0.0.1:8000/health
```

5) Start the frontend (development)
```bash
cd frontend
npm install
npm run dev
# App: http://localhost:5173 (Vite may choose 5174 if 5173 is busy)
```

Stop the backend
```bash
./scripts/stop_api.sh
```

Optional: run tests
```bash
python -m pytest tests/
```

---
## ⚔️ Features

RedCalibur integrates traditional red teaming techniques with modern AI, offering a wide array of capabilities.

### 🌐 Core OSINT Capabilities
* **Domain & Infrastructure Analysis**:
    * **WHOIS Lookup**: Comprehensive domain registration information.
    * **DNS Enumeration**: Discovery of A, AAAA, MX, TXT, CNAME, and NS records.
    * **Subdomain Discovery**: Automated enumeration using multiple techniques.
    * **SSL/TLS Analysis**: Certificate details and security configuration assessment.
    * **Port Scanning**: Intelligent scanning for open ports and services.
* **Threat Intelligence Integration**:
    * **Shodan**: Discover internet-facing devices, services, and vulnerabilities.
    * **VirusTotal**: Analyze domains and IPs for known malicious activity.
* **Search & Data Mining**:
    * **Google Dorking**: Automate advanced search queries to find sensitive information.
    * **Leak Detection**: Search Pastebin and GitHub for potential data leaks (placeholder).
    * **Dark Web Mentions**: Search for mentions on the dark web (placeholder).

### 🕵️ Advanced OSINT Capabilities
* **Image & File OSINT**:
    * **EXIF Metadata Extraction**: Extract hidden data from images.
    * **Document Metadata Analysis**: Analyze metadata from PDF documents.
    * **Reverse Image Search**: Find where an image appears online (placeholder).
* **Social Media Reconnaissance**:
  * **Username Footprinting**: Multi-platform probes via direct HTTP checks (no external CLI required).
    * **LinkedIn Scraping**: Scrape company and employee data (placeholder).
    * **Twitter OSINT**: Analyze user data and activity (placeholder).

### 🧠 AI-Enhanced Features
* **AI-Powered Phishing Detection**:
    * **Custom Neural Networks**: A PyTorch-based classifier for URL and feature analysis.
    * **Ensemble Methods**: Combines a Random Forest and Neural Network for improved accuracy and robustness.
    * **Advanced Feature Engineering**: Extracts over 10 features from URLs, including Shannon entropy and domain structure, for precise analysis.
* **Intelligent Analysis & Reporting**:
    * **LLM Integration**: Leverages large language models (e.g., Gemini) for contextual understanding and summarization.
    * **Automated Risk Scoring**: AI-driven assessment to prioritize findings.
    * **Professional Report Generation**: Automatically create summary reports in PDF and JSON formats.
---

## 🏗️ Architecture

```
RedCalibur/
├── redcalibur/
│   ├── ai_core/                  # Core AI and LLM integration
│   ├── cli.py                    # Main CLI interface
│   ├── config.py                 # Configuration and environment loading
│   ├── osint/
│   │   ├── ai_enhanced/          # AI-powered summarization, risk scoring, reporting
│   │   ├── domain_infrastructure/ # WHOIS, DNS, subdomains, SSL, tech stack, etc.
│   │   ├── image_file_osint/     # EXIF, document metadata, reverse image search
│   │   ├── network_threat_intel/ # Shodan, vuln scan, ASN, passive DNS
│   │   ├── search_engine_data_mining/ # Google dorking, dark web, leak search
│   │   ├── social_media_recon/   # Twitter, LinkedIn, Facebook/Instagram OSINT
│   │   ├── user_identity/        # Username, email, phone, breach lookups
│   │   └── virustotal_integration.py # VirusTotal API integration
│   ├── phishing_detection/       # AI phishing detection models
│   ├── prompt_injection/         # LLM security testing (future)
│   ├── payload_generation/       # AI payload creation (future)
│   ├── reconnaissance/           # AI-powered recon (future)
│   └── reporting/                # (Reserved for future reporting modules)
├── models/                       # Saved AI models
├── data/                         # Training datasets
├── reports/                      # Output reports (PDF, JSON, Markdown)
├── README.md
├── requirements.txt
└── test.py                       # Component testing
```
---

## ⚡ Running the Project

```bash
# Quick demo
.venv/bin/python demo.py phishing --simple

# Test all components
.venv/bin/python test.py

# Custom URL analysis
.venv/bin/python demo.py phishing --url "your-url-here"
```

The toolkit is now ready for demonstration, testing, and further development for your AI and Neural Networks coursework!

---
## 📦 Installation

### Quick Install
```bash
git clone https://github.com/PraneeshRV/RedCalibur.git
cd RedCalibur
pip install -e .
```

### Production Install
```bash
pip install redcalibur
```

### Environment Setup
```bash
# Create virtual environment (recommended)
python -m venv redcalibur-env
source redcalibur-env/bin/activate  # Linux/Mac
# redcalibur-env\Scripts\activate  # Windows

# Install dependencies
pip install -r requirements.txt
```

## ⚙️ Configuration

### Environment Variables
Use `.env` at the project root (copy from `.env.example`). Keys are optional but enable richer results.

Core keys used by the current API/UI
- SHODAN_API_KEY: Enables Shodan enrichment on network scan
- VIRUSTOTAL_API_KEY: Enables full URL malware scanning; without it, a basic URL health check is used
- GEMINI_API_KEY: Enables AI summarization of recon data (Google Generative AI)

Additional optional variables in `.env.example` are for future/extended tooling (e.g., Hunter.io, OpenAI/Anthropic); they are not required to run the local UI and core flows.

### Configuration Check
```bash
redcalibur config --check
redcalibur config --show
```

## 🎯 Usage

### Command Line Interface

#### Domain Reconnaissance
```bash
# Complete domain analysis
redcalibur domain --target example.com --all

# Specific checks
redcalibur domain --target example.com --whois --dns --ssl
redcalibur domain --target example.com --subdomains
```

#### Network Scanning
```bash
# Port scanning
redcalibur scan --target 192.168.1.1 --ports 80,443,22,21

# Shodan integration
redcalibur scan --target example.com --shodan
```

#### Username Intelligence
```bash
# Multi-platform username lookup
redcalibur username --target johndoe --platforms twitter,linkedin,github

# All supported platforms
redcalibur username --target johndoe
```

#### URL Scanning
```bash
# Scan a URL for malicious activity using VirusTotal
redcalibur urlscan --url http://example.com
```

#### File-Based OSINT
```bash
# Extract metadata from a PDF document
redcalibur file-osint extract-doc-meta --path /path/to/document.pdf

# Extract EXIF data from an image
redcalibur file-osint extract-exif --path /path/to/image.jpg
```

#### All-in-One Command
```bash
# Run all functionalities and generate a summary report
redcalibur all --target-domain example.com --target-ip 192.168.1.1 --username johndoe --platforms twitter,linkedin --output summary_report
```

#### Automated Reconnaissance
```bash
# Fully automated, interactive OSINT process
redcalibur auto-recon
```

#### Report Generation
```bash
# Generate comprehensive reports
redcalibur report --input results.json --format pdf
redcalibur report --input results.json --format both --output custom_name
```

## 📊 Sample Output

```json
{
  "target": "example.com",
  "timestamp": "2025-09-08T01:48:00",
  "whois": {
    "registrar": "Example Registrar",
    "creation_date": "2000-01-01",
    "expiration_date": "2026-01-01"
  },
  "dns": {
    "A": ["93.184.216.34"],
    "MX": ["mail.example.com"]
  },
  "ssl": {
    "issuer": "DigiCert Inc",
    "notAfter": "2025-12-31",
    "subjectAltName": ["example.com", "www.example.com"]
  },
  "ai_summary": "Target shows standard configuration with valid SSL certificate expiring in 2025...",
  "risk_score": 0.3
}
```
### Development Setup
```bash
git clone https://github.com/PraneeshRV/RedCalibur.git
cd RedCalibur
python -m venv dev-env
source dev-env/bin/activate
pip install -e ".[dev]"
```

### Running Tests
```bash
python -m pytest tests/
```


## 🛡️ Security & Ethics

### Responsible Use
- **Educational Purpose**: Designed for security professionals and researchers
- **Legal Compliance**: Ensure you have proper authorization before testing
- **Ethical Guidelines**: Follow responsible disclosure practices
- **Rate Limiting**: Built-in delays to respect target systems

### Disclaimer
⚠️ **IMPORTANT**: This toolkit is for educational and authorized testing purposes only. Unauthorized use against systems you do not own or have explicit permission to test is illegal and unethical.

## 🤝 Contributing

We welcome contributions!

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🔗 Links
- **Issues**: [Bug Reports](https://github.com/PraneeshRV/RedCalibur/issues)
- **Discussions**: [Community](https://github.com/PraneeshRV/RedCalibur/discussions)

## 🙏 Acknowledgments

- Inspired by the cybersecurity community
- Built with modern AI/ML technologies
- Designed for the next generation of security professionals

---

**RedCalibur** - *Forging the future of automated red teaming* ⚔️
 
---

## 🌐 Web UI (FastAPI + React)

This repository includes a lightweight API server and a modern React dashboard.

### Backend API
1) Copy `.env.example` to `.env` and fill keys as needed (optional).
2) Install deps (see Quickstart above) and run:

Dev (foreground, auto-reload):
```bash
python -m api.run
```

Background (recommended local service):
```bash
chmod +x scripts/*.sh
./scripts/start_api.sh
# Stop with: ./scripts/stop_api.sh
```

API default: http://127.0.0.1:8000 (health: `/health`).

### Frontend
In a second terminal:

```bash
cd frontend
npm install
npm run dev
```

App is served at http://localhost:5173 (or 5174) and proxies `/api/*` to http://127.0.0.1:8000 in development.

### UI Highlights
- Neon-red cyber theme, accessible contrast, responsive layout
- Domain recon (WHOIS, DNS, subdomains, SSL), AI summary and basic risk score
- Network scan with optional Shodan enrichment
- Username lookup (direct HTTP probes; no Sherlock dependency)
- URL malware scan (VirusTotal)

Note: Keys are optional. Shodan and VirusTotal enrich results when provided. Gemini powers AI summaries.

### Optional: systemd service (Linux)
If you prefer the backend to run automatically on boot:

1) Review and, if needed, edit `deploy/systemd/redcalibur.service` paths.
2) Install and enable the service:
```bash
sudo cp deploy/systemd/redcalibur.service /etc/systemd/system/
sudo systemctl daemon-reload
sudo systemctl enable redcalibur
sudo systemctl start redcalibur
```
3) Check status and logs:
```bash
systemctl status redcalibur --no-pager
journalctl -u redcalibur -n 100 --no-pager
```

### Troubleshooting
- Backend health check: http://127.0.0.1:8000/health
- Frontend can’t reach API in dev: ensure the backend is running and Vite proxy is active
- Port conflicts: Vite will choose another port (5174) if 5173 is busy; change API port with `--port` in `api/run.py` if needed
- Scripts say venv missing: create the venv at `.venv` and install requirements (see Quickstart)
- Missing keys: the app will still run, but some features return reduced data
