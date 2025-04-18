# Network Security Lab: Virtual Firewall, IDS & Attack Simulation

A fully virtualized network security lab to simulate real-world attack scenarios, analyze traffic, and configure defenses using open-source tools like pfSense, Kali Linux, Wireshark, and Snort.

---

## **Project Overview**

This lab project demonstrates the core principles of network security by:
- Configuring a firewall using pfSense
- Simulating common attacks using Kali Linux
- Monitoring traffic with Wireshark
- Detecting intrusions with Snort

---

## **Network Topology**

```
[ Kali Linux (Attacker) ]
            |
      [ pfSense Firewall ]
            |
[ Windows/Ubuntu (Victim Machine) ]
```

- Virtualized using VirtualBox with internal networking.

---

## **Tools & Technologies**

| Component          | Tool Used              |
|-------------------|------------------------|
| Virtualization     | VirtualBox             |
| Firewall           | pfSense                |
| Packet Analysis    | Wireshark              |
| Intrusion Detection| Snort (via pfSense)    |
| Attack Simulation  | Kali Linux (Nmap, Hydra, hping3) |
| Victim Machine     | Ubuntu or Windows      |

---

## **Lab Setup Instructions**

### 1. **Create Virtual Machines**
- Kali Linux (Attacker)
- pfSense (Firewall)
- Windows or Ubuntu (Victim)

All set to the same internal network.

### 2. **Configure pfSense**
- WAN: Connected to Kali
- LAN: Connected to Victim
- Enable DHCP on LAN
- Firewall Rules:
  - Block Port 23 (Telnet)
  - Allow ICMP, HTTP
  - Log denied connections

### 3. **Simulate Attacks Using Kali**
- **Nmap**: Port Scanning
  ```bash
  nmap -sS <victim_ip>
  ```
- **Hydra**: SSH brute force
  ```bash
  hydra -l root -P passwords.txt ssh://<victim_ip>
  ```
- **hping3**: DoS simulation
  ```bash
  hping3 -S --flood <victim_ip>
  ```

### 4. **Monitor Traffic**
- Capture traffic using Wireshark on victim or attacker machine.
- Filter by IP, protocol, port.

### 5. **Enable Snort on pfSense**
- Install Snort package.
- Configure interface and enable basic rules.
- Check logs for alerts.

---

## **Results**

| Test                    | Result                            |
|-------------------------|-----------------------------------|
| Ping & Web Traffic      | Allowed (verified via Wireshark) |
| Telnet Traffic          | Blocked by pfSense (logged)       |
| Nmap Port Scan          | Detected by Snort                 |
| DoS Flood               | Visible in packet capture         |
| SSH Brute Force         | Logged on victim OS               |

---

## **Screenshots**
- [✓] pfSense firewall rules
- [✓] Wireshark captures
- [✓] Snort alert logs
- [✓] Kali attack terminal output

 

---

## **Conclusion**

This project builds a strong foundation in practical network security by implementing, testing, and documenting key defenses against real-world threats.

---

## **Future Work**
- Integrate Splunk for centralized logging
- Add VPN and secure remote access
- Simulate MITM or DNS spoofing attacks
- Automate rule deployment with Ansible

---

## **Author**

**Divya Singh**  
B.Tech in Electronics & Communication Engineering  
**Email**: divyasingh.divz@gmail.com  
**LinkedIn**: [linkedin.com/in/divya-singh-84ab83294](https://www.linkedin.com/in/divya-singh-84ab83294)

---

## **License**
This project is open-source and available under the [MIT License](LICENSE).
