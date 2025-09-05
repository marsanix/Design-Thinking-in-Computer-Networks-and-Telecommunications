# Day 4: Teknologi Serat Optik & Security Requirements Definition
## Fase Define - Mendefinisikan Kebutuhan Keamanan yang Spesifik

### Tujuan Pembelajaran
Setelah sesi ini, peserta akan mampu:
1. Mengenal perkembangan teknologi fiber optic terkini
2. Memahami jenis-jenis kabel FO dan aplikasinya
3. Menganalisis keamanan pada infrastruktur fiber optic
4. Menganalisis competitive analysis untuk mengidentifikasi gaps dan opportunities
5. Mendefinisikan security requirements yang comprehensive dan actionable
6. Membuat security architecture framework berdasarkan user needs
7. Memahami compliance requirements dan industry standards
8. Menyusun technical specifications untuk network security implementation

---

## 🌐 **SESI 1: IP Addressing & Subnetting - Dasar Pengalamatan Jaringan (50 menit)**

### Mengapa IP Addressing Penting?

Sebelum memahami security requirements, kita perlu memahami bagaimana perangkat di jaringan saling berkomunikasi. IP Address adalah seperti alamat rumah - tanpa alamat yang benar, data tidak bisa sampai ke tujuan.

### A. Konsep Dasar IP Addressing - 15 menit

#### **Apa itu IP Address?**
- **Definisi**: Alamat logical yang unik untuk mengidentifikasi perangkat di jaringan
- **Fungsi**: Memungkinkan routing data antar perangkat
- **Analogi**: Seperti alamat rumah untuk pengiriman surat

#### **IPv4 Address Structure**
- **Format**: 32-bit address (4 oktet)
- **Contoh**: 192.168.1.100
- **Range**: 0.0.0.0 sampai 255.255.255.255
- **Total**: ~4.3 miliar alamat

#### **Komponen IPv4 Address**
```
192.168.1.100/24
│   │   │ │   │
│   │   │ │   └── Host portion
│   │   │ └────── Network portion
│   │   └──────── 
│   └──────────── 
└──────────────── 

/24 = Subnet Mask = 255.255.255.0
```

### B. Kelas IP Address - 10 menit

#### **Class A**
- **Range**: 1.0.0.0 - 126.255.255.255
- **Default Subnet Mask**: 255.0.0.0 (/8)
- **Network**: 8 bit, Host: 24 bit
- **Jumlah Host**: 16,777,214 per network
- **Penggunaan**: Large organizations, ISP

#### **Class B**
- **Range**: 128.0.0.0 - 191.255.255.255
- **Default Subnet Mask**: 255.255.0.0 (/16)
- **Network**: 16 bit, Host: 16 bit
- **Jumlah Host**: 65,534 per network
- **Penggunaan**: Medium organizations

#### **Class C**
- **Range**: 192.0.0.0 - 223.255.255.255
- **Default Subnet Mask**: 255.255.255.0 (/24)
- **Network**: 24 bit, Host: 8 bit
- **Jumlah Host**: 254 per network
- **Penggunaan**: Small organizations, home networks

#### **Private IP Ranges (RFC 1918)**
- **Class A Private**: 10.0.0.0 - 10.255.255.255
- **Class B Private**: 172.16.0.0 - 172.31.255.255
- **Class C Private**: 192.168.0.0 - 192.168.255.255
- **Loopback**: 127.0.0.0 - 127.255.255.255

### C. Subnet Mask & CIDR - 15 menit

#### **Apa itu Subnet Mask?**
- **Fungsi**: Memisahkan network portion dari host portion
- **Format**: Dotted decimal atau CIDR notation
- **Contoh**: 255.255.255.0 = /24

#### **CIDR (Classless Inter-Domain Routing)**
```
/24 = 255.255.255.0   = 11111111.11111111.11111111.00000000
/25 = 255.255.255.128 = 11111111.11111111.11111111.10000000
/26 = 255.255.255.192 = 11111111.11111111.11111111.11000000
/27 = 255.255.255.224 = 11111111.11111111.11111111.11100000
/28 = 255.255.255.240 = 11111111.11111111.11111111.11110000
/29 = 255.255.255.248 = 11111111.11111111.11111111.11111000
/30 = 255.255.255.252 = 11111111.11111111.11111111.11111100
```

#### **Menghitung Jumlah Host**
- **Formula**: 2^(32-subnet_bits) - 2
- **Contoh /24**: 2^(32-24) - 2 = 2^8 - 2 = 254 host
- **Contoh /26**: 2^(32-26) - 2 = 2^6 - 2 = 62 host

### D. Subnetting Praktis - 10 menit

#### **Skenario**: Perusahaan dengan network 192.168.1.0/24 perlu dibagi menjadi 4 subnet

**Langkah-langkah:**
1. **Tentukan jumlah subnet**: 4 subnet
2. **Hitung bit yang diperlukan**: 2^2 = 4, jadi perlu 2 bit
3. **Subnet mask baru**: /24 + 2 = /26
4. **Subnet mask**: 255.255.255.192

**Hasil Subnetting:**
```
Subnet 1: 192.168.1.0/26   (192.168.1.1 - 192.168.1.62)
Subnet 2: 192.168.1.64/26  (192.168.1.65 - 192.168.1.126)
Subnet 3: 192.168.1.128/26 (192.168.1.129 - 192.168.1.190)
Subnet 4: 192.168.1.192/26 (192.168.1.193 - 192.168.1.254)
```

#### **Aktivitas Praktis: "Subnet Calculator"**

**Soal 1**: Network 10.0.0.0/8 perlu dibagi untuk:
- Kantor Pusat: 1000 host
- Cabang A: 500 host
- Cabang B: 200 host
- Cabang C: 100 host

**Tugas Siswa**:
1. Tentukan subnet mask untuk masing-masing
2. Hitung range IP address
3. Identifikasi network address dan broadcast address

**Soal 2**: Sekolah dengan network 192.168.10.0/24 perlu:
- Lab Komputer: 30 host
- Ruang Guru: 20 host
- Ruang Admin: 10 host
- Guest Network: 50 host

### E. VLSM (Variable Length Subnet Masking) - Bonus

#### **Konsep VLSM**
- **Definisi**: Menggunakan subnet mask yang berbeda-beda sesuai kebutuhan
- **Keuntungan**: Efisiensi penggunaan IP address
- **Prinsip**: Alokasi dari kebutuhan terbesar ke terkecil

#### **Contoh VLSM**
Network: 172.16.0.0/16

**Kebutuhan**:
- Departemen A: 2000 host → /21 (2046 host)
- Departemen B: 1000 host → /22 (1022 host)
- Departemen C: 500 host → /23 (510 host)
- Point-to-Point Links: 2 host → /30 (2 host)

**Alokasi**:
```
Dept A: 172.16.0.0/21   (172.16.0.1 - 172.16.7.254)
Dept B: 172.16.8.0/22   (172.16.8.1 - 172.16.11.254)
Dept C: 172.16.12.0/23  (172.16.12.1 - 172.16.13.254)
P2P 1:  172.16.14.0/30  (172.16.14.1 - 172.16.14.2)
P2P 2:  172.16.14.4/30  (172.16.14.5 - 172.16.14.6)
```

### Mengapa IP Addressing Penting untuk Security?

1. **Network Segmentation**: Memisahkan traffic berdasarkan security zone
2. **Access Control**: Firewall rules berdasarkan IP range
3. **Monitoring**: Tracking aktivitas berdasarkan IP address
4. **Incident Response**: Identifikasi sumber serangan
5. **Compliance**: Audit trail dan logging

---

## 🎯 **SESI 2: Teknologi Serat Optik Terkini (60 menit)**

### A. Prinsip Kerja Serat Optik (20 menit)
- **Dasar Fisika Fiber Optic**:
  - Total Internal Reflection
  - Core, Cladding, dan Coating
  - Transmisi cahaya melalui serat optik
  
- **Keunggulan Fiber Optic**:
  - Bandwidth tinggi (hingga Terabit/s)
  - Jarak transmisi jauh tanpa repeater
  - Immune terhadap interferensi elektromagnetik
  - Keamanan tinggi (sulit disadap)

### B. Jenis-jenis Kabel Fiber Optic (25 menit)
- **Single-mode Fiber (SMF)**:
  - Core diameter: 8-10 μm
  - Jarak transmisi: hingga 100+ km
  - Aplikasi: Long-haul, backbone networks
  
- **Multi-mode Fiber (MMF)**:
  - Core diameter: 50-62.5 μm
  - Jarak transmisi: hingga 2 km
  - Aplikasi: LAN, data centers

### C. Teknologi Fiber Optic Terkini (15 menit)
- **DWDM (Dense Wavelength Division Multiplexing)**:
  - Multiplexing multiple wavelengths
  - Kapasitas hingga 160+ channels
  
- **GPON (Gigabit Passive Optical Network)**:
  - Fiber-to-the-Home (FTTH)
  - Shared bandwidth architecture
  
- **FTTx Technologies**:
  - FTTH (Fiber to the Home)
  - FTTB (Fiber to the Building)
  - FTTC (Fiber to the Curb)

---

## 🎯 **SESI 3: Competitive Analysis Review (15 menit)**

### Competitive Analysis Presentation
**Format:** Setiap kelompok mempresentasikan hasil competitive analysis mereka

**Presentation Structure (3 menit per kelompok):**
1. **Problem Recap** (30 detik)
2. **Solutions Analyzed** (1 menit)
3. **Key Findings** (1 menit)
4. **Gaps & Opportunities** (30 detik)

### Insight Synthesis Workshop
**Objective:** Mengidentifikasi common patterns dan innovation opportunities

#### **Gap Analysis Matrix**
```
┌─────────────────────────────────────────────────────────────────┐
│                    COMPETITIVE GAP ANALYSIS                    │
├─────────────────┬─────────────────┬─────────────────┬───────────┤
│   FEATURE/      │   SOLUTION 1    │   SOLUTION 2    │ SOLUTION 3│
│  CAPABILITY     │                 │                 │           │
├─────────────────┼─────────────────┼─────────────────┼───────────┤
│ User-Friendly   │ ✓ Good          │ ✗ Complex       │ ✓ Excellent│
│ Interface       │                 │                 │           │
├─────────────────┼─────────────────┼─────────────────┼───────────┤
│ Real-time       │ ✗ Limited       │ ✓ Good          │ ✗ None    │
│ Monitoring      │                 │                 │           │
├─────────────────┼─────────────────┼─────────────────┼───────────┤
│ Automated       │ ✓ Basic         │ ✓ Advanced      │ ✗ Manual  │
│ Response        │                 │                 │           │
├─────────────────┼─────────────────┼─────────────────┼───────────┤
│ Cost            │ $$$ High        │ $$ Medium       │ $ Low     │
│ Effectiveness   │                 │                 │           │
├─────────────────┼─────────────────┼─────────────────┼───────────┤
│ SME Suitability │ ✗ Too Complex   │ ✓ Good Fit      │ ✓ Perfect │
└─────────────────┴─────────────────┴─────────────────┴───────────┘

🔍 KEY GAPS IDENTIFIED:
• Lack of affordable enterprise-grade security for SMEs
• Poor integration between security tools
• Complex configuration requiring expert knowledge
• Limited customization for specific industries
• Inadequate user training and support
```

### Innovation Opportunity Identification
**Brainstorm Session:** Berdasarkan gaps yang teridentifikasi

**Innovation Opportunities:**
1. **Simplified Security Management**
   - One-click security configuration
   - AI-powered threat detection
   - Automated policy enforcement

2. **Industry-Specific Solutions**
   - Education sector security package
   - Healthcare compliance bundle
   - Retail PCI-DSS compliance

3. **Cost-Effective Enterprise Features**
   - Cloud-based security services
   - Subscription-based pricing
   - Scalable security architecture

---

## 🔒 **SESI 4: Security Framework Development (25 menit)**

### Security Requirements Hierarchy

#### **Level 1: Fundamental Security (Must Have)**
```
┌─────────────────────────────────────────────────────────────────┐
│                    FUNDAMENTAL SECURITY                        │
├─────────────────────────────────────────────────────────────────┤
│ 🛡️  PERIMETER SECURITY                                          │
│ • Firewall with basic rules                                     │
│ • Network segmentation                                          │
│ • VPN for remote access                                         │
│ • Intrusion detection system (IDS)                             │
│                                                                 │
│ 🔐  ACCESS CONTROL                                              │
│ • User authentication (multi-factor)                           │
│ • Role-based access control (RBAC)                             │
│ • Password policy enforcement                                   │
│ • Session management                                            │
│                                                                 │
│ 🦠  ENDPOINT PROTECTION                                         │
│ • Antivirus/anti-malware                                       │
│ • Endpoint detection and response (EDR)                        │
│ • Patch management                                              │
│ • Device compliance checking                                    │
│                                                                 │
│ 💾  DATA PROTECTION                                             │
│ • Data encryption (at rest and in transit)                     │
│ • Regular backups                                               │
│ • Data loss prevention (DLP)                                   │
│ • Secure file sharing                                           │
└─────────────────────────────────────────────────────────────────┘
```

#### **Level 2: Advanced Security (Should Have)**
```
┌─────────────────────────────────────────────────────────────────┐
│                     ADVANCED SECURITY                          │
├─────────────────────────────────────────────────────────────────┤
│ 🔍  THREAT INTELLIGENCE                                         │
│ • Security information and event management (SIEM)             │
│ • Threat hunting capabilities                                   │
│ • Vulnerability assessment                                      │
│ • Security analytics and reporting                              │
│                                                                 │
│ 🚨  INCIDENT RESPONSE                                           │
│ • Automated incident detection                                  │
│ • Incident response playbooks                                   │
│ • Forensic capabilities                                         │
│ • Communication and escalation procedures                       │
│                                                                 │
│ 📊  COMPLIANCE & GOVERNANCE                                     │
│ • Regulatory compliance monitoring                              │
│ • Security policy management                                    │
│ • Audit trail and logging                                       │
│ • Risk assessment and management                                │
└─────────────────────────────────────────────────────────────────┘
```

#### **Level 3: Enterprise Security (Could Have)**
```
┌─────────────────────────────────────────────────────────────────┐
│                    ENTERPRISE SECURITY                         │
├─────────────────────────────────────────────────────────────────┤
│ 🤖  AI-POWERED SECURITY                                         │
│ • Machine learning threat detection                             │
│ • Behavioral analytics                                          │
│ • Predictive security modeling                                  │
│ • Automated response and remediation                            │
│                                                                 │
│ 🌐  ZERO TRUST ARCHITECTURE                                     │
│ • Identity-centric security                                     │
│ • Micro-segmentation                                            │
│ • Continuous verification                                       │
│ • Least privilege access                                        │
│                                                                 │
│ ☁️   CLOUD SECURITY                                             │
│ • Cloud access security broker (CASB)                          │
│ • Container security                                            │
│ • Serverless security                                           │
│ • Multi-cloud security management                               │
└─────────────────────────────────────────────────────────────────┘
```

### Security Architecture Design Workshop

**Activity:** Design security architecture untuk specific use case

**Use Cases untuk dipilih:**
1. **Small Business (20-50 employees)**
   - Budget: $5,000-15,000
   - Primary concerns: Cost, simplicity, basic protection
   - Key assets: Customer data, financial records

2. **Educational Institution (500-1000 users)**
   - Budget: $20,000-50,000
   - Primary concerns: Student safety, compliance, content filtering
   - Key assets: Student records, research data

3. **Healthcare Clinic (50-200 employees)**
   - Budget: $15,000-30,000
   - Primary concerns: HIPAA compliance, patient privacy
   - Key assets: Patient records, medical devices

**Architecture Design Template:**
```
┌─────────────────────────────────────────────────────────────────┐
│                    SECURITY ARCHITECTURE                       │
├─────────────────────────────────────────────────────────────────┤
│ ORGANIZATION: _______________________________________________    │
│ BUDGET: ____________________________________________________     │
│ USERS: _____________________________________________________     │
│ KEY ASSETS: ________________________________________________     │
├─────────────────────────────────────────────────────────────────┤
│ SECURITY LAYERS:                                                │
│                                                                 │
│ 🌐 NETWORK LAYER:                                               │
│ • ___________________________________________________________    │
│ • ___________________________________________________________    │
│                                                                 │
│ 💻 ENDPOINT LAYER:                                              │
│ • ___________________________________________________________    │
│ • ___________________________________________________________    │
│                                                                 │
│ 👤 IDENTITY LAYER:                                              │
│ • ___________________________________________________________    │
│ • ___________________________________________________________    │
│                                                                 │
│ 📊 DATA LAYER:                                                  │
│ • ___________________________________________________________    │
│ • ___________________________________________________________    │
│                                                                 │
│ 🔍 MONITORING LAYER:                                            │
│ • ___________________________________________________________    │
│ • ___________________________________________________________    │
├─────────────────────────────────────────────────────────────────┤
│ IMPLEMENTATION PRIORITY:                                        │
│ Phase 1 (Month 1-2): ______________________________________     │
│ Phase 2 (Month 3-4): ______________________________________     │
│ Phase 3 (Month 5-6): ______________________________________     │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📋 **SESI 4: Compliance & Standards Analysis (15 menit)**

### Industry Standards Overview

#### **International Standards**

**ISO 27001 - Information Security Management**
- **Scope:** Comprehensive information security framework
- **Key Requirements:**
  - Risk assessment and management
  - Security policy development
  - Incident management procedures
  - Continuous improvement process
- **Applicability:** All organizations, especially those handling sensitive data

**NIST Cybersecurity Framework**
- **Core Functions:** Identify, Protect, Detect, Respond, Recover
- **Implementation Tiers:** Partial, Risk Informed, Repeatable, Adaptive
- **Profiles:** Current state vs target state
- **Applicability:** Government agencies, critical infrastructure

#### **Industry-Specific Regulations**

**PCI DSS (Payment Card Industry)**
- **Requirements:**
  - Build and maintain secure networks
  - Protect cardholder data
  - Maintain vulnerability management program
  - Implement strong access control measures
  - Regularly monitor and test networks
  - Maintain information security policy

**HIPAA (Healthcare)**
- **Security Rule Requirements:**
  - Administrative safeguards
  - Physical safeguards
  - Technical safeguards
  - Organizational requirements

**FERPA (Education)**
- **Privacy Requirements:**
  - Student record protection
  - Access control and audit
  - Data sharing restrictions
  - Breach notification procedures

### Compliance Mapping Exercise

**Instructions:**
1. Pilih satu industry standard yang relevan dengan use case Anda
2. Map security requirements ke compliance requirements
3. Identify gaps yang perlu diaddress
4. Prioritize compliance activities

**Compliance Mapping Template:**
```
┌─────────────────────────────────────────────────────────────────┐
│                    COMPLIANCE MAPPING                          │
├─────────────────────────────────────────────────────────────────┤
│ STANDARD: __________________________________________________     │
│ ORGANIZATION TYPE: _________________________________________     │
├─────────────────────────────────────────────────────────────────┤
│ REQUIREMENT │ CURRENT STATE │ TARGET STATE │ GAP │ PRIORITY │
├─────────────┼───────────────┼──────────────┼─────┼──────────┤
│             │               │              │     │          │
│             │               │              │     │          │
│             │               │              │     │          │
├─────────────────────────────────────────────────────────────────┤
│ COMPLIANCE ROADMAP:                                             │
│ Q1: ________________________________________________________     │
│ Q2: ________________________________________________________     │
│ Q3: ________________________________________________________     │
│ Q4: ________________________________________________________     │
└─────────────────────────────────────────────────────────────────┘
```

---

## ⚙️ **SESI 5: Technical Specifications Development (20 menit)**

### Network Security Technical Specs

#### **Firewall Specifications**
```
┌─────────────────────────────────────────────────────────────────┐
│                    FIREWALL REQUIREMENTS                       │
├─────────────────────────────────────────────────────────────────┤
│ PERFORMANCE REQUIREMENTS:                                       │
│ • Throughput: _____________ Mbps                                │
│ • Concurrent Sessions: _____________ sessions                   │
│ • New Sessions/sec: _____________ sessions                      │
│ • Latency: < _____________ ms                                   │
│                                                                 │
│ FEATURE REQUIREMENTS:                                           │
│ • Stateful packet inspection: ☐ Required ☐ Optional            │
│ • Deep packet inspection: ☐ Required ☐ Optional                │
│ • Application control: ☐ Required ☐ Optional                   │
│ • URL filtering: ☐ Required ☐ Optional                         │
│ • Intrusion prevention: ☐ Required ☐ Optional                  │
│ • VPN support: ☐ Required ☐ Optional                           │
│                                                                 │
│ MANAGEMENT REQUIREMENTS:                                        │
│ • Web-based GUI: ☐ Required ☐ Optional                         │
│ • CLI access: ☐ Required ☐ Optional                            │
│ • SNMP monitoring: ☐ Required ☐ Optional                       │
│ • Centralized management: ☐ Required ☐ Optional                │
│ • API integration: ☐ Required ☐ Optional                       │
└─────────────────────────────────────────────────────────────────┘
```

#### **Network Access Control (NAC) Specifications**
```
┌─────────────────────────────────────────────────────────────────┐
│                    NAC REQUIREMENTS                            │
├─────────────────────────────────────────────────────────────────┤
│ AUTHENTICATION METHODS:                                         │
│ • 802.1X: ☐ Required ☐ Optional                                │
│ • MAC address authentication: ☐ Required ☐ Optional            │
│ • Web portal authentication: ☐ Required ☐ Optional             │
│ • Certificate-based auth: ☐ Required ☐ Optional                │
│                                                                 │
│ DEVICE COMPLIANCE:                                              │
│ • Antivirus status check: ☐ Required ☐ Optional                │
│ • OS patch level verification: ☐ Required ☐ Optional           │
│ • Device registration: ☐ Required ☐ Optional                   │
│ • Guest network isolation: ☐ Required ☐ Optional               │
│                                                                 │
│ POLICY ENFORCEMENT:                                             │
│ • VLAN assignment: ☐ Required ☐ Optional                       │
│ • Bandwidth limitation: ☐ Required ☐ Optional                  │
│ • Time-based access: ☐ Required ☐ Optional                     │
│ • Application restrictions: ☐ Required ☐ Optional              │
└─────────────────────────────────────────────────────────────────┘
```

#### **SIEM System Specifications**
```
┌─────────────────────────────────────────────────────────────────┐
│                    SIEM REQUIREMENTS                           │
├─────────────────────────────────────────────────────────────────┤
│ LOG COLLECTION:                                                 │
│ • Events per second: _____________ EPS                          │
│ • Log sources supported: _____________ types                    │
│ • Log retention period: _____________ months                    │
│ • Real-time processing: ☐ Required ☐ Optional                  │
│                                                                 │
│ ANALYSIS CAPABILITIES:                                          │
│ • Correlation rules: ☐ Required ☐ Optional                     │
│ • Behavioral analytics: ☐ Required ☐ Optional                  │
│ • Threat intelligence integration: ☐ Required ☐ Optional       │
│ • Machine learning: ☐ Required ☐ Optional                      │
│                                                                 │
│ REPORTING & ALERTING:                                           │
│ • Real-time alerts: ☐ Required ☐ Optional                      │
│ • Custom dashboards: ☐ Required ☐ Optional                     │
│ • Compliance reports: ☐ Required ☐ Optional                    │
│ • Executive summaries: ☐ Required ☐ Optional                   │
└─────────────────────────────────────────────────────────────────┘
```

### Technical Specification Workshop

**Activity:** Develop detailed technical specs untuk chosen security solution

**Steps:**
1. **Solution Selection** (5 menit)
   - Pilih 1 security component dari architecture design
   - Focus pada component yang paling critical

2. **Requirement Gathering** (10 menit)
   - Performance requirements
   - Functional requirements
   - Integration requirements
   - Management requirements

3. **Specification Documentation** (5 menit)
   - Use provided templates
   - Include specific metrics and criteria
   - Define acceptance criteria

---

## 🎯 **SESI 6: Requirements Validation & Prioritization (10 menit)**

### Requirements Validation Framework

#### **SMART Criteria Check**
```
┌─────────────────────────────────────────────────────────────────┐
│                    REQUIREMENTS VALIDATION                     │
├─────────────────────────────────────────────────────────────────┤
│ REQUIREMENT: _______________________________________________     │
├─────────────────────────────────────────────────────────────────┤
│ ✓ SPECIFIC: Is it clearly defined and unambiguous?             │
│   ☐ Yes ☐ No ☐ Needs improvement                               │
│   Notes: ___________________________________________________     │
│                                                                 │
│ ✓ MEASURABLE: Can success be quantified?                       │
│   ☐ Yes ☐ No ☐ Needs improvement                               │
│   Metrics: _________________________________________________     │
│                                                                 │
│ ✓ ACHIEVABLE: Is it realistic given constraints?               │
│   ☐ Yes ☐ No ☐ Needs improvement                               │
│   Constraints: _____________________________________________     │
│                                                                 │
│ ✓ RELEVANT: Does it address user needs?                        │
│   ☐ Yes ☐ No ☐ Needs improvement                               │
│   User impact: _____________________________________________     │
│                                                                 │
│ ✓ TIME-BOUND: Is there a clear timeline?                       │
│   ☐ Yes ☐ No ☐ Needs improvement                               │
│   Timeline: ________________________________________________     │
└─────────────────────────────────────────────────────────────────┘
```

### Requirements Prioritization Matrix

#### **Value vs Complexity Matrix**
```
                    REQUIREMENTS PRIORITIZATION

    High │                    │                    │
   Value │     QUICK WINS     │   MAJOR PROJECTS   │
         │   (Do First)       │   (Plan Carefully) │
         │                    │                    │
         ├────────────────────┼────────────────────┤
         │                    │                    │
         │    FILL-INS        │   QUESTIONABLE     │
         │   (Do Later)       │   (Reconsider)     │
    Low  │                    │                    │
   Value │                    │                    │
         └────────────────────┴────────────────────┘
           Low Complexity              High Complexity
```

#### **Prioritization Scoring**

**Value Score (1-5):**
- **5:** Critical for security, high user impact
- **4:** Important for operations, medium user impact
- **3:** Useful feature, some user benefit
- **2:** Nice to have, minimal impact
- **1:** Low priority, questionable value

**Complexity Score (1-5):**
- **5:** Very complex, requires significant resources
- **4:** Complex, needs specialized skills
- **3:** Moderate complexity, standard implementation
- **2:** Simple, straightforward implementation
- **1:** Very simple, minimal effort required

### Group Exercise: Requirements Prioritization

**Instructions:**
1. List all security requirements dari architecture design
2. Score each requirement untuk Value dan Complexity
3. Plot pada prioritization matrix
4. Identify implementation sequence
5. Create roadmap dengan timeline

---

## 📊 **SESI 7: Final Requirements Documentation (10 menit)**

### Security Requirements Document (SRD) Template

```
┌─────────────────────────────────────────────────────────────────┐
│                SECURITY REQUIREMENTS DOCUMENT                  │
├─────────────────────────────────────────────────────────────────┤
│ PROJECT: ___________________________________________________     │
│ VERSION: ___________________________________________________     │
│ DATE: ______________________________________________________     │
│ AUTHOR: ____________________________________________________     │
├─────────────────────────────────────────────────────────────────┤
│ 1. EXECUTIVE SUMMARY                                            │
│ _______________________________________________________________  │
│ _______________________________________________________________  │
│                                                                 │
│ 2. BUSINESS REQUIREMENTS                                        │
│ • Primary Objectives: _____________________________________     │
│ • Success Criteria: _______________________________________     │
│ • Constraints: ____________________________________________     │
│                                                                 │
│ 3. FUNCTIONAL REQUIREMENTS                                      │
│ FR-001: ___________________________________________________     │
│ FR-002: ___________________________________________________     │
│ FR-003: ___________________________________________________     │
│                                                                 │
│ 4. NON-FUNCTIONAL REQUIREMENTS                                  │
│ • Performance: ____________________________________________     │
│ • Security: _______________________________________________     │
│ • Scalability: ____________________________________________     │
│ • Reliability: ____________________________________________     │
│ • Usability: ______________________________________________     │
│                                                                 │
│ 5. COMPLIANCE REQUIREMENTS                                      │
│ • Standards: ______________________________________________     │
│ • Regulations: ____________________________________________     │
│ • Certifications: _________________________________________     │
│                                                                 │
│ 6. IMPLEMENTATION ROADMAP                                       │
│ Phase 1 (Q1): _____________________________________________     │
│ Phase 2 (Q2): _____________________________________________     │
│ Phase 3 (Q3): _____________________________________________     │
│ Phase 4 (Q4): _____________________________________________     │
│                                                                 │
│ 7. ACCEPTANCE CRITERIA                                          │
│ • Testing Requirements: ___________________________________     │
│ • Performance Benchmarks: _________________________________     │
│ • Security Validation: ____________________________________     │
└─────────────────────────────────────────────────────────────────┘
```

### Documentation Quality Checklist

**Completeness Check:**
- [ ] All user needs addressed
- [ ] Technical specifications defined
- [ ] Compliance requirements included
- [ ] Implementation timeline specified
- [ ] Acceptance criteria clear

**Clarity Check:**
- [ ] Requirements are unambiguous
- [ ] Technical terms defined
- [ ] Assumptions documented
- [ ] Dependencies identified
- [ ] Risks acknowledged

**Consistency Check:**
- [ ] No conflicting requirements
- [ ] Consistent terminology used
- [ ] Aligned with business objectives
- [ ] Compatible with constraints
- [ ] Traceable to user needs

---

## 🔄 **REFLECTION & WRAP-UP (5 menit)**

### Define Phase Completion Assessment

**Self-Assessment Questions:**
1. Apakah problem statement kami jelas dan actionable?
2. Apakah security requirements comprehensive dan realistic?
3. Apakah technical specifications cukup detail untuk implementation?
4. Apakah compliance requirements sudah dipertimbangkan?
5. Apakah prioritization masuk akal berdasarkan value dan complexity?

### Key Learnings Reflection

**Complete these statements:**

1. **"Hal terpenting yang saya pelajari tentang defining security requirements adalah..."**
   _________________________________________________

2. **"Tantangan terbesar dalam menerjemahkan user needs menjadi technical specs adalah..."**
   _________________________________________________

3. **"Untuk fase Ideate besok, saya perlu fokus pada..."**
   _________________________________________________

### Preview Day 5 (Ideate Phase)
"Besok kita akan masuk ke fase IDEATE, di mana kita akan brainstorm berbagai solusi kreatif untuk requirements yang sudah kita definisikan. Kita akan menggunakan berbagai teknik ideation untuk menghasilkan innovative network security solutions."

---

## 📚 **DELIVERABLES & HOMEWORK**

### Day 4 Deliverables:
1. **Poster Perbandingan Jenis-jenis Kabel FO** (individual)
2. **Competitive Analysis Summary**
3. **Security Architecture Design**
4. **Compliance Mapping Document**
5. **Technical Specifications**
6. **Security Requirements Document (SRD)**
7. **Implementation Roadmap**
8. **Fiber Optic Security Analysis** (group)

### Homework Assignment: "Technology Research"
**Objective:** Research emerging technologies yang bisa diintegrasikan dalam solution

**Instructions:**
Research 3 emerging technologies dalam network security:

1. **AI/Machine Learning in Cybersecurity**
   - Current applications
   - Benefits and limitations
   - Implementation considerations
   - Cost implications

2. **Zero Trust Architecture**
   - Core principles
   - Implementation approaches
   - Technology requirements
   - Migration strategies

3. **Cloud Security Solutions**
   - Service models (SaaS, PaaS, IaaS)
   - Security advantages
   - Integration challenges
   - Vendor comparison

**Deliverable Format:**
- 2-page summary per technology
- Include diagrams/infographics
- Pros and cons analysis
- Relevance to your project
- Implementation feasibility

### Research Resources:
- Gartner Magic Quadrant reports
- Vendor whitepapers
- Industry analyst reports
- Technical blogs and forums
- Academic research papers

---

## 🛠️ **TOOLS & TEMPLATES**

### Available Templates:
- [ ] Competitive Gap Analysis Matrix
- [ ] Security Architecture Template
- [ ] Compliance Mapping Template
- [ ] Technical Specifications Template
- [ ] Requirements Validation Checklist
- [ ] Security Requirements Document Template

### Recommended Tools:
- **Lucidchart/Draw.io:** For architecture diagrams
- **Microsoft Visio:** For technical diagrams
- **Confluence/Notion:** For documentation
- **Jira:** For requirements tracking
- **Excel/Google Sheets:** For analysis matrices

---

*"Requirements are like water. If you don't contain them, they will find a way to leak into your project and flood it." - Unknown*

*"The bitterness of poor quality remains long after the sweetness of low price is forgotten." - Benjamin Franklin*