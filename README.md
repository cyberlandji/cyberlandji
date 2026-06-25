```
  ____      _               _                 _  _ _ 
 / ___|   _| |__   ___ _ __| | __ _ _ __   __| |(_|_)
| |  | | | | '_ \ / _ \ '__| |/ _` | '_ \ / _` || | |
| |__| |_| | |_) |  __/ |  | | (_| | | | | (_| || | |
 \____\__, |_.__/ \___|_|  |_|\__,_|_| |_|\__,_|/ |_|
      |___/                                   |__/   
```

# Hey, I'm Yohan 👋

## Blue Team Practitioner | Detection Engineering · SOC Operations

[![ISC2 CC](https://img.shields.io/badge/ISC2-Certified%20in%20Cybersecurity-00a651?style=for-the-badge&logo=isc2&logoColor=white)](https://www.credly.com/)
[![Security+](https://img.shields.io/badge/CompTIA-Security%2B%20(in%20progress)-e4002b?style=for-the-badge&logo=comptia&logoColor=white)](https://www.comptia.org/certifications/security)
[![CASA](https://img.shields.io/badge/APISec-CASA-blue?style=for-the-badge)](https://university.apisec.ai/)

---

I design, build, and validate detection systems — from architecture to alert.

Most of my work is **hands-on**: I build lab environments, write detection rules from real-world traffic, and document everything — including failures. My focus is understanding how attacks actually look in network data and how to detect them before the attacker gains a foothold. Lately I've been turning that craft into a **Detection-as-Code pipeline** — detection rules under continuous validation in CI, where every change re-proves the whole corpus still works.

---

## 🛠️ Tools & Technologies

![Suricata](https://img.shields.io/badge/Suricata-IDS%2FIPS-EF3B2D?style=flat-square)
![Sigma](https://img.shields.io/badge/Sigma-Detection%20Rules-008080?style=flat-square)
![Graylog](https://img.shields.io/badge/Graylog-SIEM-FF3633?style=flat-square)
![Wireshark](https://img.shields.io/badge/Wireshark-PCAP%20Analysis-1679A7?style=flat-square)
![Snort](https://img.shields.io/badge/Snort-IDS-EF3B2D?style=flat-square)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-CI%2FCD-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![Python](https://img.shields.io/badge/Python-Harness%20%26%20Tooling-3776AB?style=flat-square&logo=python&logoColor=white)
![Git](https://img.shields.io/badge/Git-Version%20Control-F05032?style=flat-square&logo=git&logoColor=white)
![Kali Linux](https://img.shields.io/badge/Kali-Linux-557C94?style=flat-square&logo=kalilinux&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-Ubuntu%20%7C%20Debian-FCC624?style=flat-square&logo=linux&logoColor=black)
![Apache](https://img.shields.io/badge/Apache-Web%20Server-D22128?style=flat-square&logo=apache&logoColor=white)
![rsyslog](https://img.shields.io/badge/rsyslog-Log%20Pipeline-green?style=flat-square)
![MITRE ATT&CK](https://img.shields.io/badge/MITRE-ATT%26CK-red?style=flat-square)
![draw.io](https://img.shields.io/badge/draw.io-Architecture-orange?style=flat-square)

---

## ⚒️ The Forge — Detection-as-Code (Live CI/CD Pipeline)

[![CI](https://github.com/cyberlandji/the-forge/actions/workflows/suricata.yml/badge.svg)](https://github.com/cyberlandji/the-forge/actions/workflows/suricata.yml)
![Status](https://img.shields.io/badge/status-●%20LIVE-brightgreen?style=flat-square)

A **living** lab, not a finished one. Detection rules ported into a Git CI/CD pipeline and held under **continuous validation** — every push re-runs the harness against *every* operation, so the green check is a standing claim that the entire corpus still works, right now. This is where I practice Detection Engineering as an engineering discipline: hermetic test fixtures, regression detection, version control.

Each operation is validated in **both directions** — a known-bad fixture that the rules **must fire** on, and a crafted known-good fixture that they **must not fire** on (false-positive guard). The badge above is the real CI state.

| Operation | Detection | CI Status |
|-----------|-----------|-----------|
| [PA-01](https://github.com/cyberlandji/the-forge/tree/main/suricata/operations/pa-01) — You Dirty Rat! (STRRAT) | 3 Suricata · known-bad + known-good | 🟢 Validated |
| PA-02 — Lumma in the Room-ah (Lumma Stealer) | 13 Suricata | 🔜 Porting |
| PA-03 — The Ghost in the Wire (GhostWeaver RAT) | 16 Suricata | 🔜 Porting |
| PA-04 — Easy as 123 (NetSupport Manager RAT) | 7 Suricata | 🔜 Porting |

> Tracks grow over time: Suricata first, then the Sigma track once endpoint telemetry is online, and OT/ICS rules from Operation Ground Truth. The lab is designed to keep growing and stay green.

---

## 🔬 Operation PCAP Autopsy — Detection Rule Development & Network Forensics

PCAP-based investigation series. Each operation analyzes real-world malware traffic, reconstructs the attack chain, and produces validated Suricata detection rules.

| Operation | Title | Malware Family | Rules | Status |
|-----------|-------|---------------|-------|--------|
| [PA-01](https://github.com/cyberlandji/operation-pcap-autopsy/tree/main/pa-01-you-dirty-rat) | You Dirty Rat! | STRRAT | 3 Suricata | ✅ Complete |
| [PA-02](https://github.com/cyberlandji/operation-pcap-autopsy/tree/main/pa-02-lumma-in-the-room-ah) | Lumma in the Room-ah | Lumma Stealer | 13 Suricata | ✅ Complete |
| [PA-03](https://github.com/cyberlandji/operation-pcap-autopsy/tree/main/pa-03-the-ghost-in-the-wire) | The Ghost in the Wire | GhostWeaver RAT | 16 Suricata + 3 Sigma | ✅ Complete |
| [PA-04](https://github.com/cyberlandji/operation-pcap-autopsy/tree/main/pa-04-easy-as-123) | Easy as 123 | NetSupport Manager RAT | 7 Suricata + 1 Sigma | ✅ Complete |

**39 Suricata rules** validated across 4 operations. 4 Sigma rules identified and deferred to Operation Prism Box. These operations are now being ported into **The Forge** for continuous validation.

---

## 🏗️ Operation Iron Watch — SOC Architecture & Detection Labs

A three-part SOC lab series. Each operation builds on the last: from manual detection to SIEM to full DMZ architecture with proactive defense.

| Operation | Focus | Status |
|-----------|-------|--------|
| [IW01](https://github.com/cyberlandji/operation-iron-watch-01) | Foundational SOC — Snort IDS, manual correlation | ✅ Complete |
| [IW02](https://github.com/cyberlandji/operation-iron-watch-02) | Graylog SIEM — web enumeration detection, SSH compromise invisible | ✅ Complete |
| [IW03](https://github.com/cyberlandji/operation-iron-watch-03) | DMZ hardening, full log pipeline, DDoS Detection Suite | ✅ Complete |

---

## 🔮 Operation Prism Box — SIEM + EDR + Detection Correlation (Coming Soon)

Elastic Stack SIEM + Suricata IDS/IPS + Elastic Defend EDR + Atomic Red Team + Shuffle SOAR. Proactive detection methodology — writing Sigma + Suricata rules from simulated attack scenarios with cross-telemetry correlation.

| Phase | Focus | Status |
|-------|-------|--------|
| PB-01 | Elastic Stack install + EDR implementation | 🔜 Planned |
| PB-02 | Atomic Red Team attack scenarios, Sigma + Suricata rule development | 🔜 Planned |
| PB-03 | Hardening, full detection suite, Shuffle SOAR + playbook automation | 🔜 Planned |

---

## 🏭 Operation Ground Truth — OT/ICS Detection (Next Build)

Industrial protocol detection in an OT/ICS context — Modbus / DNP3 behavioral rules with Suricata, framed against **IEC 62443** and **KRITIS**. Bringing detection engineering to the operational-technology side, where the traffic and the threat model look nothing like enterprise IT.

> 🔜 In design — next on the anvil.

---

## 🔗 Links

[![Portfolio](https://img.shields.io/badge/Portfolio-cyberlandji.com-000000?style=for-the-badge&logo=google-chrome&logoColor=white)](https://www.cyberlandji.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Yohan%20Cédric%20Landji-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/yohan-cedric-landji)
[![GitHub](https://img.shields.io/badge/GitHub-cyberlandji-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/cyberlandji)

---

*I design, build, and validate detection systems — from architecture to alert.*
