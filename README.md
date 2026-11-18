# Nicholas Michael Kloster

**Independent Security Researcher · AI Red Teaming Specialist · CVE Author · Critical Infrastructure Operator · U.S. Army Infantry Veteran (SSG)**

Specializing in enterprise network security appliances, identity management platforms, industrial control systems, and AI/LLM offensive security. I break LLMs and the infrastructure around them, write findings to vendor-grade standards, and ship the tools I use. Disclosure-first.

This profile documents zero-day vulnerability disclosures, vendor hardening defect advisories, AI red team research, priority emergency telecommunications administration, CISA ICS/OT training, ITDRC deployments, DC3 cyber coursework, FEMA certifications, and military leadership.

[![Medium](https://img.shields.io/badge/Medium-@NicholasKloster-black?logo=medium)](https://medium.com/@NicholasKloster)
[![Web](https://img.shields.io/badge/Web-nuclide--research.com-blue)](https://nuclide-research.com)

---

## Selected Disclosures

- **Anthropic — Claude 4.6 Jailbreak.** Public disclosure of "Ambiguity Front-Loading," a behavioral jailbreak affecting Opus 4.6, Sonnet 4.6, and Haiku 4.5. Threat model, reproduction, mitigations. → [Repo](https://github.com/Nicholas-Kloster/claude-4.6-jailbreak-vulnerability-disclosure-unredacted)
- **CISA / CVE-2025-4364 (CVSS 8.7).** Unauthenticated remote access in Assured Telematics fleet management. Federal advisory ICSA-25-140-11. → [CISA Advisory](https://www.cisa.gov/news-events/ics-advisories/icsa-25-140-11)
- **Amazon RXVM.** Reverse-engineered the client-side bot detection bytecode VM. Extracted embedded neural network. Decrypted RC4 cookies. Confirmed by Amazon. → [Repo](https://github.com/Nicholas-Kloster/RXVM)
- **Google VRP.** Sandbox escape. Confirmed.
- **30+** more findings across HackerOne, Bugcrowd, and CERT/CC-coordinated channels — fintech, crypto, KYC/IDV, AI SaaS, ICS.

---

## Assigned CVEs & ICS Advisories

| Reference | Product | Vulnerability Title | CVSS |
| --- | --- | --- | --- |
| [CVE-2026-76420](https://sec.cloudapps.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-fmc2-multivulns-HXgcqRG) | Cisco Secure FMC | Peer Impersonation | 9.0 Critical |
| [CVE-2025-4364](https://www.cisa.gov/news-events/ics-advisories/icsa-25-140-11) | Assured Telematics FMS | Information Exposure | 8.7 High |
| [CVE-2026-76412](https://sec.cloudapps.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-fmc2-multivulns-HXgcqRG) | Cisco Secure FMC | Root Privilege Escalation | 8.5 High |
| [CVE-2026-76413](https://sec.cloudapps.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-fmc2-multivulns-HXgcqRG) | Cisco Secure FMC | SSO Token Forgery | 8.5 High |
| [CVE-2026-76447](https://sec.cloudapps.cisco.com/security/center/content/CiscoSecurityAdvisory/cisco-sa-ise-multiauth-bypass-sgD2HbL4) | Cisco ISE | OCSP Authentication Bypass | 5.3 Medium |
| [CVE-2026-20241](https://www.cisco.com/c/en/us/support/docs/csa/cisco-sa-ise-cert-mE9BD5GO.html) | Cisco ISE and ISE-PIC | Authorization Bypass | 5.3 Medium |

**Technical Breakdown of CVE Disclosures**

* **CVE-2026-76420 (CSCwu27279):** Improper authorization when the sftunnel connection to FTD is down allows unauthenticated remote attackers to execute arbitrary commands as root and control FMC REST APIs.
* **CVE-2025-4364 (ICSA-25-140-11):** Unauthenticated remote exposure of sensitive system data in Transportation Systems critical infrastructure enables attackers to harvest sensitive files and administrative credentials.
* **CVE-2026-76412 (CSCwu12566):** Multistage privilege escalation flaw in Cisco Secure FMC Software allows authenticated low-privilege users to elevate permissions to root regardless of device configuration.
* **CVE-2026-76413 (CSCwu16965):** Authentication flaw in Cisco Secure FMC Single Sign-On handling permits unauthenticated remote attackers to forge SSO tokens and disrupt account availability and integrity.
* **CVE-2026-76447 (cisco-sa-ise-multiauth-bypass-sgD2HbL4):** Missing authentication in the Cisco ISE and ISE-PIC OCSP responder lets unauthenticated remote attackers trigger certificate and key reloads on demand.
* **CVE-2026-20241 (cisco-sa-ise-cert-mE9BD5GO):** Improper authorization checks in Cisco ISE and ISE-PIC allow unauthenticated remote attackers to send crafted requests and obtain unauthorized endpoint identity certificates.

---

## Vendor Hardening & Security Defect Disclosures

Beyond formal CVE assignments, the following architectural vulnerabilities were reported to Cisco and remediated across Cisco Identity Services Engine releases to harden service bindings, credential storage, and certificate lifecycle management:

| Defect ID | Component | Issue Title | Resolution Track |
| --- | --- | --- | --- |
| CSCww29079 | ISE SQL Schema | Hardcoded Oracle Credentials | Account removal |
| CSCwu43439 | ISE SSE Connector | Unauthenticated API Binding | Port binding restriction |
| CSCww36036 | ISE SSE Connector | All-Interfaces and Expired CA | Certificate removal |
| CSCww36081 | ISE CA Tomcat Server | Default Tomcat Shutdown | HTTP server hardening |

**Technical Breakdown of Hardening Defects**

* **CSCww29079:** Identified hardcoded Oracle database credentials embedded within the Cisco ISE SQL schema across all configurations, prompting the removal of static database accounts.
* **CSCwu43439:** Discovered that the Cisco ISE SSE Connector management API bound to all network interfaces without client authentication under default configurations, resulting in service port restrictions.
* **CSCww36036:** Uncovered an exposed SSE Connector configuration combining all-interface binding, push command execution settings, and an expired CA certificate.
* **CSCww36081:** Reported an exposed default Apache Tomcat shutdown configuration within the Cisco ISE Certificate Authority service, driving HTTP server hardening updates.

---

## Tools I Built

| Tool | What it is |
|---|---|
| [**aimap**](https://github.com/Nicholas-Kloster/aimap) | Go scanner for AI/ML infrastructure. 23+ service fingerprints — LLM runtimes, vector databases, agent frameworks. BlackArch-packaged. |
| [**BARE**](https://github.com/Nicholas-Kloster/BARE) | Single Rust binary. BERT encoder + 3,904 pre-encoded Metasploit modules. Runs offline in SCIFs and air-gapped networks. |
| [**AI-LLM-Infrastructure-OSINT**](https://github.com/Nicholas-Kloster/AI-LLM-Infrastructure-OSINT) | Verified Shodan and Censys queries for vector DBs, MCP servers, RAG stacks, model-serving endpoints, GPU compute. |
| [**Cortex**](https://github.com/Nicholas-Kloster/cortex-framework) | LLM API auth-boundary analyzer. Detects authentication boundary violations and authorization drift. |
| [**rag-pipeline-demo**](https://github.com/Nicholas-Kloster/rag-pipeline-demo) | Live four-stage RAG pipeline. Reverse-engineered the claude.ai artifact sandbox to make it work. |
| [**recongraph**](https://github.com/Nicholas-Kloster/recongraph) | Seed-polymorphic reconnaissance engine with environmental contamination detection. |
| [**RXVM**](https://github.com/Nicholas-Kloster/RXVM) | Amazon bot detection RE toolkit. Bytecode VM disassembler, neural network extraction, RC4 decryption. |

## Open Source & Research Projects

| Project | Description |
| --- | --- |
| [ablation](https://github.com/Ablation-Tool/ablation) | AI-assisted reverse engineering (AIARE) framework |
| [kevlar](https://github.com/Ablation-Tool/kevlar) | Proxy firewall & security layer for Model Context Protocol |
| [cerotto](https://github.com/Ablation-Tool/cerotto) | AI-assisted digital forensics tool built on the Graphics Environment Manager |
| [graphics-environment-manager](https://github.com/Ablation-Tool/graphics-environment-manager) | Graphics Environment Manager |
| [next-token-predictability](https://github.com/Ablation-Tool/next-token-predictability) | Metric for measuring the shape of a language model's next-token decision before a token is selected |
| [Zoe-Autonomy](https://github.com/Ablation-Tool/Zoe-Autonomy) | Zoe Autonomy: a self-governing measurement–action architecture |
| [research-papers](https://github.com/Ablation-Tool/research-papers) | Complete Autonomy, Accessible Volume, and Zoe research paper collection with PDFs, LaTeX sources, and reproduction archives |
| [pdf-signature-toolkit](https://github.com/Ablation-Tool/pdf-signature-toolkit) | Reproducible LaTeX source integrity records and PKCS #7 detached PDF signatures |
| [brain-gem](https://github.com/Ablation-Tool/brain-gem) | Standalone Bayesian field notebook with deterministic and stochastic chambers and hash-chained memory |
| [gem-helen](https://github.com/Ablation-Tool/gem-helen) | Optimized native geometry and forecast laboratory |
| [Chalkboard](https://github.com/Ablation-Tool/Chalkboard) | Ideas, templates, and prompts — free for anyone to take and use |

## Other Work

- [**safeconvert**](https://github.com/Nicholas-Kloster/safeconvert) — Covert domestic-violence resource PWA disguised as a unit converter.
- [**nuclide-instruments**](https://github.com/Nicholas-Kloster/nuclide-instruments) — Audio-visual instruments built with Tone.js + Canvas.
- [**nuclide-labs**](https://github.com/Nicholas-Kloster/nuclide-labs) — Interactive security education — cell tower data exposure, traffic analysis, privacy field guide.
- Poetry under the name **Savio**.

---

## Critical Infrastructure, Emergency Communications & Disaster Response

* **Louisiana GETS/WPS Program Administrator (2021–2023):** Directed Louisiana's Government Emergency Telecommunications Service (GETS) and Wireless Priority Service (WPS) program for all military users, managing priority telecommunications provisioning and issuing GETS/WPS cards.
* **Information Technology Disaster Resource Center (ITDRC):** Volunteered from 2020 through 2024 providing mission-critical IT infrastructure, emergency communications, and disaster recovery support to affected communities.
* **CISA Critical Infrastructure Authorization:** Authorized by the Cybersecurity and Infrastructure Security Agency (CISA) to perform secure infrastructure operations, technical recovery, and resilience hardening on critical systems.

---

## CISA Industrial Control Systems & Operational Technology (ICS/OT) Training

Completed the CISA and Idaho National Laboratory (INL) Industrial Control Systems and Operational Technology cybersecurity training curriculum across five operational domains:

| Domain | Course Code | Course Title | Issuing Agency |
| --- | --- | --- | --- |
| General | 100W | ICS Cybersecurity Practices | DHS / CISA / INL |
| General | FRE2115 | ICS Cybersecurity Landscape for Managers | DHS / CISA / INL |
| OT/ICS Fundamentals | 210W-01 | Differences in Deployments of ICS | DHS / CISA / INL |
| OT/ICS Fundamentals | 210W-02 | Influence of IT Components on ICS | DHS / CISA / INL |
| OT/ICS Fundamentals | 210W-03 | Common ICS Components | DHS / CISA / INL |
| OT/ICS Fundamentals | 210W-04 | Cybersecurity Within IT and ICS Domains | DHS / CISA / INL |
| Risk | 210W-05 | ICS Cybersecurity Risk | DHS / CISA / INL |
| Risk | 210W-07 | ICS Cybersecurity Vulnerabilities | DHS / CISA / INL |
| Risk | 210W-08 | ICS Cybersecurity Consequences | DHS / CISA / INL |
| Risk | 401 | ICS Cybersecurity Evaluation | DHS / CISA / INL |
| Attacker Perspective | 210W-06 | ICS Cybersecurity Threats | DHS / CISA / INL |
| Attacker Perspective | 210W-09 | Attack Methodologies in IT & ICS | DHS / CISA / INL |
| Defense | 210W-10 | Mapping IT Defense-In-Depth Security Solutions to ICS – Part I | DHS / CISA / INL |
| Defense | 210W-11 | Mapping IT Defense-In-Depth Security Solutions to ICS – Part II | DHS / CISA / INL |

---

## Federal, DoD & Industry Cybersecurity Certifications

| Credential or Course | Issuing Organization | Date | Hours / CEUs |
| --- | --- | --- | --- |
| Control Systems Security Master Professional | Industrial Cybersecurity Certification | Active | Verified |
| Ethical Hacking Essentials (EHE) | EC-Council / Published Credential | Dec 2024 | Verified |
| CENG 003 AI Foundations for the DoD | Defense Acquisition University | Sep 2024 | Self-paced |
| CCYB 002A DoD Cybersecurity Workforce Overview | Defense Acquisition University | Sep 2024 | Self-paced |
| Software Cost Estimation | Defense Acquisition University | 2024 | Self-paced |
| Cross-Sector Cybersecurity Performance Goals | DHS / CISA / INL | May 2024 | 3 hrs / 0.3 CEUs |
| Industrial Security Basics | DHS / CISA | Jan 2024 | Verified |
| CompTIA Network+ (N10-007) | U.S. Army CECOM, Augusta, GA | Mar 2023 | 80 hrs |
| 210W-07 ICS Cybersecurity Vulnerabilities | DHS / CISA | Feb 2023 | 2 hrs / 0.2 CEUs |
| ICSJWG Session 2: ICS Communication Basics | DHS / CISA / INL | Feb 2023 | 1 hr / 0.1 CEUs |
| Network Security for Homes and Small Businesses | TEEX / DHS / FEMA | Feb 2022 | Verified |
| Intro to Information Sharing and Analysis Orgs | NCPC / Norwich / DHS / FEMA | Feb 2022 | 2 hrs |
| Detecting and Responding to a Cyber Attack | TEEX / DHS / FEMA | Feb 2022 | 4 hrs / 0.4 CEUs |
| Secure Software | TEEX / DHS / FEMA | Feb 2022 | 9 hrs / 0.9 CEUs |
| Critical Infrastructure Protection | DHS / CISA | Feb 2022 | 2 hrs |

---

## FEMA Emergency Management Institute (EMI) Certifications

Completed 22 Independent Study certifications through the Federal Emergency Management Agency (FEMA) Emergency Management Institute covering incident command, public alert systems, hazardous materials, and supply chain resilience:

| Course Code | Course Title | Completion Date | CEUs |
| --- | --- | --- | --- |
| IS-00245.b | Introduction to the Federal Priorities and Allocations System | Oct 4, 2024 | 0.10 |
| IS-00018.24 | FEMA EEO Employee Course 2024 | Feb 15, 2024 | 0.10 |
| IS-00021.24 | Civil Rights and FEMA Disaster Assistance 2024 | Feb 15, 2024 | 0.10 |
| IS-00037.24 | Managerial Safety and Health 2024 | Feb 15, 2024 | 0.20 |
| IS-00075 | Military Resources in Emergency Management | Feb 15, 2024 | 0.20 |
| IS-00240.c | Leadership and Influence | Feb 15, 2024 | 0.30 |
| IS-00029.a | Public Information Officer Awareness | Feb 14, 2024 | 0.70 |
| IS-00241.c | Decision Making and Problem Solving | Feb 14, 2024 | 0.20 |
| IS-00036.a | Preparedness for Child Care Providers | Feb 13, 2024 | 0.20 |
| IS-00005.a | An Introduction to Hazardous Materials | Feb 6, 2024 | 1.00 |
| IS-00242.c | Effective Communication | Feb 6, 2024 | 0.80 |
| IS-00315.a | CERT and the Incident Command System (ICS) | Feb 6, 2024 | 0.20 |
| IS-00144.a | TERT Basic Course | Feb 4, 2024 | 0.30 |
| IS-00042.a | Social Media in Emergency Management | Feb 2, 2024 | 0.30 |
| IS-00235.c | Emergency Planning | Feb 2, 2024 | 0.50 |
| IS-00238 | Critical Concepts of Supply Chain Flow and Resilience | Feb 2, 2024 | 0.20 |
| IS-00230.c | Fundamentals of Emergency Management | Jan 30, 2024 | 0.60 |
| IS-00247.b | Integrated Public Alert and Warning System for Alert Originators | Jan 30, 2024 | 0.20 |
| IS-00251.a | Integrated Public Alert and Warning System for Administrators | Jan 30, 2024 | 0.20 |
| IS-00103 | Geospatial Information Systems Specialist (GISS) | Jan 28, 2024 | 0.20 |
| IS-00100.c | Introduction to Incident Command System, ICS-100 | Feb 14, 2023 | 0.20 |
| IS-00200.c | Basic Incident Command System for Initial Response, ICS-200 | Feb 14, 2023 | 0.40 |

---

## Department of Defense Cyber Crime Center (DC3) — Cyber Training Academy

Completed specialized technical coursework through the Department of Defense Cyber Crime Center (DC3) Cyber Training Academy, a Federal Cyber Center delivering DoD-accredited digital forensics, malware analysis, and cyber defense instruction. The transcript encompasses 109 enrolled courses across offensive and defensive cyber operations, with completions scored at 100 across graded coursework:

* **Exploit Development & Malware Analysis:** Exploiting Stack Buffer Overflow, Anatomy of a Buffer Overflow, Anatomy and Static Analysis of a Windows Portable Executable, Analyzing Malware With Cuckoo, Analyzing Memory, Memory Analysis, Basic YARA, and StormSystem 101.
* **Mobile & Zero-Day Threat Analysis:** Detecting Zero-day Attacks with Sysinternals, Analyzing Commercial Spyware on Android Devices, Android Acquisition, and iOS Security, with active coursework in Malicious PE Behavior Analysis, Behavior Analysis of Malicious Portable Executables, and Malicious Botnets.
* **Digital Forensics & Incident Response:** Advanced NTFS Analysis, Windows Forensic Execution Artifacts, Detecting Anti-Forensic Techniques, EnCase Forensic Imager, FTK Imager, Autopsy Basics, IoT Forensics, IT Disaster Recovery Planning, and Traffic Collection Basics, alongside ongoing Cerberus Analysis in FTK, Collecting BitLocker-encrypted Data, File Carving in EnCase, Introduction to EnCase Case Analyzer, and Introduction to Axiom training.
* **Linux & Log Forensics:** Real-time Large Data Acquisitions in Linux, GUI Tools for Linux Computer Incident Response, Analyzing Binary Logs, Advanced BASH Scripting Techniques, and Linux Essentials.
* **Network Security & Intrusion Detection:** Network Intrusions Basics, Network Security Monitoring Using Security Onion, Managing Network Traffic Using Snort, Network Defense With Honeypots, NetFlow Overview, Network Monitoring Traffic Analysis, and Protocol Analysis Basics, with ongoing Packet Analysis With Wireshark and Data Carving in Wireshark.
* **SIEM & Packet Analysis:** Zeek Integration into ELK, Windows Log Analysis with Splunk, Introduction to NetWitness Investigator, ArcSight ESM, Netcat and Tcpdump, Introduction to Socat, and Open Source Tools for Incident Response.
* **Red Teaming & Reconnaissance:** Domain Fronting, File Transfer for Threat Emulators, Advanced Persistent Threats, Network Enumeration Attacker Tactics, HTTP in Burp Suite, Nmap, Zenmap, Aircrack Suite, and Google for Investigators.
* **Threat Intelligence & Footprinting:** Intro to i2 Analyst's Notebook and Managing Digital Footprints, with additional ongoing training in Indicators of Compromise and Ransomware Lifecycles, Mitigations, and Future.
* **ICS/SCADA & Vulnerability Management:** ICS/SCADA Basics, DISA STIG Overview, Security Content Automation Protocol, Vulnerability Management, and Vulnerability Scanning with Tenable Nessus.
* **Systems Engineering & Security Automation:** System Administration With Ansible, AWS Infrastructure, Basic Configuration of Cisco Routers and Switches, PowerShell Essentials, WMI Command-line, Sysinternals Tools, Advanced BASH, Advanced Regular Expressions, Microsoft Windows Computer Management, Introduction to Windows 11, Command-line SSL Tricks, Collecting System Information and Searching Data with PowerShell, File Sharing With FreeNAS, Introduction to Arduino, and Cyber Risk Management.
* **Cryptography & Application Analysis:** A Brief History of Cryptography, Introduction to Digital Cryptography, and Application Layer Protocol Analysis.

---

## Publications & Professional Affiliations

* **[Medium Technical Publications](https://medium.com/@NicholasKloster):** Authored technical documentation on [TempleOS kernel/system commands](https://medium.com/@NicholasKloster/templeos-commands-cf5f9a03f837), military service records, and verified FEMA, DoD, and ethical hacking certification portfolios.
* **InfraGard (FBI):** Missouri – Kansas City chapter — FBI-affiliated public-private partnership for critical infrastructure protection.
* **FEMA Student Identification (SID):** Registered FEMA SID holder for Emergency Management Institute and Center for Domestic Preparedness training.
* **National Fire Protection Association (NFPA):** Recognized Member in Good Standing, issued November 30, 2024.

---

## U.S. Army Service & Leadership

* **Primary Specialty:** Served 8 years and 3 months as an 11B3O Infantryman Non-Commissioned Officer (Staff Sergeant, E-6) with Additional Skill Identifier 8R, concluding service at Rifle Company FC. ETS 2023. Inactive Secret clearance.
* **Emergency Telecommunications Leadership:** Served as the Louisiana Program Administrator for the GETS and WPS priority telecommunications programs from 2021 to 2023, overseeing enrollment and credential issuance for all military personnel.
* **Combat Deployments:** Completed two combat deployments to Kandahar, Afghanistan within designated imminent danger pay areas from March to November 2016 and March to November 2018.
* **Military Education:** Graduated from the five-week Advanced Leader Course in 2021, two-week Basic Military Mountaineering Course in 2020, four-week Basic Leader Course in 2018, and one-week Combat Lifesavers Course.
* **Decorations & Awards:** Army Commendation Medal with C Device, second Army Commendation Medal, Army Achievement Medal, second Good Conduct Medal, Afghanistan Campaign Medal with Star, and NATO Medal.

---

## NuClide

Most of my recent work is built collaboratively with Claude (Anthropic). The collaboration is **NuClide** — Nick + Claude. The tools, the disclosures, the research methodology — that's what happens when a security researcher and a language model build things together instead of just talking.

No degree. Everything here is self-taught.

## Contact

[nuclide-research.com](https://nuclide-research.com) · [Medium](https://medium.com/@NicholasKloster)

**Open to:** AI/LLM red team roles · offensive security research · advisory · contract tool development
