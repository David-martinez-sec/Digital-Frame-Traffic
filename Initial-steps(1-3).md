# IoT Traffic Analysis – Initial Steps

This document records the first three steps in setting up an investigation into the network behavior of the digital picture frame discovered during a routine scan.

---

## Step 1 — Confirm the Device
- Identified the IoT device as a **digital picture frame** during an Nmap scan.  
- Current network details:  
  - **IP:** 10.0.0.43  
  - **MAC:** (recorded locally)  
  - **Hostname:** (recorded locally, if available)  
- Notes: These details confirm the target and ensure I’m monitoring the correct device.

---

## Step 2 — Define Scope
- Scope is limited to the **digital picture frame only**.  
- Focus areas:  
  - Outbound domains and IPs the frame communicates with  
  - Frequency and patterns of communication  
  - Signs of unusual or unnecessary traffic  
- No other devices will be included in this analysis.

---

## Step 3 — Pick Capture Method
- Chosen method: **Ethernet capture** with the Raspberry Pi acting as an inline bridge.  
- Reasoning:  
  - The device will be connected over Ethernet temporarily.  
  - The Pi will sit between the picture frame and the router, forwarding traffic while capturing it.  
  - This avoids the complications of Wi-Fi monitoring (adapter support, encryption, handshake capture).  
- Considerations:  
  - Requires at least one Ethernet cable and ideally a USB–Ethernet adapter to give the Pi two wired interfaces.  
  - Once connected, the Pi will transparently log traffic for later analysis without interfering with normal device operation.  
