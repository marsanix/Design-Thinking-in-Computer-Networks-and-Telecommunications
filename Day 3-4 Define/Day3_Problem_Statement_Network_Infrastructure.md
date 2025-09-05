# Day 3: IPv6 Technology & Problem Statement - Network Infrastructure Challenges
## Fase Define - Mendefinisikan Masalah dengan Presisi

### Tujuan Pembelajaran
Setelah sesi ini, peserta akan mampu:
1. Memahami konsep IPv6 dan perbedaannya dengan IPv4
2. Menganalisis keterbatasan IPv4 sebagai problem statement
3. Menganalisis user research findings untuk mengidentifikasi core problems
4. Menggunakan framework problem definition untuk network infrastructure
5. Membuat problem statement yang actionable dan measurable
6. Memahami root cause analysis dalam konteks network security
7. Memprioritaskan masalah berdasarkan impact dan feasibility
8. Melakukan konfigurasi dasar IPv6 di Cisco Packet Tracer

---

## 📚 **SESI 1: Dasar Komunikasi Jaringan - OSI dan TCP/IP Models (45 menit)**

### Mengapa Perlu Memahami Model Jaringan?

Sebelum mempelajari IPv6, kita perlu memahami bagaimana komunikasi jaringan bekerja. Bayangkan seperti mengirim surat:
- Kita perlu alamat yang jelas (IP Address)
- Perlu cara pengiriman (Protocol)
- Perlu aturan bagaimana surat dikemas (Encapsulation)

### A. OSI Model (Open Systems Interconnection) - 20 menit

#### **Konsep Dasar OSI Model**
OSI Model adalah kerangka kerja 7 layer yang menjelaskan bagaimana data bergerak dari satu komputer ke komputer lain melalui jaringan.

#### **7 Layer OSI Model (dari atas ke bawah):**

**Layer 7 - Application Layer** 🌐
- **Fungsi**: Interface antara user dan jaringan
- **Contoh**: Web browser, email client, FTP
- **Protokol**: HTTP, HTTPS, SMTP, POP3, FTP
- **Analogi**: Seperti aplikasi yang kita gunakan sehari-hari

**Layer 6 - Presentation Layer** 🎭
- **Fungsi**: Enkripsi, kompresi, format data
- **Contoh**: SSL/TLS encryption, JPEG, MP3
- **Analogi**: Seperti penerjemah bahasa

**Layer 5 - Session Layer** 🤝
- **Fungsi**: Membuat, mengelola, dan mengakhiri sesi komunikasi
- **Contoh**: SQL sessions, NetBIOS
- **Analogi**: Seperti operator telepon yang menghubungkan panggilan

**Layer 4 - Transport Layer** 🚛
- **Fungsi**: Pengiriman data yang reliable, flow control
- **Protokol**: TCP (reliable), UDP (fast)
- **Analogi**: Seperti jasa pengiriman paket (JNE, TIKI)

**Layer 3 - Network Layer** 🗺️
- **Fungsi**: Routing, logical addressing (IP)
- **Protokol**: IP, ICMP, OSPF, BGP
- **Device**: Router
- **Analogi**: Seperti GPS yang menentukan rute terbaik

**Layer 2 - Data Link Layer** 🔗
- **Fungsi**: Frame formatting, error detection, MAC addressing
- **Protokol**: Ethernet, WiFi (802.11)
- **Device**: Switch, Bridge
- **Analogi**: Seperti amplop surat dengan alamat lokal

**Layer 1 - Physical Layer** ⚡
- **Fungsi**: Transmisi bit melalui media fisik
- **Contoh**: Kabel UTP, Fiber optic, Radio waves
- **Device**: Hub, Repeater, Kabel
- **Analogi**: Seperti jalan raya tempat kendaraan lewat

#### **Mnemonik untuk Menghapal OSI:**
**"All People Seem To Need Data Processing"**
- **A**pplication
- **P**resentation  
- **S**ession
- **T**ransport
- **N**etwork
- **D**ata Link
- **P**hysical

### B. TCP/IP Model - 15 menit

#### **Konsep TCP/IP Model**
TCP/IP adalah model praktis yang digunakan di Internet. Lebih sederhana dari OSI dengan 4 layer.

#### **4 Layer TCP/IP Model:**

**Layer 4 - Application Layer** 📱
- **Setara OSI**: Layer 5, 6, 7
- **Fungsi**: Semua fungsi aplikasi, presentasi, dan sesi
- **Protokol**: HTTP, HTTPS, FTP, SMTP, DNS, DHCP
- **Contoh**: Web browsing, email, file transfer

**Layer 3 - Transport Layer** 🚚
- **Setara OSI**: Layer 4
- **Protokol**: TCP, UDP
- **TCP**: Connection-oriented, reliable, slower
- **UDP**: Connectionless, fast, less reliable
- **Port Numbers**: Mengidentifikasi aplikasi (HTTP=80, HTTPS=443)

**Layer 2 - Internet Layer** 🌍
- **Setara OSI**: Layer 3
- **Protokol**: IP (IPv4/IPv6), ICMP, ARP
- **Fungsi**: Routing antar network
- **IP Address**: Alamat logical untuk identifikasi device

**Layer 1 - Network Access Layer** 🔌
- **Setara OSI**: Layer 1, 2
- **Fungsi**: Akses ke media fisik dan data link
- **Teknologi**: Ethernet, WiFi, PPP
- **MAC Address**: Alamat fisik network card

### C. Perbandingan OSI vs TCP/IP - 5 menit

| Aspek | OSI Model | TCP/IP Model |
|-------|-----------|-------------|
| **Jumlah Layer** | 7 Layer | 4 Layer |
| **Penggunaan** | Teoritis, referensi | Praktis, implementasi |
| **Fleksibilitas** | Sangat detail | Lebih sederhana |
| **Adoption** | Standard referensi | Internet standard |
| **Troubleshooting** | Sangat detail | Cukup untuk praktis |

### D. Aktivitas Praktis: "Data Journey" - 5 menit

**Skenario**: Siswa mengirim email dari komputer sekolah ke Gmail

**Tugas Kelompok**:
1. Trace perjalanan data melalui OSI layers
2. Identifikasi protokol di setiap layer
3. Jelaskan apa yang terjadi di setiap layer

**Contoh Jawaban**:
- **Layer 7**: User menulis email di aplikasi email
- **Layer 6**: Email di-encode dalam format MIME
- **Layer 5**: Sesi SMTP dibuat dengan mail server
- **Layer 4**: TCP memastikan email terkirim reliable
- **Layer 3**: IP routing menentukan jalur ke Gmail server
- **Layer 2**: Ethernet frame membawa data di LAN sekolah
- **Layer 1**: Sinyal listrik melalui kabel UTP

### Mengapa OSI/TCP-IP Penting untuk IPv6?

1. **Layer 3 (Network)**: IPv6 bekerja di layer ini
2. **Addressing**: Memahami logical vs physical addressing
3. **Routing**: IPv6 routing protocols
4. **Troubleshooting**: Systematic approach untuk problem solving
5. **Security**: IPSec built-in di IPv6 (Layer 3)

---

## 🎯 **SESI 2: Teknologi IPv6 - Solusi untuk Keterbatasan IPv4 (60 menit)**

### A. Keterbatasan IPv4 sebagai Problem Statement (20 menit)
- **Address Exhaustion**: 
  - IPv4 hanya menyediakan ~4.3 miliar alamat
  - Pertumbuhan Internet dan IoT membutuhkan lebih banyak alamat
  - NAT sebagai solusi sementara dengan keterbatasan
  
- **Masalah Teknis IPv4**:
  - Fragmentasi paket
  - Broadcast storms
  - Konfigurasi manual yang kompleks
  - Keamanan yang tidak built-in

### B. Struktur dan Keunggulan IPv6 (25 menit)
- **Struktur Alamat IPv6**:
  - 128-bit address space (340 undecillion alamat)
  - Format: 8 grup 4 digit hexadecimal
  - Contoh: 2001:0db8:85a3:0000:0000:8a2e:0370:7334
  
- **Keunggulan IPv6**:
  - Auto-configuration (SLAAC)
  - Built-in security (IPSec)
  - Improved QoS support
  - Eliminasi NAT
  - Multicast yang lebih efisien

### C. Praktikum IPv6 di Packet Tracer (15 menit)
- **Basic IPv6 Configuration**:
  - Enable IPv6 pada router
  - Konfigurasi IPv6 address pada interface
  - Verifikasi konektivitas dengan ping

---

## 🎯 **SESI 3: Review & Synthesis User Research (15 menit)**

### User Research Findings Gallery Walk
**Setup:** Setiap kelompok menampilkan hasil user research mereka di dinding kelas

**Materials yang ditampilkan:**
- User personas
- Empathy maps
- Pain points summary (termasuk IPv4 limitations)
- Security incident research
- Stakeholder analysis

### Insight Clustering Activity
**Objective:** Mengidentifikasi pola dan tema dari semua user research

**Process:**
1. **Individual Review (5 menit):** Setiap peserta review semua findings
2. **Sticky Note Insights (5 menit):** Tulis 1 insight per sticky note
3. **Clustering (5 menit):** Kelompokkan insights yang serupa

**Insight Categories yang Muncul:**
```
┌─────────────────┬─────────────────┬─────────────────┬─────────────────┐
│   PERFORMANCE   │    SECURITY     │   USABILITY     │      COST       │
│                 │                 │                 │                 │
│ • Slow network  │ • Virus attacks │ • Complex UI    │ • Budget limits │
│ • Downtime      │ • Data breaches │ • Too many      │ • ROI unclear   │
│ • Bandwidth     │ • Unauthorized  │   passwords     │ • Hidden costs  │
│   issues        │   access        │ • Poor UX       │ • Maintenance   │
│ • Latency       │ • Compliance    │ • Training gap  │   expensive     │
│ • IPv4 limits   │ • No IPSec      │ • NAT complexity│ • IPv6 migration│
└─────────────────┴─────────────────┴─────────────────┴─────────────────┘
```

---

## 🔍 **SESI 4: Root Cause Analysis Framework (20 menit)**

### The "5 Whys" Technique untuk Network Problems

#### **Example: "WiFi Lambat di Kantor"

**Problem:** WiFi lambat di kantor pada jam sibuk

1. **Why?** Bandwidth tidak cukup untuk semua user
   
2. **Why?** Banyak user streaming video dan download file besar
   
3. **Why?** Tidak ada policy untuk bandwidth management
   
4. **Why?** IT team tidak aware tentang usage patterns
   
5. **Why?** Tidak ada monitoring tools untuk network traffic

**Root Cause:** Kurangnya visibility dan control terhadap network usage

**Solution Direction:** Implement network monitoring dan bandwidth management system

---

### Fishbone Diagram untuk Network Security Issues

```
                    NETWORK SECURITY BREACH
                           │
        ┌──────────────────┼──────────────────┐
        │                  │                  │
    PEOPLE              PROCESS           TECHNOLOGY
        │                  │                  │
   ┌────┴────┐        ┌────┴────┐        ┌────┴────┐
   │ Lack of │        │ No      │        │ Outdated│
   │ training│        │ security│        │ firewall│
   │         │        │ policy  │        │         │
   │ Poor    │        │         │        │ Weak    │
   │ password│        │ No      │        │ encryption│
   │ habits  │        │ incident│        │         │
   │         │        │ response│        │ No IDS  │
   └─────────┘        └─────────┘        └─────────┘
        │                  │                  │
        │                  │                  │
   ENVIRONMENT         MATERIALS          METHODS
        │                  │                  │
   ┌────┴────┐        ┌────┴────┐        ┌────┴────┐
   │ Remote  │        │ Legacy  │        │ No      │
   │ work    │        │ systems │        │ security│
   │         │        │         │        │ testing │
   │ BYOD    │        │ Unpatched│        │         │
   │ policy  │        │ software│        │ Manual  │
   │         │        │         │        │ processes│
   └─────────┘        └─────────┘        └─────────┘
```

### Group Exercise: Root Cause Analysis
**Instructions:**
1. Pilih 1 major pain point dari user research
2. Gunakan 5 Whys technique
3. Buat fishbone diagram
4. Identifikasi root causes
5. Brainstorm potential solutions

**Common Network Problems untuk Analysis:**
- Frequent network downtime
- Slow internet speed
- Security breaches
- User access issues
- High IT support tickets

---

## 📝 **SESI 5: Problem Statement Framework (20 menit)**

### SMART Problem Statement Template

**Format:**
```
[USER SEGMENT] experiences [PROBLEM] when [CONTEXT/SITUATION] 
which causes [IMPACT] because [ROOT CAUSE].

Currently, [CURRENT SOLUTION] but this fails because [WHY IT FAILS].

Success would look like [DESIRED OUTCOME] measured by [METRICS].
```

### Example Problem Statements

#### **Problem Statement 1: SME Network Security**
```
Small business owners experience frequent malware infections 
when employees browse the internet and download files 
which causes business disruption and data loss 
because there is no comprehensive endpoint protection.

Currently, they rely on basic antivirus software 
but this fails because it doesn't provide real-time 
threat detection and user behavior monitoring.

Success would look like zero malware incidents 
measured by security event logs and user productivity metrics.
```

#### **Problem Statement 2: School Network Management**
```
School IT administrators experience overwhelming support requests 
when students and teachers cannot access educational resources 
which causes learning disruption and IT team burnout 
because the network lacks proper user authentication and content filtering.

Currently, they manually manage user access and troubleshoot issues 
but this fails because it's not scalable and reactive rather than proactive.

Success would look like 90% reduction in access-related support tickets 
measured by helpdesk metrics and user satisfaction surveys.
```

#### **Problem Statement 3: Corporate Remote Access**
```
Remote employees experience slow and unreliable VPN connections 
when working from home or traveling 
which causes reduced productivity and missed deadlines 
because the current VPN infrastructure cannot handle the increased load.

Currently, they use a legacy VPN solution with limited bandwidth 
but this fails because it wasn't designed for large-scale remote work.

Success would look like consistent high-speed remote access 
measured by connection speed tests and employee satisfaction scores.
```

---

### Problem Statement Workshop

**Step 1: Problem Identification (5 menit)**
Setiap kelompok memilih 1 core problem dari user research mereka

**Step 2: Context Mapping (5 menit)**
Identifikasi:
- Who is affected?
- When does it happen?
- Where does it occur?
- What triggers it?

**Step 3: Impact Assessment (5 menit)**
Quantify impact:
- Financial cost
- Time lost
- User frustration
- Security risk
- Operational disruption

**Step 4: Root Cause Validation (5 menit)**
Verify root cause dengan evidence dari user research

**Step 5: Success Criteria Definition (5 menit)**
Define measurable success metrics

---

## 🎯 **SESI 5: Problem Prioritization Matrix (15 menit)**

### Impact vs Effort Matrix

```
                    PROBLEM PRIORITIZATION MATRIX

    High │                    │                    │
  Impact │        QUICK       │      MAJOR         │
         │        WINS        │    PROJECTS        │
         │                    │                    │
         ├────────────────────┼────────────────────┤
         │                    │                    │
         │       FILL-INS     │   THANKLESS        │
         │                    │     TASKS          │
    Low  │                    │                    │
  Impact │                    │                    │
         └────────────────────┴────────────────────┘
           Low Effort                    High Effort
```

### Scoring Criteria

#### **Impact Score (1-5)**
- **5:** Critical business impact, affects many users
- **4:** High impact, affects key processes
- **3:** Moderate impact, noticeable but manageable
- **2:** Low impact, minor inconvenience
- **1:** Minimal impact, rarely noticed

#### **Effort Score (1-5)**
- **5:** Very high effort, requires major resources
- **4:** High effort, significant time and resources
- **3:** Moderate effort, standard project scope
- **2:** Low effort, quick implementation
- **1:** Very low effort, minimal resources needed

### Group Exercise: Problem Prioritization

**Instructions:**
1. List all identified problems
2. Score each problem for Impact (1-5)
3. Score each problem for Effort (1-5)
4. Plot on the matrix
5. Identify "Quick Wins" and "Major Projects"

**Example Problems to Prioritize:**

| Problem | Impact | Effort | Category |
|---------|--------|--------|---------|
| Implement basic firewall | 4 | 2 | Quick Win |
| Deploy SIEM solution | 5 | 5 | Major Project |
| Update password policy | 3 | 1 | Quick Win |
| Network infrastructure overhaul | 5 | 5 | Major Project |
| User security training | 4 | 2 | Quick Win |
| Implement zero-trust architecture | 5 | 5 | Major Project |

---

## 🔬 **SESI 6: Technical Requirements Analysis (15 menit)**

### From Problem to Technical Requirements

#### **Problem-to-Requirement Mapping Framework**

```
┌─────────────────────────────────────────────────────────────────┐
│                    REQUIREMENT ANALYSIS                        │
├─────────────────────────────────────────────────────────────────┤
│ USER PROBLEM:                                                   │
│ _______________________________________________________________  │
│                                                                 │
│ FUNCTIONAL REQUIREMENTS:                                        │
│ • What must the system DO?                                      │
│   - ___________________________________________________________  │
│   - ___________________________________________________________  │
│   - ___________________________________________________________  │
│                                                                 │
│ NON-FUNCTIONAL REQUIREMENTS:                                    │
│ • How well must the system perform?                             │
│   - Performance: ___________________________________________     │
│   - Security: _____________________________________________      │
│   - Scalability: __________________________________________      │
│   - Reliability: __________________________________________      │
│   - Usability: ____________________________________________      │
│                                                                 │
│ CONSTRAINTS:                                                    │
│ • What limitations exist?                                       │
│   - Budget: _______________________________________________      │
│   - Timeline: _____________________________________________      │
│   - Technology: ___________________________________________      │
│   - Skills: _______________________________________________      │
│   - Compliance: ___________________________________________      │
└─────────────────────────────────────────────────────────────────┘
```

#### **Example: WiFi Performance Problem**

**User Problem:** "WiFi lambat saat jam sibuk"

**Functional Requirements:**
- System must monitor real-time bandwidth usage
- System must implement Quality of Service (QoS) rules
- System must provide user-friendly bandwidth allocation
- System must generate usage reports

**Non-Functional Requirements:**
- **Performance:** Support 200+ concurrent users
- **Security:** WPA3 encryption, user authentication
- **Scalability:** Expandable to 500 users
- **Reliability:** 99.9% uptime
- **Usability:** Self-service portal for users

**Constraints:**
- **Budget:** Maximum $10,000
- **Timeline:** 3 months implementation
- **Technology:** Must integrate with existing infrastructure
- **Skills:** Current IT team capabilities
- **Compliance:** Educational institution policies

---

### Requirements Validation Checklist

**SMART Requirements Check:**
- [ ] **Specific:** Clearly defined and unambiguous
- [ ] **Measurable:** Can be quantified or verified
- [ ] **Achievable:** Realistic given constraints
- [ ] **Relevant:** Addresses the core problem
- [ ] **Time-bound:** Has clear timeline

**Additional Validation:**
- [ ] Traceable to user needs
- [ ] Testable and verifiable
- [ ] Consistent with other requirements
- [ ] Feasible with available resources
- [ ] Compliant with standards and regulations

---

## 📊 **SESI 7: Problem Statement Presentation (10 menit)**

### Presentation Template

**Slide 1: Problem Overview**
- Problem statement (1-2 sentences)
- Affected user segments
- Key statistics/evidence

**Slide 2: Root Cause Analysis**
- Primary root causes
- Supporting evidence
- Current failed solutions

**Slide 3: Impact Assessment**
- Business impact
- User impact
- Technical impact
- Risk assessment

**Slide 4: Success Criteria**
- Measurable outcomes
- Success metrics
- Timeline expectations

**Slide 5: Next Steps**
- Priority level
- Resource requirements
- Dependencies

### Presentation Guidelines
- **Time limit:** 3 minutes per group
- **Focus:** Clarity and evidence-based arguments
- **Audience:** Peers acting as stakeholders
- **Goal:** Get buy-in for problem importance

### Peer Feedback Framework

**Feedback Categories:**
1. **Clarity:** Is the problem clearly defined?
2. **Evidence:** Is there sufficient evidence?
3. **Impact:** Is the impact compelling?
4. **Feasibility:** Are the success criteria realistic?
5. **Priority:** Should this be high priority?

**Feedback Format:**
- 2 Stars (what worked well)
- 1 Wish (what could be improved)

---

## 🔄 **REFLECTION & WRAP-UP (5 menit)**

### Problem Definition Quality Check

**Self-Assessment Questions:**
1. Does our problem statement clearly identify WHO is affected?
2. Does it specify WHAT the problem is?
3. Does it explain WHEN/WHERE it occurs?
4. Does it describe the IMPACT?
5. Does it identify the ROOT CAUSE?
6. Are our success criteria MEASURABLE?
7. Is the problem ACTIONABLE?

### Key Learnings Reflection

**Complete these statements:**

1. **"The most important insight from today's root cause analysis was..."**
   _________________________________________________

2. **"I learned that a good problem statement must..."**
   _________________________________________________

3. **"The biggest challenge in defining network problems is..."**
   _________________________________________________

### Preview Day 4
"Besok kita akan melanjutkan fase Define dengan fokus pada Security Requirements. Kita akan mendalami bagaimana mengubah security pain points menjadi technical specifications yang dapat diimplementasikan."

---

## 📚 **DELIVERABLES & HOMEWORK**

### Day 3 Deliverables:
1. **IPv6 Configuration Lab** (Packet Tracer file dengan konfigurasi IPv6)
2. **Root Cause Analysis** (5 Whys + Fishbone Diagram)
3. **SMART Problem Statement** (final version)
4. **Problem Prioritization Matrix**
5. **Technical Requirements Document**
6. **Problem Statement Presentation**

### Homework Assignment: "Competitive Analysis"
**Objective:** Research existing solutions untuk problem yang sudah didefinisikan

**Instructions:**
1. Identify 3 existing solutions (products/services) yang address problem Anda
2. Untuk setiap solution, analyze:
   - **Features:** Apa yang ditawarkan?
   - **Strengths:** Apa kelebihan utama?
   - **Weaknesses:** Apa kekurangan atau gap?
   - **Target Users:** Siapa target market mereka?
   - **Pricing:** Berapa cost-nya?
   - **Implementation:** Seberapa mudah implementasi?

**Deliverable Format:**
```
┌─────────────────────────────────────────────────────────────────┐
│                    COMPETITIVE ANALYSIS                        │
├─────────────────────────────────────────────────────────────────┤
│ SOLUTION 1: _______________________________________________      │
│ Features: _________________________________________________      │
│ Strengths: ________________________________________________      │
│ Weaknesses: _______________________________________________      │
│ Target Users: _____________________________________________      │
│ Pricing: __________________________________________________      │
│ Implementation: ___________________________________________      │
├─────────────────────────────────────────────────────────────────┤
│ SOLUTION 2: [Same format]                                       │
├─────────────────────────────────────────────────────────────────┤
│ SOLUTION 3: [Same format]                                       │
├─────────────────────────────────────────────────────────────────┤
│ GAPS IDENTIFIED:                                                │
│ • ___________________________________________________________    │
│ • ___________________________________________________________    │
│ • ___________________________________________________________    │
├─────────────────────────────────────────────────────────────────┤
│ OPPORTUNITIES FOR INNOVATION:                                   │
│ • ___________________________________________________________    │
│ • ___________________________________________________________    │
│ • ___________________________________________________________    │
└─────────────────────────────────────────────────────────────────┘
```

### Research Resources:
- Vendor websites (Cisco, Fortinet, Palo Alto, etc.)
- Industry reports (Gartner, IDC)
- User review sites (G2, Capterra)
- Technical documentation
- Case studies

---

## 🛠️ **TOOLS & TEMPLATES**

### Available Templates:
- [ ] 5 Whys Analysis Template
- [ ] Fishbone Diagram Template
- [ ] SMART Problem Statement Template
- [ ] Impact vs Effort Matrix
- [ ] Technical Requirements Template
- [ ] Competitive Analysis Template

### Recommended Tools:
- **Miro/Mural:** For root cause analysis diagrams
- **Google Sheets:** For prioritization matrices
- **Canva:** For presentation slides
- **Notion:** For documentation

---

*"A problem well-defined is a problem half-solved." - Charles Kettering*

*"The formulation of the problem is often more essential than its solution." - Albert Einstein*