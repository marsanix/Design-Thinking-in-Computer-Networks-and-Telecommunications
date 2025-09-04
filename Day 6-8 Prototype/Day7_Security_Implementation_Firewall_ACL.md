# Day 7: Keamanan Informasi & Security Implementation
## Fase: Prototype - Security Hardening

### 🎯 Learning Objectives
Setelah mengikuti sesi ini, peserta akan mampu:
1. Memahami konsep Keamanan Informasi dan Cybersecurity
2. Menganalisis ancaman dan vulnerability dalam jaringan
3. Mengimplementasikan firewall rules pada router
4. Mengkonfigurasi Access Control Lists (ACL) untuk network security
5. Menerapkan port security pada switch
6. Mengimplementasikan basic intrusion detection
7. Melakukan security testing dan validation
8. Mendokumentasikan security policies
9. Membuat security policy dan incident response plan

---

## 📋 Session Overview
**Durasi:** 60 menit  
**Format:** Hands-on Security Workshop  
**Tools:** Cisco Packet Tracer, Security Research dari homework  
**Deliverable:** Secured Network Topology dengan security documentation

---

## 🛡️ **SESI 1: Keamanan Informasi Fundamentals (45 menit)**

### A. Konsep Keamanan Informasi (15 menit)
- **CIA Triad**:
  - **Confidentiality**: Kerahasiaan data
  - **Integrity**: Integritas data
  - **Availability**: Ketersediaan sistem
  
- **Prinsip Keamanan Tambahan**:
  - **Authentication**: Verifikasi identitas
  - **Authorization**: Kontrol akses
  - **Non-repudiation**: Tidak dapat disangkal
  - **Accountability**: Pertanggungjawaban

### B. Ancaman dan Vulnerability (15 menit)
- **Jenis Ancaman**:
  - **Malware**: Virus, worm, trojan, ransomware
  - **Social Engineering**: Phishing, pretexting
  - **Network Attacks**: DDoS, Man-in-the-middle
  - **Insider Threats**: Ancaman dari dalam organisasi
  
- **Common Vulnerabilities**:
  - Weak passwords
  - Unpatched systems
  - Misconfiguration
  - Lack of encryption

### C. Security Framework dan Standards (15 menit)
- **ISO 27001**: Information Security Management
- **NIST Cybersecurity Framework**: Identify, Protect, Detect, Respond, Recover
- **COBIT**: Control Objectives for IT
- **Best Practices**: Defense in depth, Zero trust

## 🔒 **SESI 2: Security Assessment & Planning (20 menit)**

### Current Network Analysis
**Review implementasi Day 6:**
- Network topology yang telah dibuat
- Existing security measures
- Potential vulnerabilities (berdasarkan konsep keamanan informasi)
- Traffic flow analysis

### Security Requirements Review
**Berdasarkan solution concept:**
- Security objectives yang harus dicapai (CIA Triad)
- Compliance requirements
- Risk assessment results
- Security policies yang perlu diimplementasikan

### Security Implementation Plan
**Planning untuk hari ini:**
- Priority security measures
- Implementation sequence
- Testing strategies
- Success criteria

## 🚀 Opening Activity (10 menit)

### Security Threat Review
**Aktivitas:** "Threat Landscape Analysis"
- Presentasi homework: 3 common network threats
- Mapping threats ke existing topology
- Prioritizing security implementations

**Key Discussion:**
- Mana threat yang paling critical untuk small office?
- Bagaimana current topology vulnerable?
- Apa quick wins yang bisa diimplementasikan?

---

## 🛠️ Main Activities

### Activity 1: Firewall Implementation dengan Router ACL (15 menit)

#### Understanding Access Control Lists (ACL)
**ACL Types:**
- **Standard ACL (1-99):** Filter berdasarkan source IP
- **Extended ACL (100-199):** Filter berdasarkan source, destination, protocol, port

#### Scenario: Protecting Server VLAN
**Security Requirements:**
- Block external access ke management interfaces
- Allow only HTTP/HTTPS ke web server
- Block inter-VLAN access kecuali yang diperlukan
- Log security violations

#### Step-by-Step ACL Implementation

**Step 1: Extended ACL untuk Internet Traffic**
```cisco
Router(config)# ip access-list extended INTERNET_IN
Router(config-ext-nacl)# remark === Block malicious traffic ===
Router(config-ext-nacl)# deny tcp any any eq 23
Router(config-ext-nacl)# deny tcp any any eq 22
Router(config-ext-nacl)# deny tcp any any range 135 139
Router(config-ext-nacl)# deny tcp any any eq 445
Router(config-ext-nacl)# deny udp any any eq 161
Router(config-ext-nacl)# remark === Allow legitimate traffic ===
Router(config-ext-nacl)# permit tcp any host 192.168.1.18 eq 80
Router(config-ext-nacl)# permit tcp any host 192.168.1.18 eq 443
Router(config-ext-nacl)# permit tcp any host 192.168.1.18 eq 21
Router(config-ext-nacl)# permit icmp any any echo-reply
Router(config-ext-nacl)# permit tcp any any established
Router(config-ext-nacl)# deny ip any any log
Router(config-ext-nacl)# exit

Router(config)# interface gi0/0
Router(config-if)# ip access-group INTERNET_IN in
Router(config-if)# exit
```

**Step 2: Inter-VLAN Security**
```cisco
Router(config)# ip access-list extended VLAN_SECURITY
Router(config-ext-nacl)# remark === Server VLAN Protection ===
Router(config-ext-nacl)# permit tcp 192.168.1.32 0.0.0.31 host 192.168.1.18 eq 80
Router(config-ext-nacl)# permit tcp 192.168.1.32 0.0.0.31 host 192.168.1.18 eq 443
Router(config-ext-nacl)# permit tcp 192.168.1.32 0.0.0.31 host 192.168.1.18 eq 21
Router(config-ext-nacl)# deny ip 192.168.1.32 0.0.0.31 192.168.1.16 0.0.0.15 log
Router(config-ext-nacl)# permit ip any any
Router(config-ext-nacl)# exit

Router(config)# interface gi0/1.20
Router(config-subif)# ip access-group VLAN_SECURITY in
Router(config-subif)# exit
```

### Activity 2: Switch Port Security Implementation (10 menit)

#### Port Security Configuration
**Tujuan:** Prevent MAC address spoofing dan unauthorized device access

```cisco
Switch(config)# interface range fa0/1-10
Switch(config-if-range)# switchport mode access
Switch(config-if-range)# switchport port-security
Switch(config-if-range)# switchport port-security maximum 2
Switch(config-if-range)# switchport port-security mac-address sticky
Switch(config-if-range)# switchport port-security violation restrict
Switch(config-if-range)# exit

# Untuk server ports - lebih strict
Switch(config)# interface fa0/24
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan 10
Switch(config-if)# switchport port-security
Switch(config-if)# switchport port-security maximum 1
Switch(config-if)# switchport port-security mac-address sticky
Switch(config-if)# switchport port-security violation shutdown
Switch(config-if)# exit
```

#### DHCP Snooping untuk Additional Security
```cisco
Switch(config)# ip dhcp snooping
Switch(config)# ip dhcp snooping vlan 20
Switch(config)# interface gi0/1
Switch(config-if)# ip dhcp snooping trust
Switch(config-if)# exit

Switch(config)# interface range fa0/1-10
Switch(config-if-range)# ip dhcp snooping limit rate 10
Switch(config-if-range)# exit
```

### Activity 3: Network Monitoring & Logging (10 menit)

#### Syslog Configuration
```cisco
# Pada Router
Router(config)# logging on
Router(config)# logging host 192.168.1.18
Router(config)# logging trap informational
Router(config)# service timestamps log datetime msec
Router(config)# logging source-interface gi0/1.10

# Pada Switch
Switch(config)# logging on
Switch(config)# logging host 192.168.1.18
Switch(config)# logging trap warnings
Switch(config)# service timestamps log datetime msec
```

#### SNMP untuk Network Monitoring
```cisco
Router(config)# snmp-server community SecureRead ro
Router(config)# snmp-server community SecureWrite rw
Router(config)# snmp-server host 192.168.1.18 version 2c SecureRead
Router(config)# snmp-server enable traps
```

### Activity 4: Security Testing & Validation (10 menit)

#### Security Test Scenarios

**Test 1: ACL Functionality**
```
Test Case: External Telnet Access
Expected: DENIED
Command: telnet [router_external_ip] dari internet cloud
Result: Connection refused/timeout
```

**Test 2: Inter-VLAN Access Control**
```
Test Case: Workstation ke Server Management
Expected: DENIED
Command: ping 192.168.1.17 dari workstation
Result: Request timeout
```

**Test 3: Port Security**
```
Test Case: MAC Address Spoofing
Expected: Port shutdown/restrict
Action: Change MAC address pada PC
Result: Port security violation
```

#### Monitoring Commands
```cisco
# Check ACL hits
show access-lists

# Check port security status
show port-security
show port-security interface fa0/1

# Check logging
show logging

# Check DHCP snooping
show ip dhcp snooping binding
```

### Activity 5: Security Documentation (5 menit)

#### Security Policy Documentation
```markdown
## Network Security Implementation

### Access Control Policies
1. **Internet Access Control**
   - Block: Telnet, SSH, NetBIOS, SNMP dari external
   - Allow: HTTP, HTTPS, FTP ke web server
   - Log: All denied attempts

2. **Inter-VLAN Policies**
   - Workstations: Limited server access (HTTP/HTTPS only)
   - Servers: No direct access dari workstations
   - Management: Restricted to admin VLAN

3. **Port Security**
   - Maximum 2 MAC addresses per user port
   - Maximum 1 MAC address per server port
   - Sticky MAC learning enabled
   - Violation action: Restrict (users), Shutdown (servers)

### Monitoring & Logging
- Syslog server: 192.168.1.18
- SNMP monitoring enabled
- Security violation logging
- Performance monitoring
```

---

## 🔍 Advanced Security Features (Bonus)

### Network Address Translation (NAT)
```cisco
Router(config)# access-list 1 permit 192.168.1.0 0.0.0.255
Router(config)# ip nat inside source list 1 interface gi0/0 overload
Router(config)# interface gi0/0
Router(config-if)# ip nat outside
Router(config-if)# exit
Router(config)# interface gi0/1
Router(config-if)# ip nat inside
Router(config-if)# exit
```

### Zone-Based Firewall (Konsep)
```cisco
# Konsep untuk advanced implementation
Router(config)# zone security INSIDE
Router(config)# zone security OUTSIDE
Router(config)# zone security DMZ

# Policy maps untuk traffic control
Router(config)# class-map type inspect match-any INSIDE_TO_OUTSIDE
Router(config-cmap)# match protocol http
Router(config-cmap)# match protocol https
Router(config-cmap)# match protocol dns
```

---

## 📊 Security Assessment Checklist

### Pre-Implementation Security Gaps
- [ ] No access control pada router interfaces
- [ ] No port security pada switches
- [ ] No logging atau monitoring
- [ ] No protection against common attacks
- [ ] No network segmentation enforcement

### Post-Implementation Security Features
- [x] Router ACL untuk external traffic filtering
- [x] Inter-VLAN access control
- [x] Switch port security
- [x] DHCP snooping
- [x] Centralized logging
- [x] SNMP monitoring
- [x] Security violation detection

### Security Metrics
```
Security Score Improvement:
Before: 2/10 (Basic connectivity only)
After:  7/10 (Comprehensive security controls)

Remaining Gaps:
- Advanced threat detection
- Encryption implementation
- User authentication (802.1X)
```

---

## 🎯 Deliverables

### Individual Deliverables
1. **Secured Packet Tracer File:** `Day7_SecuredTopology_[Nama].pkt`
2. **Security Configuration Backup:** All device configs
3. **Security Test Report:** Test results dan screenshots
4. **Security Policy Document:** Menggunakan template di atas

### Team Deliverables
1. **Security Demo:** 5 menit demonstration
2. **Vulnerability Assessment:** Before vs After comparison
3. **Incident Response Plan:** Basic procedures

---

## 🏠 Homework: Advanced Security Research

### Assignment: "Next-Level Security Features"
**Deadline:** Sebelum Day 8

**Research Topics (pilih 2):**
1. **Wireless Security:**
   - WPA3 implementation
   - Guest network isolation
   - Wireless intrusion detection

2. **Advanced Threat Protection:**
   - IPS (Intrusion Prevention System)
   - DDoS protection
   - Malware detection

3. **Identity & Access Management:**
   - 802.1X authentication
   - RADIUS server integration
   - Role-based access control

4. **Network Encryption:**
   - VPN implementation
   - IPSec tunnels
   - SSL/TLS certificates

**Deliverable:**
- 2-page research report per topic
- Implementation proposal untuk Day 8
- Cost-benefit analysis

---

## 📚 Resources

### Cisco Security Documentation
- [ACL Configuration Guide](https://www.cisco.com/c/en/us/support/docs/security/ios-firewall/23602-confaccesslists.html)
- [Port Security Best Practices](https://www.cisco.com/c/en/us/support/docs/lan-switching/)
- [Network Security Baseline](https://www.cisco.com/c/en/us/support/docs/availability/)

### Security Standards & Frameworks
- NIST Cybersecurity Framework
- ISO 27001 Network Security
- CIS Controls for Network Security

### Testing Tools
- Packet Tracer Simulation Mode
- Network security checklists
- Vulnerability assessment templates

---

## 🔄 Reflection & Preview

### Today's Reflection
1. **Bagaimana security implementation mengubah network behavior?**
2. **Apa trade-offs antara security dan usability?**
3. **Mana security control yang paling effective?**
4. **Bagaimana cara measure security effectiveness?**

### Preview Day 8
**Topic:** "Advanced Security & Network Optimization"
- Wireless security implementation
- Advanced threat protection
- Network performance optimization
- Final prototype integration
- Preparation untuk testing phase

**Preparation:**
- Complete advanced security research
- Review current topology performance
- Prepare optimization ideas
- Think about real-world deployment challenges

---

*"Security is not a product, but a process. Today we built the foundation, tomorrow we perfect it!"*

**Mentor Notes:**
- Emphasize security mindset, not just configuration
- Encourage testing dan validation
- Discuss real-world security incidents
- Help students understand business impact of security decisions
- Prepare for common ACL troubleshooting issues