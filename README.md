```
  ____      _               _                 _  _ _ 
 / ___|   _| |__   ___ _ __| | __ _ _ __   __| |(_|_)
| |  | | | | '_ \ / _ \ '__| |/ _` | '_ \ / _` || | |
| |__| |_| | |_) |  __/ |  | | (_| | | | | (_| || | |
 \____\__, |_.__/ \___|_|  |_|\__,_|_| |_|\__,_|/ |_|
      |___/                                   |__/   
```

# Hey, I'm Yohan 👋

## Blue Team Practitioner — Detection Engineering

*Detection-as-code pipelines · SOC & purple-team labs · writing quality Sigma/Suricata rules to share*

[![ISC2 CC](https://img.shields.io/badge/ISC2-Certified%20in%20Cybersecurity-00a651?style=for-the-badge&logo=isc2&logoColor=white)](https://www.credly.com/)
[![Security+](https://img.shields.io/badge/CompTIA-Security%2B%20(in%20progress)-e4002b?style=for-the-badge&logo=comptia&logoColor=white)](https://www.comptia.org/certifications/security)
[![CASA](https://img.shields.io/badge/APISec-CASA-blue?style=for-the-badge)](https://university.apisec.ai/)

---

I design, build, and validate detection systems — from architecture to alert.

Most of my work is **hands-on**: I build lab environments, write detection rules from real-world traffic, and document everything — including failures. My focus is understanding how attacks actually look in **network and endpoint data** and how to detect them before the attacker gains a foothold. Lately I've been turning that craft into a **Detection-as-Code pipeline** — detection rules under continuous validation in CI, where every change re-proves the whole corpus still works.

---

## 🛠️ Tools & Technologies

![Suricata](https://img.shields.io/badge/Suricata-IDS%2FIPS-EF3B2D?style=flat-square)
![Sigma](https://img.shields.io/badge/Sigma-Detection%20Rules-008080?style=flat-square)
![Zeek](https://img.shields.io/badge/Zeek-Network%20Security%20Monitor-2C6E9B?style=flat-square)
![Snort](https://img.shields.io/badge/Snort-IDS-EF3B2D?style=flat-square)
![Wireshark](https://img.shields.io/badge/Wireshark-PCAP%20Analysis-1679A7?style=flat-square)
![Elastic Stack](https://img.shields.io/badge/Elastic%20Stack-SIEM-005571?style=flat-square&logo=elastic&logoColor=white)
![Elastic Defend](https://img.shields.io/badge/Elastic%20Defend-EDR-FEC514?style=flat-square&logo=elastic&logoColor=black)
![Graylog](https://img.shields.io/badge/Graylog-Log%20Management-FF3633?style=flat-square)
![Atomic Red Team](https://img.shields.io/badge/Atomic%20Red%20Team-Adversary%20Emulation-D22128?style=flat-square)
![MITRE ATT&CK](https://img.shields.io/badge/MITRE-ATT%26CK-red?style=flat-square)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-CI%2FCD-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![Python](https://img.shields.io/badge/Python-Harness%20%26%20Tooling-3776AB?style=flat-square&logo=python&logoColor=white)
![Git](https://img.shields.io/badge/Git-Version%20Control-F05032?style=flat-square&logo=git&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-Containers-2496ED?style=flat-square&logo=docker&logoColor=white)
![WireGuard](https://img.shields.io/badge/WireGuard-VPN%20Mesh-88171A?style=flat-square&logo=wireguard&logoColor=white)
![Hetzner](https://img.shields.io/badge/Hetzner-Cloud%20Host-D50C2D?style=flat-square&logo=hetzner&logoColor=white)
![Kali Linux](https://img.shields.io/badge/Kali-Linux-557C94?style=flat-square&logo=kalilinux&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-Ubuntu%20%7C%20Debian-FCC624?style=flat-square&logo=linux&logoColor=black)
![Windows](https://img.shields.io/badge/Windows%2010-Victim%20Endpoint-0078D6?style=flat-square&logo=windows&logoColor=white)
![Raspberry Pi](https://img.shields.io/badge/Raspberry%20Pi%203B%2B-Iron%20Watch%20Lab-C51A4A?style=flat-square&logo=raspberrypi&logoColor=white)
![Apache](https://img.shields.io/badge/Apache-Web%20Server-D22128?style=flat-square&logo=apache&logoColor=white)
![rsyslog](https://img.shields.io/badge/rsyslog-Log%20Pipeline-green?style=flat-square)
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
| [PA-02](https://github.com/cyberlandji/the-forge/tree/main/suricata/operations/pa-02) — Lumma in the Room-ah (Lumma Stealer) | 12 Suricata (1 removed — ECH) · known-bad + known-good | 🟢 Validated |
| [PA-03](https://github.com/cyberlandji/the-forge/tree/main/suricata/operations/pa-03) — The Ghost in the Wire (GhostWeaver RAT) | 16 Suricata · known-bad + known-good + benign-adversarial | 🟢 Validated |
| [PA-04](https://github.com/cyberlandji/the-forge/tree/main/suricata/operations/pa-04) — Easy as 123 (NetSupport Manager RAT) | 7 Suricata · known-bad + known-good | 🟢 Validated |

> All four PCAP Autopsy operations are ported and green — **38 Suricata rules under continuous validation**. Tracks grow from here: the **Sigma track** comes online now that endpoint telemetry is live (Operation Prism Box), then OT/ICS rules from Operation Ground Truth. The lab is designed to keep growing and stay green.

---

## 🔮 Operation Prism Box — SIEM + EDR + Detection Correlation

A cloud-hosted, living detection lab on a **WireGuard mesh**: an **Elastic Stack** brain (Elasticsearch + Kibana) with a **Fleet Server** managing **Elastic Defend** EDR on a **Windows 10 victim endpoint**, correlated against **Suricata / Zeek** network telemetry. **Atomic Red Team** drives simulated attack chains; detection rules (**Sigma + Suricata**) are written from the resulting telemetry and cross-correlated across the network and endpoint layers — then hardened and automated with **Shuffle SOAR**.

| Phase | Focus | Status |
|-------|-------|--------|
| PB-01 | Elastic Stack brain + Fleet Server + Elastic Defend EDR on Windows victim (WireGuard mesh) | ✅ Complete |
| PB-02 | Atomic Red Team campaigns · Sigma + Suricata rule development · network↔endpoint correlation | 🚧 In progress |
| PB-03 | Hardening · full detection suite · Shuffle SOAR + playbook automation | 🔜 Planned |

> Repo: [github.com/cyberlandji/prism-box](https://github.com/cyberlandji/prism-box)
>
> *A Microsoft-stack mirror (Defender for Endpoint + Sentinel, KQL translation) is a longer-term goal — decoupled from this arc, not a direct successor to PB-03.*

---

## 🔬 Operation PCAP Autopsy — Detection Rule Development & Network Forensics

PCAP-based investigation series. Each operation analyzes real-world malware traffic, reconstructs the attack chain, and produces validated Suricata detection rules. Zeek runs alongside as a known-answer calibration layer, auditing and sharpening the investigation methodology.

| Operation | Title | Malware Family | Rules | Status |
|-----------|-------|---------------|-------|--------|
| [PA-01](https://github.com/cyberlandji/operation-pcap-autopsy/tree/main/pa-01-you-dirty-rat) | You Dirty Rat! | STRRAT | 3 Suricata | ✅ Complete |
| [PA-02](https://github.com/cyberlandji/operation-pcap-autopsy/tree/main/pa-02-lumma-in-the-room-ah) | Lumma in the Room-ah | Lumma Stealer | 12 Suricata (1 removed — ECH) | ✅ Complete |
| [PA-03](https://github.com/cyberlandji/operation-pcap-autopsy/tree/main/pa-03-the-ghost-in-the-wire) | The Ghost in the Wire | GhostWeaver RAT | 16 Suricata + 3 Sigma | ✅ Complete |
| [PA-04](https://github.com/cyberlandji/operation-pcap-autopsy/tree/main/pa-04-easy-as-123) | Easy as 123 | NetSupport Manager RAT | 7 Suricata + 1 Sigma | ✅ Complete |

**38 Suricata rules** validated across 4 operations. 4 Sigma rules identified and deferred to Operation Prism Box. These operations are now ported into **The Forge** for continuous validation — all four green in CI.

---

## 🌐 Community Contribution — SigmaHQ

Giving back to the ruleset I learn from. My **first pull request to [SigmaHQ](https://github.com/SigmaHQ/sigma)** — a Zeek-based detection for **NetSupport Manager RAT cleartext C2 over port 443**, derived directly from the PA-04 network forensics.

- **Rule:** `zeek_http_netsupport_manager_cleartext_c2.yml` → `rules/network/zeek/`
- **Logic:** `user_agent|startswith 'NetSupport Manager/'` **AND** `id.resp_p: 443`
- **Why it's non-duplicate:** existing SigmaHQ coverage for this RAT is host-based; this fills the **network-layer** gap.
- **Validation:** fields confirmed against real PA-04 Zeek `http.log` · `sigma-cli` clean (0 errors) · logic tested to fire only on malicious rows.

> 📬 Submitted and currently under maintainer review — [PR #6110](https://github.com/SigmaHQ/sigma/pull/6110).

---

## 🏗️ Operation Iron Watch — SOC Architecture & Detection Labs

A three-part SOC lab series. Each operation builds on the last: from manual detection to centralized log management to full DMZ architecture with proactive defense.

| Operation | Focus | Status |
|-----------|-------|--------|
| [IW01](https://github.com/cyberlandji/operation-iron-watch-01) | Foundational SOC — Snort IDS, manual correlation | ✅ Complete |
| [IW02](https://github.com/cyberlandji/operation-iron-watch-02) | Graylog log management — web enumeration detection, SSH compromise invisible | ✅ Complete |
| [IW03](https://github.com/cyberlandji/operation-iron-watch-03) | DMZ hardening, full log pipeline, DDoS Detection Suite | ✅ Complete |

---

## 🏭 Operation Ground Truth — OT/ICS Detection (Next Build)

Industrial protocol detection in an OT/ICS context — Modbus / DNP3 behavioral rules with Suricata, framed against **IEC 62443** and **KRITIS**. Bringing detection engineering to the operational-technology side, where the traffic and the threat model look nothing like enterprise IT.

> 🔜 In design — next on the anvil.

---

## 🔗 Links

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Yohan%20Cédric%20Landji-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/yohan-cedric-landji)
[![GitHub](https://img.shields.io/badge/GitHub-cyberlandji-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/cyberlandji)

---

*I design, build, and validate detection systems — from architecture to alert.*
