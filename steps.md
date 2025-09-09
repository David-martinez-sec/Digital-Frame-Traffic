# Steps: IoT Traffic Analysis (High-Level Plan)

> Flow: Device ➜ Pi Bridge (tap) ➜ Zeek Logs ➜ SQLite DB ➜ Analysis ➜ Findings/Hardening

---

## Step 1 — Reconfirm the Target and Baseline
- **What:** Positively identify the IoT device discovered during Nmap recon (model, MAC, IP lease behavior). Capture a quick baseline (DHCP, ARP, hostname).
- **Why:** Prevents chasing the wrong host and establishes a reference point for later comparison.

## Step 2 — Define Scope, Goals, and Safety
- **What:** Write a brief scope (only this device + home LAN), goals (visibility, risk assessment, SQL practice), and basic rules of engagement (no active exploitation).
- **Why:** Keeps the project focused, ethical, and easy to communicate to others (portfolio-ready).

## Step 3 — Choose the Capture Strategy
- **What:** Decide between an inline Ethernet bridge (preferred), router/AP capture, or Wi-Fi monitor mode.
- **Why:** Strategy determines visibility. Inline bridging gives full L2 coverage for the target without trickery.

## Step 4 — Prepare the Pi Environment
- **What:** Ensure the Pi OS is current, name interfaces, and plan management access (e.g., Pi on Wi-Fi, bridge on Ethernet).
- **Why:** A stable, predictable platform reduces noise and troubleshooting later.

## Step 5 — Establish a Minimal Initial Capture
- **What:** Do a short, time-boxed packet capture to validate visibility (e.g., DNS, outbound connections).
- **Why:** Early sanity check before building the full pipeline; confirms the tap is actually seeing useful traffic.

## Step 6 — Deploy Zeek for Structured Logging
- **What:** Run Zeek on the bridge interface to generate `dns.log`, `conn.log`, `ssl.log` (and others as needed).
- **Why:** Zeek translates packets into analyst-friendly records—exactly what SOC teams use.

## Step 7 — Plan Log Management
- **What:** Decide retention windows, rotation frequency, and which logs to keep vs. ignore (e.g., focus on DNS/conn/ssl).
- **Why:** Prevents disk bloat and keeps the dataset purposeful for analysis and SQL practice.

## Step 8 — Data Modeling for SQL
- **What:** Sketch tables/columns for DNS and connection data (e.g., `dns(query, ts, src_ip, answers…)`, `conn(ts, orig_h, resp_h, proto, bytes…)`).
- **Why:** A simple, intentional schema makes querying and joins straightforward.

## Step 9 — ETL: From Zeek Logs to Database
- **What:** Define an Extract-Transform-Load flow (parse → normalize → load into SQLite/Postgres).
- **Why:** Bridges raw security telemetry to relational analysis; builds real, marketable SQL + data-engineering skills.

## Step 10 — Core SQL Analyses (Threat-Hunting Basics)
- **What:** Write queries for top domains, failed vs. successful DNS, unique destinations, periodicity, byte ratios, first/last-seen, and allow-lists/deny-lists.
- **Why:** Turns telemetry into insights and detection ideas; mirrors day-to-day analyst work.

## Step 11 — Enrichment (Optional but Valuable)
- **What:** Add GeoIP, ASN, reverse DNS, and basic threat-intel tags to IPs/domains.
- **Why:** Enrichment turns raw indicators into context that supports decisions.

## Step 12 — Hypotheses & Anomaly Testing
- **What:** Form and test hypotheses (e.g., “Does the frame beacon every 10 minutes to a single ASN?” “Any off-hours spikes?”).
- **Why:** Structured inquiry prevents over-fitting to noise and produces credible findings.

## Step 13 — Visualization & Reporting
- **What:** Plot simple charts (e.g., top domains, traffic over time) and summarize findings in a short report.
- **Why:** Clear visuals and narratives are key for interviews, stakeholders, and your portfolio.

## Step 14 — Security Actions & Hardening
- **What:** Based on findings: isolate the device (VLAN), restrict egress (firewall), update firmware, or replace the device.
- **Why:** Converts analysis into risk reduction—closing the loop like a real security engineer.

## Step 15 — Documentation & Reproducibility
- **What:** Record assumptions, limitations, and “gotchas”; capture data lineage from packet to SQL row.
- **Why:** Professionalism—future you (and reviewers) can reproduce and extend the work.

## Step 16 — Extensions (Optional)
- **What:** Try Suricata for rule-based alerts; add TLS JA3 fingerprinting pivots; attempt WPA2 decryption on home Wi-Fi captures; stream to a dashboard.
- **Why:** Lets you branch into IDS engineering, protocol fingerprinting, and blue-team operations.

---

## Deliverables Checklist
- [ ] Short **Scope & ROE** note  
- [ ] **Zeek logs** (selected types) with retention plan  
- [ ] **Database schema** + ETL notes  
- [ ] **Core SQL** queries (saved as `.sql`)  
- [ ] **Findings report** with visuals  
- [ ] **Hardening recommendations** and next steps

