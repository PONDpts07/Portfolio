# Test Result -  Hierarchical Network Design_Cisco_DHCP and Fortinet Next-Gen Firewall (EVE-NG Lab)


## Summary
- Topology file: 
    - `docs/`
        - Network Diagram  Site-to-Site VPN Deployment with Fortinet.png

- Configs used:  
    - `backups/`
        - `Firewall/` 
            - `FGT-01_7-0_0066_202509281110.conf`
            - `FGT-02_7-0_0066_202509281110.conf `

    - `configs/` 
        - `Router/` 
            - VISP.cfg
        - `Switchs/`
            - `Access1.cfg`
            - `Access2.cfg`
            - `Core1.cfg`
            - `Core2.cfg`
            - `Distribution1.cfg`
            - `Distribution2.cfg`      


This document contains the test results for the Layer 2 and Layer 3 network design, including:
- FortiGate HA (FGT-01 / FGT-02)
- Core Switch Redundancy (Core1 / Core2)
- Distribution Layer with VRRP
- Access Layer (VLAN segmentation)
- End-to-End connectivity tests (Ping, Routing, Failover)

## Test Environment
- **VISP Loopback:** 8.8.8.8/32
- **FortiGate-01 Loopback:** 1.1.1.1/32  
- **FortiGate-02 Loopback:** 1.1.1.2/32 
- **Core1 Loopback:** 1.1.1.3/32  
- **Core2 Loopback:** 1.1.1.4/32  
- **Distribution1 Loopback:** 1.1.1.5/32  
- **Distribution2 Loopback:** 1.1.1.6/32  

**VRRP Gateways:**
- VLAN 10 → 192.168.10.254  
- VLAN 20 → 192.168.20.254  
- VLAN 30 → 192.168.30.254  
- VLAN 199 → 192.168.199.254  

---

## Test Cases & Results
# Network Project - Test Results

| ID  | Test Case / Scenario    | Expected Result  | Actual Result             | Status |
|-----|-------------------------|--------------------------------------------------|---------------|--------|
| TC1 | Firewall Policies enforcement | Traffic blocked/allowed according to policy   | Traffic filtered as expected | ✅Pass   |
| TC2 | Redundant links failover | Traffic reroutes through backup link automatically | Failover successful without downtime   | ✅Pass   |
| TC3 | OSPF dynamic routing                          | Routes learned dynamically & traffic reachable   | OSPF neighbors formed, routes present         | ✅Pass   |
| TC4 | VRRP high availability                        | Virtual IP remains reachable during device failover | Virtual IP remained active                     | ✅Pass   |
| TC5 | RSTP with Root Guard                          | Loops prevented, root guard blocks invalid root | Root guard blocked rogue root bridge          | ✅Pass   |
| TC6 | Spanning-tree & port security                 | STP settings prevent loops & secure ports       | Portfast, BPDU Guard, and Port-Security working | ✅Pass   |
| TC7 | DHCP servers on distribution switches        | Clients receive correct IP & options            | DHCP assigned correct IPs                      | ✅Pass   |

----

# Test Results –  Hierarchical Network Design_Cisco_DHCP and Fortinet Next-Gen Firewall (EVE-NG Lab)



## TC01 – Firewall Policies Enforcement
**Expected**: Traffic blocked/allowed according to firewall policies such as vlan10 to VISP (simulate isp 8.8.8.8) 

**Observed**: ✅ Pass  
![Firewall Policy Screenshot](https://res.cloudinary.com/dlmqbpout/image/upload/v1759347424/1d045b7a-f316-4737-a30c-3aa8fe9010e7.png)

---

## TC02 – Redundant Link Failover
**Expected**: Traffic reroutes through backup link automatically during primary link failure  
**Expected**: การจราจรจะเปลี่ยนเส้นทางผ่านลิงก์สำรองอัตโนมัติเมื่อเกิดลิงก์หลักล้มเหลว  
**Observed**: ✅ Pass  
**คำอธิบาย**: ทดสอบความสามารถของลิงก์สำรองในการรักษาการเชื่อมต่อให้ระบบยังทำงานต่อได้  
![Redundant Link Screenshot](https://res.cloudinary.com/dlmqbpout/image/upload/v1759347636/f4b916b9-01c8-4438-ad48-717bd48804c3.png)

---

## TC03 – OSPF Dynamic Routing
**Expected**: Routes learned dynamically & traffic reachable across network  such as at routing table on FGT-01 and FGT-02

**Observed**: ✅ Pass  
![OSPF Routing Screenshot FGT-01](https://res.cloudinary.com/dlmqbpout/image/upload/v1759348227/ba7d3e73-9fce-4e55-97c6-796ccc3d214f.png)

![OSPF Routing Screenshot FGT-02](https://res.cloudinary.com/dlmqbpout/image/upload/v1759348011/d81779a5-cd2e-4f1d-8604-dfcc9919c617.png)

---

## TC04 – VRRP High Availability
**Expected**: Virtual IP remains reachable during device failover  
**Observed**: ✅ Pass  

![VRRP Status Dis 1 Screenshot](https://res.cloudinary.com/dlmqbpout/image/upload/v1759351236/4879377e-7cd0-4974-8469-79b831ded907.png)

![VRRP Status Dis 2 Screenshot](https://res.cloudinary.com/dlmqbpout/image/upload/v1759349031/dbdc5fda-b887-4b68-94cd-e8c1b7db7dad.png)

![VRRP test before failover Screenshot](https://res.cloudinary.com/dlmqbpout/image/upload/v1759349504/7663b157-03d8-4326-8cfb-ed463f72d3db.png)

![VRRP test after failover Screenshot](https://res.cloudinary.com/dlmqbpout/image/upload/v1759349271/f1725574-d30d-4113-b01b-c62f7f696773.png)
---

## TC05 – RSTP with Root Guard
**Expected**: Loops prevented, root guard blocks invalid root  
**Observed**: ✅ Pass  
![RSTP Core1 Screenshot](https://res.cloudinary.com/dlmqbpout/image/upload/v1759350241/319702e7-8699-40f0-8795-cdd0cc6935a9.png)

![RSTP Core2 Screenshot](https://res.cloudinary.com/dlmqbpout/image/upload/v1759350195/700a3c81-4338-4fb9-a181-cf1498926431.png)

![RSTP Distri 1 Screenshot](https://res.cloudinary.com/dlmqbpout/image/upload/v1759349852/d658bf37-141f-4ccf-b2f9-6421dbd7115f.png)

![RSTP Distri 2 Screenshot](https://res.cloudinary.com/dlmqbpout/image/upload/v1759349797/32858ff8-602c-4844-b961-b0f8fc9ae8fd.png)
---

## TC06 – Spanning-Tree & Port Security
**Expected**: STP settings prevent loops & secure ports  
**Observed**: ✅ Pass  
![Port Security Access1 Screenshot](https://res.cloudinary.com/dlmqbpout/image/upload/v1759350530/8c616399-be15-4517-8044-6fbee1576820.png)

![Port Security Access2 Screenshot](https://res.cloudinary.com/dlmqbpout/image/upload/v1759350591/76ad6390-c995-4bd7-9d4a-02ffefccffcb.png)
---

## TC07 – DHCP Servers on Distribution Switches
**Expected**: Clients receive correct IP & options from DHCP  
**Observed**: ✅ Pass  
![DHCP Server Distri1 Screenshot](https://res.cloudinary.com/dlmqbpout/image/upload/v1759350745/bc4b535c-34a9-4249-a325-fcb73dc026c6.png)

![DHCP Server Distri2 Screenshot](https://res.cloudinary.com/dlmqbpout/image/upload/v1759350853/34c50049-c19b-48a1-929e-0f4728afbfd9.png)

![DHCP Client VLAN10,20,30,199 Screenshot](https://res.cloudinary.com/dlmqbpout/image/upload/v1759351061/49c718c2-0b32-4da3-ba46-d64b086e21ff.png)

