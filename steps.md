# IoT Traffic Analysis – Steps

This file outlines the main steps I’ll follow to investigate the network behavior of the digital picture frame I discovered.  
The goal is to keep the flow high-level: what I’m doing and why.

---

## Step 1 — Confirm the Device
- **What:** Double-check the device identity (MAC address, IP lease, hostname).  
- **Why:** Makes sure I’m tracking the correct target and not mixing it up with something else on the network.  

## Step 2 — Define Scope
- **What:** Keep the investigation limited to this one IoT device on my home LAN.  
- **Why:** Keeps things focused and avoids creating unnecessary noise.  

## Step 3 — Pick Capture Method
- **What:** Decide how to see the device’s traffic (inline bridge, router capture, or Wi-Fi monitor mode).  
- **Why:** The method determines what traffic I’ll be able to observe.  

## Step 4 — Prepare the Pi
- **What:** Set up the Raspberry Pi, update it, and configure the interfaces so it can sit in-line with the device.  
- **Why:** A stable Pi setup is the foundation for capturing traffic reliably.  

## Step 5 — Test a Small Capture
- **What:** Run a short packet capture to make sure I’m actually seeing the device’s communications.  
- **Why:** Quick sanity check before logging long-term data.  

## Step 6 — Use Zeek for Logs
- **What:** Run Zeek on the Pi to generate structured logs (DNS, connections, TLS info).  
- **Why:** Zeek turns raw packets into readable records that are easier to review.  

## Step 7 — Organize Logs
- **What:** Decide which log types matter (DNS, connection, SSL) and rotate them as needed.  
- **Why:** Prevents the Pi from filling up and keeps the dataset manageable.  

## Step 8 — Plan Database Tables
- **What:** Map out simple tables for the data I want to load, such as DNS queries or connections.  
- **Why:** Makes later analysis easier and keeps the structure consistent.  

## Step 9 — Load Logs into Database
- **What:** Extract the data from Zeek logs and import into SQLite.  
- **Why:** A database lets me query and look for patterns more effectively.  

## Step 10 — Write Core Queries
- **What:** Build queries to find top domains, unique IPs, failed vs. successful lookups, and traffic patterns.  
- **Why:** These basics give a clear picture of what the device is doing on the network.  

## Step 11 — Add Context (Optional)
- **What:** Look up IP locations, owners, or use blocklists to tag suspicious destinations.  
- **Why:** Adds more meaning to the raw data and can highlight unusual behavior.  

## Step 12 — Look for Anomalies
- **What:** Check if the device contacts the same service at odd intervals, talks to unexpected regions, or has sudden spikes in traffic.  
- **Why:** Helps decide if the behavior is normal or potentially a problem.  

## Step 13 — Summarize Findings
- **What:** Write up what I saw, supported with charts or simple visuals if needed.  
- **Why:** Keeps the results clear and easy to revisit later.  

## Step 14 — Take Action
- **What:** If anything looks unsafe, isolate the device, block destinations, update firmware, or remove it from the network.  
- **Why:** The point of the analysis is not just to observe, but to make improvements if necessary.  

## Step 15 — Document and Store
- **What:** Keep notes on what worked, what didn’t, and where the data lives.  
- **Why:** Ensures I can repeat or extend the process later without starting over.  

---

