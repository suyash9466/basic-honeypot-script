---

# Admin Honeypot Logger & Blocker

## Overview

This project is a **Python-based honeypot system** designed to simulate an admin login panel and monitor malicious login attempts. It captures attacker behavior, enriches it with GeoIP data, and automatically blocks repeated offenders using **Windows Firewall**.

The tool is useful for **intrusion detection, threat intelligence collection, and digital forensics analysis**.

---

## Features

* **Login Attempt Logging**

  * Captures username, IP address, user-agent, and timestamp

* **GeoIP Enrichment**

  * Uses MaxMind GeoLite2 database to resolve attacker location

* **Brute-force Detection**

  * Tracks repeated login attempts per IP

* **Automatic IP Blocking**

  * Blocks suspicious IPs via Windows Firewall after threshold breach

* **SQLite Storage**

  * Persistent logging of all attack data

* **Security Alerting**

  * Writes alerts to log files for monitoring and analysis

---

## Tech Stack

* **Language:** Python

* **Database:** SQLite

* **Libraries:**

  * `sqlite3` – database handling
  * `geoip2` – GeoIP lookup
  * `logging` – event logging
  * `subprocess` / `os` – firewall rule execution

* **External Dependency:**

  * MaxMind GeoLite2-City database

---

## Project Structure

```id="b9l2r4"
honeypot-script/
├── honeypot.py              # Main honeypot script
├── requirements.txt         # Dependencies
├── README.md                # Documentation
├── geoip/
│   └── GeoLite2-City.mmdb   # GeoIP database (manual download)
└── logs/
    ├── admin/
    │   └── alerts.log       # Security alerts
    └── admin_attacks.db     # SQLite database (auto-created)
```

---

## Installation

1. Clone the repository:

```bash id="j4n3qk"
git clone https://github.com/your-username/honeypot-script.git
cd honeypot-script
```

2. Install dependencies:

```bash id="c7l0pm"
pip install -r requirements.txt
```

3. Download GeoLite2 database:

* Go to: [https://dev.maxmind.com/geoip/geolite2-free-geolocation-data/](https://dev.maxmind.com/geoip/geolite2-free-geolocation-data/)
* Place `GeoLite2-City.mmdb` inside `/geoip/`

---

## Usage

Run the honeypot script:

```bash id="9m8wsa"
python honeypot.py
```

The script will:

* Monitor fake admin login attempts
* Log attacker details
* Automatically block malicious IPs

---

## How It Works

1. Simulates an **admin login endpoint**

2. Captures incoming login attempts

3. Extracts:

   * IP address
   * Username
   * User-Agent

4. Performs:

   * GeoIP lookup
   * Attempt frequency tracking

5. If threshold exceeded:

   * Adds firewall rule to block IP

6. Stores all data in SQLite and logs alerts

---

## Security Use Cases

* Honeypot deployment for research
* Brute-force attack detection
* Threat intelligence collection
* Digital forensics logging
* Blue team monitoring setups

---

## Disclaimer

This tool is intended for:

* Educational purposes
* Authorized security research

Do not deploy on public infrastructure without proper controls.

---

## Limitations

* Windows-only firewall blocking
* No distributed logging (single system)
* Basic threshold-based detection
* No real-time dashboard

---

## Future Improvements

* Web dashboard for monitoring
* Visualization of attack patterns
* Cloud logging integration (ELK / SIEM)
* ML-based anomaly detection
* Integration with IDS/IPS systems

---

## Author

**Suyash Khare**
Cybersecurity & Forensics Student

---
