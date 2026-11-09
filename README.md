
```
  ____      _               _                 _  _ _ 
 / ___|   _| |__   ___ _ __| | __ _ _ __   __| |(_|_)
| |  | | | | '_ \ / _ \ '__| |/ _` | '_ \ / _` || | |
| |__| |_| | |_) |  __/ |  | | (_| | | | | (_| || | |
 \____\__, |_.__/ \___|_|  |_|\__,_|_| |_|\__,_|/ |_|
      |___/                                   |__/   
```

# Hey, I'm Yohan 👋

## Security Analyst — SOC & Detection Engineering

*Malware traffic investigations · endpoint detection on Elastic · detection rules under automated tests*

[![ISC2 CC](https://img.shields.io/badge/ISC2-Certified%20in%20Cybersecurity-00a651?style=for-the-badge&logo=isc2&logoColor=white)](https://www.credly.com/badges/12c8d4ce-3e75-4b4b-a603-6a03796f0d9b/public_url)
[![CASA](https://img.shields.io/badge/APIsec-CASA-blue?style=for-the-badge)](https://www.credly.com/badges/71cbe68b-112e-444f-a7b9-d8241f8773ae/public_url)
[![Security+](https://img.shields.io/badge/CompTIA-Security%2B%20(in%20progress)-e4002b?style=for-the-badge&logo=comptia&logoColor=white)](https://www.comptia.org/certifications/security)

---

I investigate malicious network and endpoint activity and turn what I find into detection rules that are tested automatically. Everything here is built in my own labs and documented, including what didn't work.

### At a glance

- 🔬 **4 real-world malware investigations** from network captures, mapped to MITRE ATT&CK
- ⚒️ **38 Suricata rules under CI validation** — the badge below is the live state, not a screenshot
- 🔮 **Elastic SIEM + EDR lab** — an 11-step Lumma Stealer chain emulated and traced through endpoint and SIEM evidence
- 🌐 **SigmaHQ pull request** — [#6110](https://github.com/SigmaHQ/sigma/pull/6110), network-layer detection for NetSupport Manager RAT
- 💼 Cybersecurity internship (2026): cloud security architecture, GDPR and EU AI Act readiness
- 📍 Bremen, Germany — open to **Security Analyst, SOC and Detection Engineering** roles in DE · BE · LU · CH · French (native) · German · English

---

## 🛠️ Core Stack

![Suricata](https://img.shields.io/badge/Suricata-IDS%2FIPS-EF3B2D?style=flat-square)
![Sigma](https://img.shields.io/badge/Sigma-Detection%20Rules-008080?style=flat-square)
![EQL](https://img.shields.io/badge/EQL-Event%20Query%20Language-005571?style=flat-square)
![Zeek](https://img.shields.io/badge/Zeek-Network%20Security%20Monitor-2C6E9B?style=flat-square)
![Wireshark](https://img.shields.io/badge/Wireshark-PCAP%20Analysis-1679A7?style=flat-square)
![Elastic Stack](https://img.shields.io/badge/Elastic%20Stack-SIEM-005571?style=flat-square&logo=elastic&logoColor=white)
![Elastic Defend](https://img.shields.io/badge/Elastic%20Defend-EDR-FEC514?style=flat-square&logo=elastic&logoColor=black)
![Atomic Red Team](https://img.shields.io/badge/Atomic%20Red%20Team-Adversary%20Emulation-D22128?style=flat-square)
![MITRE ATT&CK](https://img.shields.io/badge/MITRE-ATT%26CK-red?style=flat-square)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-CI%2FCD-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![Python](https://img.shields.io/badge/Python-Harness%20%26%20Tooling-3776AB?style=flat-square&logo=python&logoColor=white)

*Also used across the labs:* Snort · Graylog · Docker · WireGuard · Hetzner Cloud · Kali · Ubuntu/Debian · Windows 10 · Apache · rsyslog · Git · draw.io

---

## 🔬 Operation PCAP Autopsy — Malware Traffic Investigations

Each operation takes a capture of a real malware infection, reconstructs the attack chain, maps it to MITRE ATT&CK and produces validated Suricata rules. Zeek runs alongside as an independent cross-check of each investigation.

| Operation | Malware family | Suricata rules | Status |
|-----------|----------------|----------------|--------|
| [PA-01](https://github.com/cyberlandji/operation-pcap-autopsy/tree/main/pa-01-you-dirty-rat) | STRRAT | 3 | ✅ Complete |
| [PA-02](https://github.com/cyberlandji/operation-pcap-autopsy/tree/main/pa-02-lumma-in-the-room-ah) | Lumma Stealer | 12 (1 removed — ECH) | ✅ Complete |
| [PA-03](https://github.com/cyberlandji/operation-pcap-autopsy/tree/main/pa-03-the-ghost-in-the-wire) | GhostWeaver RAT | 16 | ✅ Complete |
| [PA-04](https://github.com/cyberlandji/operation-pcap-autopsy/tree/main/pa-04-easy-as-123) | NetSupport Manager RAT | 7 | ✅ Complete |

**38 Suricata rules** across 4 operations, all ported into The Forge and green in CI. Each operation also documents the behaviour that network data alone can't show — the starting point for the endpoint work in Prism Box.

---

## 🔮 Operation Prism Box — Elastic SIEM & EDR Lab

A cloud-hosted detection lab on a **WireGuard mesh**: **Elasticsearch + Kibana** with a **Fleet Server** managing **Elastic Defend** EDR on a **Windows 10 victim endpoint**. **Atomic Red Team** drives emulated attack chains; detection rules are written from the resulting telemetry.

| Phase | Focus | Status |
|-------|-------|--------|
| PB-01 | Elastic Stack + Fleet Server + Elastic Defend on a Windows victim (WireGuard mesh) | ✅ Complete |
| PB-02 | Detection engineering on Elastic — emulation campaigns, correlation, rule authoring | 🚧 Active |

### 🐦‍⬛ Magpie — Lumma Stealer, endpoint side

**Why Lumma:** in PCAP Autopsy (PA-02) the network traffic only showed part of the attack. Magpie rebuilds the same attack chain on an endpoint to see the behaviour from the process side.

- **11-step chain, pinned by atomic GUID** (not test index) so the run is reproducible.
- **All 11 steps correlated** across three independent sources — Atomic Red Team log, Windows Security event 4688 and Kibana's process entity — with the UTC/CEST offset reconciled.
- **Defender caught 2 of 11**, both at the delivery stage. Everything after the foothold passed the built-in antivirus — the gap custom rules exist to close.
- **4 SigmaHQ rules adapted** under DRL 1.1 (`related: derived`, original authors retained), converted to Elastic rules and **replay-validated 4/4 firing**.
- **Key finding:** two rules deployed as **Lucene** produced zero alerts although the events were present. Lucene's whitespace tokenisation breaks wildcard matching on command-line substrings with spaces. Rewriting them in **EQL** fixed both; the non-firing Lucene versions stay in the repo as evidence.
- **Scope:** the atomics are separate technique demonstrations, not an end-to-end data theft. The claim is *"each technique Lumma uses was emulated and its telemetry correlated"* — the exfiltration step sent synthetic data to a placeholder domain.

> Write-up: [`pb-02-detection-engineering/magpie`](https://github.com/cyberlandji/prism-box/tree/main/pb-02-detection-engineering/magpie)

---

## ⚒️ The Forge — Detection-as-Code Pipeline

[![CI](https://github.com/cyberlandji/the-forge/actions/workflows/suricata.yml/badge.svg)](https://github.com/cyberlandji/the-forge/actions/workflows/suricata.yml)

Every push lints all Suricata rules and replays them against the malware captures; the build fails if an expected detection doesn't fire. Each operation is tested in **both directions** — known-bad traffic the rules **must** catch, and known-good traffic they **must not** (false-positive guard).

| Operation | Detection | CI status |
|-----------|-----------|-----------|
| [PA-01](https://github.com/cyberlandji/the-forge/tree/main/suricata/operations/pa-01) — STRRAT | 3 Suricata · known-bad + known-good | 🟢 Validated |
| [PA-02](https://github.com/cyberlandji/the-forge/tree/main/suricata/operations/pa-02) — Lumma Stealer | 12 Suricata · known-bad + known-good | 🟢 Validated |
| [PA-03](https://github.com/cyberlandji/the-forge/tree/main/suricata/operations/pa-03) — GhostWeaver RAT | 16 Suricata · known-bad + known-good + benign-adversarial | 🟢 Validated |
| [PA-04](https://github.com/cyberlandji/the-forge/tree/main/suricata/operations/pa-04) — NetSupport Manager RAT | 7 Suricata · known-bad + known-good | 🟢 Validated |

---

## 🌐 Community Contribution — SigmaHQ

My first pull request to [SigmaHQ](https://github.com/SigmaHQ/sigma): a Zeek-based detection for **NetSupport Manager RAT cleartext C2 over port 443**, derived from the PA-04 investigation.

- **Rule:** `zeek_http_netsupport_manager_cleartext_c2.yml` → `rules/network/zeek/`
- **Logic:** `user_agent|startswith 'NetSupport Manager/'` **AND** `id.resp_p: 443`
- **Why it's not a duplicate:** existing SigmaHQ coverage for this RAT is host-based; this covers the network layer.
- **Validation:** fields checked against the real PA-04 Zeek `http.log` · `sigma-cli` clean · fires only on the malicious rows.

> 📬 Under maintainer review — [PR #6110](https://github.com/SigmaHQ/sigma/pull/6110)

---

## 🏗️ Operation Iron Watch — SOC Lab Series

Three labs, each building on the last: manual detection, then centralised log management, then a full DMZ architecture.

| Operation | Focus | Status |
|-----------|-------|--------|
| [IW01](https://github.com/cyberlandji/operation-iron-watch-01) | Foundational SOC — Snort IDS, manual correlation | ✅ Complete |
| [IW02](https://github.com/cyberlandji/operation-iron-watch-02) | Graylog log management — web enumeration detection, and an SSH compromise the setup could not see | ✅ Complete |
| [IW03](https://github.com/cyberlandji/operation-iron-watch-03) | DMZ hardening, full log pipeline, DDoS detection suite | ✅ Complete |

---

**Next:** Brood — behavioural EQL sequence detection in Prism Box · OT/ICS detection with Suricata (Modbus).

## 🔗 Contact

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Yohan%20Cédric%20Landji-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/yohan-cedric-landji)

*Everything I build lives here on GitHub — the repos above are the portfolio.*
