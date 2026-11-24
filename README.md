# 🦉 OStackX

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Linux-0a0c10?style=flat-square"/>
  <img src="https://img.shields.io/badge/Category-OScan-blue?style=flat-square"/>
  <img src="https://img.shields.io/badge/License-Proprietary-orange?style=flat-square"/>
  <img src="https://img.shields.io/badge/Part%20of-OwlSec%20Toolkit-7b5ea7?style=flat-square"/>
  <img src="https://img.shields.io/badge/Version-1.0.0-cyan?style=flat-square"/>
</p>

> **OStackX** — OpenStack Service Configuration Security Auditor

---

> ⚠️ **AUTHORISED USE ONLY** — Use only on systems you own or have explicit written permission to test. Unauthorised use is illegal.

---

## 📌 Overview


OStackX is an offline, read-only OpenStack service configuration security auditor covering Keystone, Nova, Neutron, Glance, Cinder and Horizon. It parses oslo.config INI files, a YAML subset and Horizon local_settings.py (via a safe AST reader, never exec), then applies OpenStack Security Guide checklists including file mode and ownership. Secrets are masked, each rule carries CWE and MITRE ATT&CK tags, and reports export to TXT, Markdown, JSON, CSV or SARIF.

---

## ✨ Features


- Stdlib oslo.config INI parser, YAML-subset parser and a safe AST reader for Horizon local_settings.py
- OpenStack Security Guide checklists for Identity, Compute, Networking, Image, Block Storage and Dashboard
- oslo.policy and clouds.yaml review plus file mode/ownership checks (0640 root:<svc>)
- Secrets masked everywhere, with --show-secrets available when explicitly required
- CWE + MITRE ATT&CK mapping per rule, with severity filtering and --fail-on CI gates
- Export to TXT, Markdown, JSON, CSV and SARIF 2.1.0, plus a --demo self-test

---

## ⚙️ Requirements

- **Linux**
- **No Python installation needed** — runs as a standalone executable

---

## 🚀 Usage


```bash
./OStackX --scan -f sarif -o openstack.sarif
./OStackX --keystone /etc/keystone/keystone.conf --nova /etc/nova/nova.conf
./OStackX -r /mnt/image --fail-on high --json
./OStackX --demo
./OStackX --help
```

---

## 📦 Part of OwlSec Toolkit

This tool is part of the **OwlSec** suite — a collection of 275+ security and privacy tools.

🔗 [owlsec.org](https://owlsec.org)

---

## ©️ License

Proprietary — © 2026 Owlsec LLC. All rights reserved.

*Tools are distributed as pre-built executables. Source code is proprietary.*

---

## 🔍 Verification & Transparency

This tool is closed-source. These files let you see exactly what is inside it,
without the source:

- [`SBOM.cdx.json`](SBOM.cdx.json) — CycloneDX inventory: SHA-256 of this
  binary, bundled CPython version, and every bundled library with its exact
  version and license. Feed it to Grype, Trivy or Dependency-Track to audit
  our dependencies for CVEs yourself.
- [`THIRD-PARTY-NOTICES.md`](THIRD-PARTY-NOTICES.md) — the full license text
  of every third-party component, extracted from this binary.

**No telemetry, no analytics, no licence check-in.** This tool does not phone
home. Verify that claim yourself:

```bash
sudo strace -f -e trace=network ./OStackX --help   # watch every network call
firejail --net=none ./OStackX --help               # deny the network entirely
```

Release signing, GPL compliance and vulnerability reporting:
[**TRUST.md**](https://github.com/owlsecx/owl-os/blob/main/TRUST.md)
