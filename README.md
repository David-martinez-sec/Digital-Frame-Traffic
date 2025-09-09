# Digital-Frame-Traffic: IoT Traffic Analysis Project

## Inception
While conducting a routine network scan with `nmap`, I identified a device on my home network that raised suspicion.  
Although its ports appeared filtered, the device stood out against the rest of the scan results. Upon closer inspection, I realized it was a **digital picture frame**.  

The discovery highlighted an important reality: even simple consumer IoT devices can present unknown or poorly documented behaviors on a network. Given how often IoT devices lack strong security controls, I chose to treat this as a learning opportunity.  

Rather than ignore the anomaly, I decided to monitor and log the device’s network communications to evaluate:
- Which external domains or IPs it was contacting
- Whether its traffic patterns seemed legitimate
- If there were any indications of misuse, compromise, or data exfiltration

---

## Intent
This project is designed as both an investigation and a skills-building exercise. By analyzing an everyday IoT device, I aim to strengthen my expertise in:

- **Network traffic monitoring**: Using a Raspberry Pi as an inline bridge to passively observe communications.
- **Security logging**: Deploying Zeek to generate structured logs (DNS queries, connections, TLS metadata).
- **Log analysis with SQL**: Importing log data into a relational database to practice querying and threat-hunting workflows.
- **Critical thinking**: Developing the mindset to treat anomalies as opportunities for investigation, not just curiosities.

Beyond technical growth, this project reflects a broader cybersecurity principle: **visibility matters**.  
Understanding how devices behave on the network is the first step toward securing them — whether at home or in the enterprise.

---

## Next Steps
Future documentation (separate file) will detail:
- The environment setup (Pi bridge, Zeek installation)
- Log ingestion into SQLite
- Example queries and insights

