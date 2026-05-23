# SOC Analyst AI Agent 🛡️

An automated threat detection and response pipeline that captures live network traffic, detects suspicious activity, and triggers an AI agent for real-time analysis — simulating a Tier 1 SOC analyst workflow.

---

## 🔍 How It Works

```
Ubuntu (Attacker Machine)
        ↓ sends ICMP/network traffic
Kali Linux (Internal Server)
        ↓ soc_agent.py captures live traffic via tshark
        ↓ converts PCAP → CSV
        ↓ analyses packet volume per source IP
        ↓ detects suspicious IPs exceeding threshold
        ↓ generates alert.json
        ↓ sends alert to Airia AI Agent via API
Airia AI Agent
        ↓ analyses the alert
        ↓ returns threat assessment and recommendation
```

---

## 🧰 Tech Stack

| Tool | Purpose |
|---|---|
| Python 3 | Core automation script |
| tshark | Live packet capture |
| Wireshark/PCAP | Traffic analysis |
| Airia AI | AI agent for threat analysis |
| Kali Linux | Internal server / defender machine |
| Ubuntu | Attacker simulation machine |

---

## ⚙️ Configuration

```python
INTERFACE = "eth0"           # Network interface to monitor
CAPTURE_DURATION = 100       # Capture window in seconds
THRESHOLD = 40               # Suspicious packet threshold per source IP
PCAP_FILE = "/tmp/traffic.pcap"
CSV_FILE  = "/tmp/traffic.csv"
ALERT_FILE = "/tmp/alert.json"
```

---

## 🚀 How to Run

```bash
# Clone the repo
git clone https://github.com/yourusername/soc-analyst-ai-agent.git
cd soc-analyst-ai-agent

# Install dependencies
pip install requests

# Add your Airia API credentials in soc_agent.py
AIRIA_API_URL = "your-pipeline-url"
AIRIA_API_KEY = "your-api-key"

# Run the agent
sudo python3 soc_agent.py
```

---

## 📸 Architecture

![Architecture](architecture.png)

---

## 📊 Sample Output

```
[+] Capturing on eth0 for 100s
[+] Capture saved to traffic.pcap
[+] CSV created at traffic.csv
[+] Traffic volume per source IP:
    192.168.56.1: 97 packets
[!] Suspicious IP detected: 192.168.56.1
[+] Alert JSON written to alert.json
[+] Sending alert to Airia Agent Execution API...
```

---

## ⚠️ Known Limitations

- Airia API integration requires internet access — host-only network mode will block the API call (lab limitation, detection logic works fully)
- Run as root required for tshark packet capture

---

## 💡 What I Learned

- Live network traffic capture and analysis using tshark
- Building automated detection pipelines with Python
- Integrating AI agents via REST API with authentication
- Simulating real SOC workflows — detect → alert → analyse → respond
- Network fundamentals: ICMP, packet thresholds, source IP analysis

---

## 👤 Author

Karan| Cybersecurity Analyst | 
Building: Red team skills on TryHackMe | Blue team in the lab
