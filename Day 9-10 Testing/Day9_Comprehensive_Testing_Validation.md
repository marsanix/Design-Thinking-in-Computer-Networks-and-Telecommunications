# Day 9: Desain Topologi Jaringan & Comprehensive Testing
## Fase: Testing - Prototype Validation

### 🎯 Learning Objectives
Setelah mengikuti sesi ini, peserta akan mampu:
1. Memahami prinsip-prinsip desain topologi jaringan
2. Menganalisis berbagai jenis topologi jaringan dan karakteristiknya
3. Melakukan comprehensive testing pada network prototype
4. Mengvalidasi security controls dan policies
5. Melakukan performance benchmarking
6. Mengidentifikasi dan mengatasi issues dalam implementation
7. Mendokumentasikan test results dan findings
8. Mempersiapkan user acceptance testing
9. Mengoptimalkan desain topologi berdasarkan hasil testing

---

## 📋 Session Overview
**Durasi:** 60 menit  
**Format:** Testing Workshop & Validation  
**Tools:** Cisco Packet Tracer, Testing Plan dari homework  
**Deliverable:** Comprehensive Test Report dengan validation results

---

## 🏗️ **SESI 1: Desain Topologi Jaringan (45 menit)**

### A. Prinsip Desain Topologi (15 menit)
- **Scalability**: Kemampuan untuk berkembang
- **Reliability**: Keandalan dan redundancy
- **Performance**: Optimasi bandwidth dan latency
- **Security**: Segmentasi dan isolasi
- **Cost-effectiveness**: Efisiensi biaya
- **Manageability**: Kemudahan pengelolaan

### B. Jenis-jenis Topologi Jaringan (15 menit)
- **Physical Topologies**:
  - Star, Ring, Bus, Mesh
  - Hybrid topologies
  
- **Logical Topologies**:
  - Hierarchical (3-tier)
  - Spine-Leaf
  - Full Mesh
  - Hub-and-Spoke

### C. Design Considerations (15 menit)
- **Traffic Patterns**: North-South vs East-West
- **Bandwidth Requirements**: Core, distribution, access
- **Redundancy**: Single points of failure
- **Growth Planning**: Future expansion
- **Security Zones**: DMZ, internal, management

---

## 🧠 **SESI 2: Testing Strategy & Planning (20 menit)**

### Testing Framework Review
**Comprehensive Testing Approach:**
- Functional testing checklist
- Security validation procedures
- Performance benchmarking methods
- User acceptance criteria
- Documentation requirements
- Topology validation tests

### Test Environment Setup
**Preparation untuk testing:**
- Baseline measurements
- Testing tools configuration
- Monitoring setup
- Documentation templates
- Team role assignments

### Success Criteria Definition
**Clear metrics untuk evaluation:**
- Performance thresholds
- Security compliance requirements
- Functionality requirements
- User experience standards
- Documentation quality standards
- Topology design effectiveness

---

## 🚀 Opening Activity (10 menit)

### Testing Plan Review
**Aktivitas:** "Test Strategy Alignment"
- Presentasi testing plans dari homework
- Consolidation of best testing approaches
- Assignment of testing responsibilities per team

**Key Focus:**
- Apa yang akan kita test hari ini?
- Bagaimana kita measure success?
- Apa contingency plans jika ada failures?

---

## 🛠️ Main Testing Activities

### Activity 1: Functional Testing (15 menit)

#### Network Connectivity Testing
**Objective:** Validate basic network functionality

**Test Suite 1: Basic Connectivity**
```
Test Case 1.1: Intra-VLAN Communication
Procedure:
1. PC1 (VLAN 20) ping PC2 (VLAN 20)
2. PC1 ping Server (VLAN 10) - should work
3. Document response times

Expected Result: Successful ping, <10ms response
Actual Result: [To be filled]
Status: [PASS/FAIL]
Notes: [Any observations]
```

**Test Suite 2: Inter-VLAN Routing**
```
Test Case 2.1: Workstation to Server Access
Procedure:
1. PC (VLAN 20) access web server (VLAN 10)
2. Test HTTP (port 80) access
3. Test HTTPS (port 443) access
4. Test FTP (port 21) access

Expected Result: HTTP/HTTPS/FTP successful, other ports blocked
Actual Result: [To be filled]
Status: [PASS/FAIL]
```

**Test Suite 3: Internet Connectivity**
```
Test Case 3.1: External Access
Procedure:
1. PC ping external IP (8.8.8.8)
2. Test web browsing simulation
3. Verify NAT functionality

Expected Result: Successful external connectivity
Actual Result: [To be filled]
Status: [PASS/FAIL]
```

#### Wireless Network Testing
```
Test Case 4.1: Wireless Authentication
Procedure:
1. Connect laptop ke OFFICE_SECURE SSID
2. Test WPA3 authentication
3. Verify VLAN assignment
4. Test connectivity

Expected Result: Successful authentication dan connectivity
Actual Result: [To be filled]
Status: [PASS/FAIL]

Test Case 4.2: Guest Network Isolation
Procedure:
1. Connect ke OFFICE_GUEST SSID
2. Attempt access ke internal resources
3. Test internet-only access

Expected Result: Internet access only, internal blocked
Actual Result: [To be filled]
Status: [PASS/FAIL]
```

### Activity 2: Security Testing (15 menit)

#### Access Control Validation
**Objective:** Verify security policies are working correctly

**Test Suite 5: ACL Functionality**
```
Test Case 5.1: External Threat Simulation
Procedure:
1. Simulate external telnet attempt
2. Simulate SSH brute force
3. Test blocked ports (135-139, 445)
4. Verify logging of denied attempts

Expected Result: All malicious attempts blocked dan logged
Actual Result: [To be filled]
Status: [PASS/FAIL]

Commands untuk Testing:
# Dari external source
telnet [router_external_ip] 23
ssh [router_external_ip]
nmap -p 135-139,445 [router_external_ip]

# Check logs
show logging | include DENY
show access-lists
```

**Test Suite 6: Port Security Validation**
```
Test Case 6.1: MAC Address Spoofing
Procedure:
1. Record legitimate MAC address
2. Change PC MAC address
3. Attempt network access
4. Verify port security action

Expected Result: Port security violation, appropriate action taken
Actual Result: [To be filled]
Status: [PASS/FAIL]

Commands untuk Validation:
show port-security
show port-security interface fa0/1
show port-security address
```

**Test Suite 7: DHCP Snooping**
```
Test Case 7.1: Rogue DHCP Server Detection
Procedure:
1. Setup unauthorized DHCP server
2. Attempt DHCP offer
3. Verify DHCP snooping blocks rogue server

Expected Result: Rogue DHCP blocked
Actual Result: [To be filled]
Status: [PASS/FAIL]

Validation Commands:
show ip dhcp snooping
show ip dhcp snooping binding
```

### Activity 3: Performance Testing (10 menit)

#### Network Performance Benchmarking
**Objective:** Measure network performance dan validate QoS

**Test Suite 8: Bandwidth Testing**
```
Test Case 8.1: QoS Traffic Prioritization
Procedure:
1. Generate high-priority traffic (voice simulation)
2. Generate normal traffic (data)
3. Generate low-priority traffic (guest)
4. Measure bandwidth allocation

Expected Result: Traffic prioritized according to QoS policy
Actual Result: [To be filled]
Status: [PASS/FAIL]

Monitoring Commands:
show policy-map interface gi0/0
show class-map
```

**Test Suite 9: Latency & Throughput**
```
Test Case 9.1: Network Response Times
Procedure:
1. Measure ping response times
2. Test file transfer speeds
3. Measure web page load times
4. Document performance baselines

Expected Result: Response times <50ms, throughput >80% of link capacity
Actual Result: [To be filled]
Status: [PASS/FAIL]
```

### Activity 4: Stress Testing (5 menit)

#### Network Resilience Testing
**Objective:** Test network behavior under stress conditions

**Test Suite 10: Failover Testing**
```
Test Case 10.1: Link Failure Simulation
Procedure:
1. Disconnect primary uplink
2. Measure convergence time
3. Test continued connectivity
4. Restore link dan test recovery

Expected Result: <30 second convergence, no data loss
Actual Result: [To be filled]
Status: [PASS/FAIL]
```

**Test Suite 11: High Load Testing**
```
Test Case 11.1: Multiple Simultaneous Connections
Procedure:
1. Simulate multiple users
2. Generate concurrent traffic
3. Monitor performance degradation
4. Test QoS effectiveness

Expected Result: Graceful degradation, priority traffic maintained
Actual Result: [To be filled]
Status: [PASS/FAIL]
```

### Activity 5: Documentation & Analysis (5 menit)

#### Test Results Compilation
**Objective:** Document findings dan prepare recommendations

**Testing Summary Template:**
```markdown
# Network Testing Summary Report

## Executive Summary
- **Testing Date:** [Date]
- **Total Test Cases:** 11
- **Passed:** [Number]
- **Failed:** [Number]
- **Overall Success Rate:** [Percentage]

## Test Results by Category

### Functional Testing (70% weight)
| Test Case | Status | Notes |
|-----------|--------|-------|
| 1.1 Intra-VLAN | PASS/FAIL | [Comments] |
| 2.1 Inter-VLAN | PASS/FAIL | [Comments] |
| 3.1 Internet | PASS/FAIL | [Comments] |
| 4.1 Wireless Auth | PASS/FAIL | [Comments] |
| 4.2 Guest Isolation | PASS/FAIL | [Comments] |

### Security Testing (20% weight)
| Test Case | Status | Notes |
|-----------|--------|-------|
| 5.1 ACL Function | PASS/FAIL | [Comments] |
| 6.1 Port Security | PASS/FAIL | [Comments] |
| 7.1 DHCP Snooping | PASS/FAIL | [Comments] |

### Performance Testing (10% weight)
| Test Case | Status | Notes |
|-----------|--------|-------|
| 8.1 QoS Priority | PASS/FAIL | [Comments] |
| 9.1 Latency | PASS/FAIL | [Comments] |
| 10.1 Failover | PASS/FAIL | [Comments] |
| 11.1 Load Test | PASS/FAIL | [Comments] |

## Critical Issues Identified
1. **High Priority Issues:**
   - [Issue description]
   - Impact: [Business impact]
   - Recommendation: [Fix recommendation]

2. **Medium Priority Issues:**
   - [Issue description]
   - Impact: [Technical impact]
   - Recommendation: [Improvement suggestion]

## Performance Metrics
- **Average Ping Response:** [ms]
- **Throughput:** [Mbps]
- **Convergence Time:** [seconds]
- **Security Violations Detected:** [number]

## Recommendations
1. **Immediate Actions Required:**
   - [Critical fixes]

2. **Optimization Opportunities:**
   - [Performance improvements]

3. **Future Enhancements:**
   - [Advanced features]
```

---

## 🔧 Troubleshooting Common Issues

### Issue Resolution Guide

**Problem 1: Inter-VLAN Communication Failure**
```
Symptoms: PCs cannot reach servers
Diagnosis:
1. Check VLAN configuration: show vlan brief
2. Verify trunk ports: show interface trunk
3. Check router sub-interfaces: show ip interface brief
4. Verify routing: show ip route

Common Fixes:
- Ensure trunk allows required VLANs
- Check sub-interface encapsulation
- Verify IP addressing
```

**Problem 2: ACL Not Blocking Traffic**
```
Symptoms: Unauthorized traffic passing through
Diagnosis:
1. Check ACL configuration: show access-lists
2. Verify ACL application: show ip interface
3. Check ACL order dan logic

Common Fixes:
- Correct ACL direction (in/out)
- Fix wildcard masks
- Reorder ACL statements
- Add explicit deny statement
```

**Problem 3: Wireless Authentication Issues**
```
Symptoms: Cannot connect to wireless network
Diagnosis:
1. Check SSID configuration
2. Verify encryption settings
3. Check VLAN assignment

Common Fixes:
- Verify WPA key
- Check VLAN trunk configuration
- Ensure wireless interface is up
```

---

## 📊 Testing Metrics & KPIs

### Success Criteria
```
Functional Requirements:
✓ 100% basic connectivity
✓ 100% security policy enforcement
✓ 95% performance targets met
✓ <30 second failover time

Security Requirements:
✓ 0 unauthorized access attempts successful
✓ 100% malicious traffic blocked
✓ All security violations logged
✓ Guest network isolation 100% effective

Performance Requirements:
✓ Ping response <50ms
✓ Throughput >80% of link capacity
✓ QoS policies working correctly
✓ No packet loss under normal load
```

### Quality Gates
```
Gate 1: Basic Functionality (Must Pass)
- All devices reachable
- Internet connectivity working
- VLAN segmentation functional

Gate 2: Security Controls (Must Pass)
- ACLs blocking unauthorized traffic
- Port security preventing violations
- Wireless security working

Gate 3: Performance Standards (Should Pass)
- Response times within limits
- QoS prioritization working
- No significant bottlenecks

Gate 4: Resilience Testing (Nice to Pass)
- Graceful failure handling
- Quick recovery times
- Minimal service disruption
```

---

## 🎯 Deliverables

### Individual Deliverables
1. **Test Execution Report:** Detailed test results
2. **Issue Log:** Problems found dan resolutions
3. **Performance Baseline:** Network performance metrics
4. **Recommendations:** Improvement suggestions

### Team Deliverables
1. **Consolidated Test Report:** Combined team results
2. **Demo Preparation:** Working prototype demonstration
3. **Lessons Learned:** Testing insights dan best practices

---

## 🏠 Homework: User Acceptance Testing Preparation

### Assignment: "End-User Validation"
**Deadline:** Day 10

**Tasks:**
1. **Create user scenarios:**
   - Typical daily operations
   - Common user tasks
   - Emergency procedures

2. **Develop user documentation:**
   - Quick start guide
   - Troubleshooting tips
   - Contact information

3. **Prepare user training:**
   - Key features demonstration
   - Security awareness
   - Best practices

**Format:** User acceptance test plan + training materials

---

## 📚 Resources

### Testing Methodologies
- Network Testing Best Practices
- Security Validation Frameworks
- Performance Benchmarking Standards

### Cisco Testing Tools
- Packet Tracer Simulation Mode
- Built-in diagnostic commands
- Performance monitoring features

### Industry Standards
- IEEE Network Testing Standards
- NIST Security Testing Guidelines
- ISO Network Performance Metrics

---

## 🔄 Reflection & Preview

### Today's Reflection
1. **Apa yang paling surprising dari test results?**
2. **Mana area yang perlu most improvement?**
3. **Bagaimana testing mengubah understanding tentang network?**
4. **Apa yang akan kalian test differently next time?**

### Key Achievements
- ✅ Comprehensive testing execution
- ✅ Security validation completed
- ✅ Performance baseline established
- ✅ Issues identified dan documented
- ✅ Recommendations developed

### Preview Day 10
**Topic:** "User Acceptance Testing & Final Evaluation"
- End-user testing scenarios
- Final prototype demonstration
- Peer evaluation dan feedback
- Project retrospective
- Career pathway discussion
- Certification preparation

**Preparation:**
- Complete user acceptance testing homework
- Practice final demonstration
- Prepare for peer feedback
- Reflect on learning journey

---

*"Testing is not about finding bugs, it's about building confidence. Today we validated our solution works!"*

**Mentor Notes:**
- Encourage systematic testing approach
- Help with troubleshooting complex issues
- Emphasize documentation importance
- Prepare students untuk real-world testing scenarios
- Celebrate successful validations dan learn from failures