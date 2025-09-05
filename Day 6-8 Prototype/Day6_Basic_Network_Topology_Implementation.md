# Day 6: Data Center, Cloud Computing & Network Topology Implementation
## Fase: Prototype - Hands-on Implementation

### 🎯 Learning Objectives
Setelah mengikuti sesi ini, peserta akan mampu:
1. Memahami konsep Data Center dan Cloud Computing
2. Menganalisis arsitektur Data Center modern
3. Mengimplementasikan basic network topology menggunakan Cisco Packet Tracer
4. Mengkonfigurasi perangkat jaringan dasar (Router, Switch, PC)
5. Menerapkan IP addressing dan subnetting
6. Melakukan basic connectivity testing
7. Mengimplementasikan VLAN untuk network segmentation
8. Memahami konsep dasar network security dalam implementasi
9. Membuat simulasi Data Center sederhana di Packet Tracer

---

## 📋 Session Overview
**Durasi:** 60 menit  
**Format:** Hands-on Workshop  
**Tools:** Cisco Packet Tracer, Design Canvas dari Day 5  
**Deliverable:** Basic Network Topology dengan dokumentasi

---

## 🏢 **SESI 1: Data Center dan Cloud Computing (60 menit)**

### A. Konsep Data Center Modern (20 menit)
- **Definisi Data Center**:
  - Fasilitas terpusat untuk menyimpan, mengelola, dan mendistribusikan data
  - Infrastruktur IT yang mendukung operasi bisnis
  - Komponen: Server, Storage, Network, Power, Cooling
  
- **Arsitektur Data Center**:
  - **Three-Tier Architecture**: Core, Aggregation, Access
  - **Spine-Leaf Architecture**: Scalable dan low-latency
  - **Virtualization**: Server, Network, Storage virtualization
  - **Software-Defined Infrastructure**: SDN, SDS, SDDC

### B. Cloud Computing Fundamentals (20 menit)
- **Service Models**:
  - **IaaS** (Infrastructure as a Service): Virtual machines, storage
  - **PaaS** (Platform as a Service): Development platforms
  - **SaaS** (Software as a Service): Applications
  
- **Deployment Models**:
  - **Public Cloud**: AWS, Azure, Google Cloud
  - **Private Cloud**: On-premises cloud
  - **Hybrid Cloud**: Kombinasi public dan private
  - **Multi-Cloud**: Multiple cloud providers

### C. Simulasi Data Center di Packet Tracer (20 menit)
- **Basic Data Center Setup**:
  - Core switches dengan redundancy
  - Server farm dengan load balancing
  - DMZ untuk web services
  - Management network
  - Basic virtualization simulation

## 🔧 **SESI 2: Network Components - Komponen Jaringan (20 menit)**

### A. Hardware Components (10 menit)

#### 1. Router
- **Fungsi**: Menghubungkan jaringan yang berbeda, routing traffic
- **Karakteristik**:
  - Bekerja di Layer 3 (Network Layer)
  - Memiliki routing table
  - Dapat melakukan NAT, DHCP, Firewall
- **Contoh**: Cisco 1941, 2911, ISR 4000 series
- **Port**: Ethernet, Serial, Console

#### 2. Switch
- **Fungsi**: Menghubungkan perangkat dalam satu jaringan
- **Karakteristik**:
  - Bekerja di Layer 2 (Data Link Layer)
  - Menggunakan MAC address table
  - Mendukung VLAN
- **Jenis**:
  - **Unmanaged**: Plug-and-play, tidak bisa dikonfigurasi
  - **Managed**: Dapat dikonfigurasi, monitoring, VLAN
- **Contoh**: Cisco 2960, 3560, Catalyst 9000 series

#### 3. Hub (Legacy)
- **Fungsi**: Menghubungkan perangkat (sudah jarang digunakan)
- **Karakteristik**:
  - Bekerja di Layer 1 (Physical Layer)
  - Collision domain besar
  - Half-duplex communication
- **Mengapa tidak digunakan**: Security issues, collision

#### 4. Access Point (AP)
- **Fungsi**: Menyediakan akses wireless
- **Karakteristik**:
  - Bridge antara wired dan wireless
  - Mendukung multiple SSID
  - Security: WPA2, WPA3
- **Contoh**: Cisco Aironet, Meraki

### B. Network Media & Cables (5 menit)

#### 1. Twisted Pair Cable
- **UTP (Unshielded)**: Cat5e, Cat6, Cat6a
- **STP (Shielded)**: Untuk environment dengan interference
- **Jarak maksimal**: 100 meter

#### 2. Fiber Optic
- **Single-mode**: Jarak jauh (hingga 40km)
- **Multi-mode**: Jarak menengah (hingga 2km)
- **Keuntungan**: Kecepatan tinggi, tidak terpengaruh interference

#### 3. Wireless
- **Standards**: 802.11a/b/g/n/ac/ax (WiFi 6)
- **Frequency**: 2.4GHz, 5GHz, 6GHz
- **Range**: Tergantung power dan obstacles

### C. Network Services & Protocols (5 menit)

#### 1. DHCP (Dynamic Host Configuration Protocol)
- **Fungsi**: Memberikan IP address otomatis
- **Components**: DHCP Server, Client, Scope, Lease
- **Keuntungan**: Manajemen IP otomatis, mengurangi konflik

#### 2. DNS (Domain Name System)
- **Fungsi**: Mengubah domain name ke IP address
- **Hierarchy**: Root, TLD, Authoritative servers
- **Record types**: A, AAAA, CNAME, MX

#### 3. NAT (Network Address Translation)
- **Fungsi**: Mengubah private IP ke public IP
- **Types**: Static NAT, Dynamic NAT, PAT (Port Address Translation)
- **Keuntungan**: Menghemat public IP, security

### 🎯 **Aktivitas Praktis: "Component Detective"**
**Durasi**: 5 menit

**Instruksi**:
1. Bagi kelas menjadi 4 kelompok
2. Setiap kelompok mendapat skenario jaringan
3. Tentukan komponen yang dibutuhkan dan alasannya

**Skenario**:
- **Kelompok 1**: Kantor kecil (10 PC, 1 printer, internet)
- **Kelompok 2**: Sekolah (100 PC, WiFi, server)
- **Kelompok 3**: Warnet (20 PC, billing system, gaming)
- **Kelompok 4**: Rumah (5 device, smart TV, IoT)

**Output**: Diagram sederhana dengan komponen dan justifikasi

---

## 🚀 Opening Activity (10 menit)

### Prototype Kickoff
**Aktivitas:** "From Concept to Reality"
- Review solution concept dari Day 5
- Mapping konsep ke implementasi teknis (termasuk cloud/DC integration)
- Setting expectations untuk 3 hari prototype

**Discussion Points:**
- Apa yang akan kita build?
- Bagaimana kita akan measure success?
- Apa challenges yang mungkin kita hadapi?
- Bagaimana mengintegrasikan konsep Data Center dan Cloud?
- Komponen apa saja yang dibutuhkan berdasarkan materi sebelumnya?

---

## 🛠️ Main Activities

### Activity 1: Cisco Packet Tracer Setup & Orientation (10 menit)

#### Packet Tracer Interface Overview
- **Logical Workspace:** Area untuk design topology
- **Physical Workspace:** View physical layout
- **Device Selection:** Router, Switch, End Devices, Connections
- **Simulation Mode:** untuk troubleshooting dan testing

#### Basic Operations
```
1. Adding Devices:
   - Drag & drop dari device panel
   - Pilih model yang sesuai (2960 Switch, 1941 Router)

2. Making Connections:
   - Straight-through cable untuk different devices
   - Crossover cable untuk same type devices
   - Console cable untuk configuration

3. Basic Configuration:
   - CLI access melalui terminal
   - Basic commands (enable, configure terminal)
```

### Activity 2: Basic Network Design Implementation (20 menit)

#### Scenario: Small Office Network
**Requirements dari User Research:**
- 20 workstations
- 1 server
- Internet connectivity
- Basic security
- Network segmentation

#### Step-by-Step Implementation

**Step 1: Physical Topology**
```
Topology Layout:
[Internet Cloud] -- [Router] -- [Core Switch] -- [Access Switches]
                                      |              |
                                 [Server]      [Workstations]
```

**Step 2: Device Placement**
- 1x Router 1941 (Gateway)
- 1x Switch 2960-24TT (Core)
- 2x Switch 2960-24TT (Access)
- 1x Server-PT
- 6x PC-PT (representing 20 workstations)

**Step 3: Physical Connections**
- Router Gi0/0 to Internet Cloud
- Router Gi0/1 to Core Switch Gi0/1
- Core Switch Gi0/2 to Access Switch 1 Gi0/1
- Core Switch Gi0/3 to Access Switch 2 Gi0/1
- Server to Core Switch Fa0/1
- PCs to Access Switches

### Activity 3: IP Addressing & Subnetting (15 menit)

#### Network Planning
**Base Network:** 192.168.1.0/24

**Subnet Allocation:**
```
Management VLAN:    192.168.1.0/28    (VLAN 1)
Server VLAN:        192.168.1.16/28   (VLAN 10)
Workstation VLAN:   192.168.1.32/27   (VLAN 20)
Guest VLAN:         192.168.1.64/27   (VLAN 30)
```

#### Router Configuration
```cisco
Router(config)# interface gi0/1
Router(config-if)# no shutdown
Router(config-if)# exit

Router(config)# interface gi0/1.10
Router(config-subif)# encapsulation dot1Q 10
Router(config-subif)# ip address 192.168.1.17 255.255.255.240
Router(config-subif)# exit

Router(config)# interface gi0/1.20
Router(config-subif)# encapsulation dot1Q 20
Router(config-subif)# ip address 192.168.1.33 255.255.255.224
Router(config-subif)# exit
```

#### Switch Configuration
```cisco
Switch(config)# vlan 10
Switch(config-vlan)# name Servers
Switch(config-vlan)# exit

Switch(config)# vlan 20
Switch(config-vlan)# name Workstations
Switch(config-vlan)# exit

Switch(config)# interface range fa0/1-10
Switch(config-if-range)# switchport mode access
Switch(config-if-range)# switchport access vlan 20
Switch(config-if-range)# exit

Switch(config)# interface gi0/1
Switch(config-if)# switchport mode trunk
Switch(config-if)# exit
```

### Activity 4: Basic Connectivity Testing (5 menit)

#### Testing Checklist
- [ ] PC to PC dalam same VLAN
- [ ] PC to Server
- [ ] PC to Router (Gateway)
- [ ] Inter-VLAN routing
- [ ] Internet connectivity (simulation)

#### Troubleshooting Commands
```cisco
# Pada PC
ping 192.168.1.33
ipconfig

# Pada Router
show ip interface brief
show ip route

# Pada Switch
show vlan brief
show interface status
```

---

## 📊 Documentation Template

### Network Documentation
```markdown
## Basic Network Topology Documentation

### Network Overview
- **Topology Type:** Hierarchical
- **Total Devices:** [Number]
- **VLANs Implemented:** [List]

### IP Addressing Scheme
| VLAN | Network | Gateway | Purpose |
|------|---------|---------|----------|
| 10   | 192.168.1.16/28 | .17 | Servers |
| 20   | 192.168.1.32/27 | .33 | Workstations |

### Device Configuration Summary
| Device | Interface | IP Address | VLAN |
|--------|-----------|------------|------|
| Router | Gi0/1.10 | 192.168.1.17 | 10 |
| Router | Gi0/1.20 | 192.168.1.33 | 20 |

### Testing Results
- [x] Intra-VLAN connectivity
- [x] Inter-VLAN routing
- [ ] Internet access
- [ ] Security policies
```

---

## 🎯 Deliverables

### Individual Deliverables
1. **Packet Tracer File:** `Day6_BasicTopology_[Nama].pkt`
2. **Network Documentation:** Menggunakan template di atas
3. **Configuration Backup:** Export semua device configs

### Team Deliverables
1. **Topology Presentation:** 5 menit per team
2. **Lessons Learned:** Challenges dan solutions

---

## 🏠 Homework: Security Research

### Assignment: "Security Threats Analysis"
**Deadline:** Sebelum Day 7

**Tasks:**
1. **Research 3 common network security threats:**
   - Threat description
   - How it affects small office networks
   - Potential impact
   - Basic mitigation strategies

2. **Identify security gaps dalam topology hari ini:**
   - Apa yang missing?
   - Apa yang bisa di-improve?
   - Prioritas implementation

3. **Prepare security enhancement proposal:**
   - Firewall placement
   - Access Control Lists (ACL)
   - Network monitoring

**Format:** 1-2 halaman report + annotated topology diagram

---

## 📚 Resources

### Cisco Packet Tracer Resources
- [Packet Tracer Tutorials](https://www.netacad.com/courses/packet-tracer)
- [Basic Router Configuration Guide](https://www.cisco.com/c/en/us/support/docs/routers/)
- [Switch Configuration Best Practices](https://www.cisco.com/c/en/us/support/docs/switches/)

### Network Design References
- RFC 1918: Private Internet Address Allocation
- Cisco Hierarchical Network Design
- VLAN Best Practices Guide

### Tools untuk Next Session
- Cisco Packet Tracer (updated version)
- Network documentation template
- Security checklist

---

## 🔄 Reflection & Preview

### Today's Reflection
1. **Apa yang paling challenging dalam implementasi hari ini?**
2. **Bagaimana design thinking membantu dalam problem-solving?**
3. **Apa yang akan kalian improve untuk tomorrow?**

### Preview Day 7
**Topic:** "Security Implementation - Firewall & Access Control"
- Implementing firewall rules
- Access Control Lists (ACL)
- Network security monitoring
- Intrusion detection basics

**Preparation:**
- Review security research homework
- Bring topology dari hari ini
- Install Wireshark (optional)

---

*"The best way to learn networking is by doing. Today we built the foundation, tomorrow we secure it!"*

**Mentor Notes:**
- Encourage experimentation
- Help with troubleshooting, don't give direct answers
- Focus on understanding, not just configuration
- Document common issues for future reference