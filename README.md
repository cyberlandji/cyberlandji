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

*Detection-as-code pipelines · SOC & purple-team labs · network & endpoint detection engineering*

[![ISC2 CC](https://img.shields.io/badge/ISC2-Certified%20in%20Cybersecurity-00a651?style=for-the-badge&logo=isc2&logoColor=white)](https://www.credly.com/)
[![Security+](https://img.shields.io/badge/CompTIA-Security%2B%20(in%20progress)-e4002b?style=for-the-badge&logo=comptia&logoColor=white)](https://www.comptia.org/certifications/security)
[![CASA](https://img.shields.io/badge/APISec-CASA-blue?style=for-the-badge)](https://university.apisec.ai/)

---

I design, build, and validate detection systems — from architecture to alert.

Most of my work is **hands-on**: I build lab environments, write detection rules from real-world traffic and real endpoint telemetry, and document everything — including failures. My focus is understanding how attacks actually look in **network and endpoint data** and how to detect them before the attacker gains a foothold. Lately I've been turning that craft into a **Detection-as-Code pipeline** — detection rules under continuous validation in CI, where every change re-proves the whole corpus still works.

### At a glance

- ⚒️ **38 Suricata rules under continuous CI validation** — the badge below is live state, not a screenshot
- 🔮 **Elastic detection lab running** — EDR + SIEM on a WireGuard mesh; emulated campaigns correlated node-by-node, rules deployed and replay-validated
- 🌐 **First SigmaHQ pull request open** — [#6110](https://github.com/SigmaHQ/sigma/pull/6110), filling a network-layer gap in existing RAT coverage
- 🗂️ Work is organised as **named operations** — *Iron Watch* (SOC architecture) · *PCAP Autopsy* (network forensics) · *The Forge* (detection-as-code CI) · *Prism Box* (endpoint detection engineering) · *Ground Truth* (OT/ICS, next)
- 📍 Bremen, Germany — open to **Detection Engineering / SOC** roles in DE · BE · CH · LU · French (native) · German · English · reach me on [LinkedIn](https://www.linkedin.com/in/yohan-cedric-landji)

---

## 🛠️ Core Stack

![Suricata](https://img.shields.io/badge/Suricata-IDS%2FIPS-EF3B2D?style=flat-square)
![Sigma](https://img.shields.io/badge/Sigma-Detection%20Rules-008080?style=flat-square)
![EQL](https://img.shields.io/badge/EQL-Event%20Query%20Language-005571?style=flat-square)
![Zeek](https://img.shields.io/badge/Zeek-Network%20Security%20Monitor-2C6E9B?style=flat-square)
![Wireshark](https://img.shields.io/badge/Wireshark-PCAP%20Analysis-1679A7?style=flat-square)
![Elastic Stack](https://img.shields.io/badge/Elastic%20Stack-SIEM-005571?style=flat-square&logo=elastic&logoColor=white)
![Elastic Defend](https://img.shields.io/badge/Elastic%20Defend-EDR-FEC514?style=flat-square&logo=elastic&logoColor=black)
![Sysmon](https://img.shields.io/badge/Sysmon-Endpoint%20Telemetry-0078D6?style=flat-square)
![Atomic Red Team](https://img.shields.io/badge/Atomic%20Red%20Team-Adversary%20Emulation-D22128?style=flat-square)
![MITRE ATT&CK](https://img.shields.io/badge/MITRE-ATT%26CK-red?style=flat-square)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-CI%2FCD-2088FF?style=flat-square&logo=githubactions&logoColor=white)
![Python](https://img.shields.io/badge/Python-Harness%20%26%20Tooling-3776AB?style=flat-square&logo=python&logoColor=white)

*Also used across the labs:* Snort · Graylog · Docker · WireGuard · Hetzner Cloud · Kali · Ubuntu/Debian · Windows 10 · Apache · rsyslog · Git · draw.io

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

> All four PCAP Autopsy operations are ported and green — **38 Suricata rules under continuous validation**. Next intake: the **Sigma track**, now that endpoint telemetry is live and Operation Prism Box has surfaced the coverage gaps worth authoring from scratch — followed by OT/ICS rules from Operation Ground Truth. The lab is designed to keep growing and stay green.

---

## 🔮 Operation Prism Box — SIEM + EDR + Detection Correlation

A cloud-hosted, living detection lab on a **WireGuard mesh**: an **Elastic Stack** brain (Elasticsearch + Kibana) with a **Fleet Server** managing **Elastic Defend** EDR on a **Windows 10 victim endpoint**, correlated against **Suricata / Zeek** network telemetry. **Atomic Red Team** drives emulated attack chains; detection rules are written from the resulting telemetry and cross-correlated across the network and endpoint layers — then hardened and automated with **Shuffle SOAR**.

| Phase | Focus | Status |
|-------|-------|--------|
| PB-01 | Elastic Stack brain + Fleet Server + Elastic Defend EDR on Windows victim (WireGuard mesh) | ✅ Complete |
| PB-02 | Detection engineering on Elastic — emulation campaigns, correlation, rule authoring | 🚧 Active |
| PB-03 | Hardening · full detection suite · Shuffle SOAR + playbook automation | 🔜 Planned |

### PB-02 — Campaigns

PB-02 is my detection-engineering home on the Elastic stack. Campaigns are deliberately laddered: each one has to prove a **different tier of detection craft**, not just add more coverage.

| Campaign | Emulates | Detection tier | Status |
|----------|----------|----------------|--------|
| [**Magpie**](https://github.com/cyberlandji/prism-box/tree/main/pb-02-detection-engineering/magpie) | Lumma Stealer — 11-node chain, Atomic Red Team | **Signature** — single-event Sigma → Elastic (Lucene / EQL) | ✅ Complete |
| **Brood** | DBatLoader / ModiLoader | **Behavioural** — multi-event ancestry correlation, hand-authored EQL sequences | 🔜 Next |

**🐦‍⬛ Magpie — complete.** An 11-node Lumma Stealer kill chain, **pinned by atomic GUID** (not test index) so the run is actually reproducible, detonated on the victim endpoint and then correlated node-by-node against ground truth.

- **All 11 nodes correlated** — endpoint evidence, SIEM evidence, and timeline reconciled independently per technique (Kibana in UTC vs. victim in CEST — a standing +2h reconciliation).
- **4 Sigma rules adapted from SigmaHQ** under DRL 1.1 (`related: derived`, original authors retained), converted to Elastic detection rules, deployed to Kibana and **replay-validated 4/4 firing**.
- **Defender caught 2 of 11** — both at the delivery/transfer stage. Everything after the foothold passed the NGAV tier untouched, which is exactly the gap custom rules exist to close.
- **Headline finding:** two rules deployed as **Lucene** produced zero alerts despite the events being present. Root cause — Lucene's whitespace tokenisation breaks wildcard matching on **space-bearing command-line substrings**. Re-converting to **EQL** fixed both. The non-firing Lucene versions are kept in the repo on purpose, as evidence.
- **Honest scoping:** the atomics are discrete TTP demonstrations, not an end-to-end data flow — the exfil node shipped synthetic data to a placeholder domain. The claim is *"each TTP Lumma uses was emulated and its telemetry correlated,"* not *"credentials were stolen and exfiltrated end-to-end."*

**🥚 Brood — next on the bench.** Where Magpie detects *events*, Brood detects *relationships*. The thesis: express well-known parent/child abuse as **true two-step EQL sequences** (`sequence by … with maxspan=…`, ancestry join, derived time window) instead of the single-event `ParentImage` shortcut most rules settle for. Sigma can't cleanly express sequences — so Brood is authored directly in EQL, by design.

- **Campaign: DBatLoader / ModiLoader** — chosen because it's ancestry-native: multi-stage BAT / JS / PowerShell chains, a **signed legitimate binary used as the malicious parent** via DLL side-loading, plus LOLBin abuse.
- Single-host by design — the name is the scope guardrail. No lateral movement, no AD.
- Status: campaign and method locked, awaiting clean baseline reset and detonation.

> Repo: [github.com/cyberlandji/prism-box](https://github.com/cyberlandji/prism-box) — detection work lives in [`pb-02-detection-engineering/`](https://github.com/cyberlandji/prism-box/tree/main/pb-02-detection-engineering)
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

**38 Suricata rules** validated across 4 operations, all four ported into **The Forge** and green in CI. The 4 Sigma rules identified during these autopsies are **still open** — network-layer, single-event signature work, parked in PB-02 alongside the campaign output rather than lost in a backlog.

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

## 🔗 Contact

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Yohan%20Cédric%20Landji-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/yohan-cedric-landji)

*Everything I build lives here on GitHub — the repos above are the portfolio.*

---

*I design, build, and validate detection systems — from architecture to alert.*
