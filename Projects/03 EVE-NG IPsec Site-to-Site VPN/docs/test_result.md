# Test Results – Site-to-Site VPN (EVE-NG Lab)

## Summary
- Topology file: 
    - `docs/`
        - Network Diagram  Site-to-Site VPN Deployment with Fortinet.png

- Configs used:  
    - `backups/`
        - `Firewall/` 
            - FGT-Datacenter_7-0_0066_202509241120.conf
            - FGT-HQ_7-0_0066_202509241120.conf

    - `configs/` 
        - `Router/` 
            - vISP.cfg
        - `Switchs/`
            - Access_DCSW.cfg
            - Access_HQSW.cfg
            - Distribution_DCSW01.cfg 
            - Distribution_DCSW02.cfg
            - Distribution_HQSW01.cfg
            - Distribution_HQSW02.cfg   

---

## Objective
Test connects From HQ to vISP , DC to vISP and across VPN tunnel between HQ LAN and DC LAN
Including inspection routing and OSPF on topology EVE-NG

## Results Table

| ID   | Scenario                        | Source              | Destination        | Expected Result        |
|------|---------------------------------|---------------------|--------------------|------------------------|
| TC01 | Ping HQ VLAN10 to vISP          | 192.168.10.1       | vISP IP (e.g. 8.8.8.8 simulated) | ✅ Reachable |
| TC02 | Ping HQ VLAN199 to vISP         | 192.168.199.1       | vISP IP (e.g. 8.8.8.8 simulated) | ✅ Reachable |
| TC03 | Ping DC LAN to vISP             | 192.168.200.1       | vISP IP (e.g. 8.8.8.8 simulated) | ✅ Reachable |
| TC04 | Verify VPN Tunnel Up  HQ and DC          | N/A                 | N/A                | ✅ Phase1/Phase2 = UP  |
| TC05 | Routing Table Check  HQ         | HQ FortiGate        | Show route         | ✅ See 192.168.200.0/24|
| TC06 | Routing Table Check  DC         | HQ FortiGate        | Show route         | ✅ See 192.168.10.0/24 and 192.168.199.0/24 |
| TC07 | Ping across VPN between HQ LAN and DC LAN          | 192.168.10.1 <br> 192.168.199.1<br>192.168.200.1<br>192.168.200.1     | 192.168.200.1<br>192.168.200.1<br>192.168.10.1<br>192.168.199.1     | ✅ Success (VPN path) |
| TC08 | Traceroute across VPN between HQ LAN and DC LAN     |  192.168.10.1 <br> 192.168.199.1<br>192.168.200.1<br>192.168.200.1       | 192.168.200.1<br>192.168.200.1<br>192.168.10.1<br>192.168.199.1     | ✅ Success via VPN tunnel   |
---

# Test Results – Site-to-Site VPN (EVE-NG)

## TC01 – Ping HQ VLAN10 → vISP
**Expected**: VPC (192.168.10.1) should reach vISP simulated IP   
**Observed**: ✅ Pass  
![Ping vISP Screenshot](https://res.cloudinary.com/dlmqbpout/image/upload/v1758824433/%E0%B8%AA%E0%B8%81%E0%B8%A3%E0%B8%B5%E0%B8%99%E0%B8%8A%E0%B9%87%E0%B8%AD%E0%B8%95_2025-09-26_011124_zyqahm.png)

---

## TC02 – Ping HQ VLAN199 → vISP
**Expected**: VPC (192.168.199.1) should reach vISP simulated IP  
**Observed**: ✅ Pass  
![Ping vISP Screeshot](https://res.cloudinary.com/dlmqbpout/image/upload/v1758824654/%E0%B8%AA%E0%B8%81%E0%B8%A3%E0%B8%B5%E0%B8%99%E0%B8%8A%E0%B9%87%E0%B8%AD%E0%B8%95_2025-09-26_012355_wqqaca.png)

---

## TC03 – Ping DC → vISP
**Expected**: VPC (192.168.200.1) should reach vISP simulated IP  
**Observed**: ✅ Pass  
![Ping vISP Screenshot](https://res.cloudinary.com/dlmqbpout/image/upload/v1758824863/%E0%B8%AA%E0%B8%81%E0%B8%A3%E0%B8%B5%E0%B8%99%E0%B8%8A%E0%B9%87%E0%B8%AD%E0%B8%95_2025-09-26_012718_y5u9ji.png)

---
## TC04 – Verify VPN Tunnel Up HQ and DC
**Expected**: Phase1/Phase2 UP  
**Observed**: ✅ Pass  

![Tunnel Up form HQ Screenshot](https://res.cloudinary.com/dlmqbpout/image/upload/v1758825112/%E0%B8%AA%E0%B8%81%E0%B8%A3%E0%B8%B5%E0%B8%99%E0%B8%8A%E0%B9%87%E0%B8%AD%E0%B8%95_2025-09-26_013128_zzoeuc.png)
![Tunnel Up form DC Screenshot](https://res.cloudinary.com/dlmqbpout/image/upload/v1758825181/%E0%B8%AA%E0%B8%81%E0%B8%A3%E0%B8%B5%E0%B8%99%E0%B8%8A%E0%B9%87%E0%B8%AD%E0%B8%95_2025-09-26_013254_qhip9r.png)

---

## TC05 – Routing Table Check HQ
**Expected**: HQ FortiGate should have static/learned route to 192.168.200.0/24 via To-Datacenter  
**Observed**: ✅ Pass  
![Routing Table Screenshot](https://res.cloudinary.com/dlmqbpout/image/upload/v1758825286/%E0%B8%AA%E0%B8%81%E0%B8%A3%E0%B8%B5%E0%B8%99%E0%B8%8A%E0%B9%87%E0%B8%AD%E0%B8%95_2025-09-26_013435_vwbrx8.png)

---

## TC06 – Routing Table Check DC
**Expected**: HQ FortiGate should have static/learned route to 192.168.10.0/24 via VPN To-HQ  and static/learned route to 192.168.199.0/24 via VPN To-HQ 

**Observed**: ✅ Pass  
![Routing Table Screenshot](https://res.cloudinary.com/dlmqbpout/image/upload/v1758825367/%E0%B8%AA%E0%B8%81%E0%B8%A3%E0%B8%B5%E0%B8%99%E0%B8%8A%E0%B9%87%E0%B8%AD%E0%B8%95_2025-09-26_013600_tsad9p.png)

---

## TC07 – Ping across VPN between HQ LAN and DC LAN
**Action1**: From client `192.168.10.1` → server `192.168.200.1` (ping 5 packets)  
**Expected**: ICMP reply success (0% loss)  
**Observed**: ✅ Pass  
![Ping HQ VLAN10 to DC LAN Screenshot](https://res.cloudinary.com/dlmqbpout/image/upload/v1758825520/%E0%B8%AA%E0%B8%81%E0%B8%A3%E0%B8%B5%E0%B8%99%E0%B8%8A%E0%B9%87%E0%B8%AD%E0%B8%95_2025-09-26_013827_pnvdop.png)

**Action2**: From client `192.168.199.1` → server `192.168.200.1` (ping 5 packets) 
**Expected**: ICMP reply success (0% loss)  
**Observed**: ✅ Pass  
![Ping HQ VLAN199 to DC LAN Screenshot](https://res.cloudinary.com/dlmqbpout/image/upload/v1758825607/%E0%B8%AA%E0%B8%81%E0%B8%A3%E0%B8%B5%E0%B8%99%E0%B8%8A%E0%B9%87%E0%B8%AD%E0%B8%95_2025-09-26_014000_sdslos.png)

**Action3**: From server `192.168.200.1` → client `192.168.10.1` (ping 5 packets)  
**Expected**: ICMP reply success (0% loss)  
**Observed**: ✅ Pass  
![Traceroute Server to HQ VLAN10 LAN Screenshot](https://res.cloudinary.com/dlmqbpout/image/upload/v1758825673/%E0%B8%AA%E0%B8%81%E0%B8%A3%E0%B8%B5%E0%B8%99%E0%B8%8A%E0%B9%87%E0%B8%AD%E0%B8%95_2025-09-26_014105_a14ynn.png)

**Action4**: From server `192.168.200.1` → client `192.168.199.1` (ping 5 packets)  
**Expected**: ICMP reply success (0% loss)  
**Observed**: ✅ Pass  
![Traceroute  Server to HQ VLAN199 LAN Screenshot](https://res.cloudinary.com/dlmqbpout/image/upload/v1758825758/%E0%B8%AA%E0%B8%81%E0%B8%A3%E0%B8%B5%E0%B8%99%E0%B8%8A%E0%B9%87%E0%B8%AD%E0%B8%95_2025-09-26_014225_e7ed6f.png)

---


## TC08 – Traceroute across VPN between HQ LAN and DC LAN

**Action1**: From client `192.168.10.1` → server `192.168.200.1` 
**Expected**: Success via VPN tunnel  
**Observed**: ✅ Pass  
![Traceroute HQ VLAN10 to DC LAN Screenshot](https://res.cloudinary.com/dlmqbpout/image/upload/v1758825856/%E0%B8%AA%E0%B8%81%E0%B8%A3%E0%B8%B5%E0%B8%99%E0%B8%8A%E0%B9%87%E0%B8%AD%E0%B8%95_2025-09-26_014404_t11v0i.png)


**Action2**: From client `192.168.199.1` → server `192.168.200.1`
**Expected**: Success via VPN tunnel  
**Observed**: ✅ Pass  
![Traceroute HQ VLAN199 to DC LAN Screenshot](https://res.cloudinary.com/dlmqbpout/image/upload/v1758825962/%E0%B8%AA%E0%B8%81%E0%B8%A3%E0%B8%B5%E0%B8%99%E0%B8%8A%E0%B9%87%E0%B8%AD%E0%B8%95_2025-09-26_014555_adyvm4.png)


**Action3**: From server `192.168.200.1` → client `192.168.10.1`  
**Expected**: Success via VPN tunnel  
**Observed**: ✅ Pass  
![Traceroute Server to HQ VLAN10 Screenshot](https://res.cloudinary.com/dlmqbpout/image/upload/v1758826049/%E0%B8%AA%E0%B8%81%E0%B8%A3%E0%B8%B5%E0%B8%99%E0%B8%8A%E0%B9%87%E0%B8%AD%E0%B8%95_2025-09-26_014723_bvsh2a.png)


**Action4**: From server `192.168.200.1` → client `192.168.199.1` 
**Expected**: Success via VPN tunnel  
**Observed**: ✅ Pass  
![Traceroute Server to HQ VLAN199 Screenshot](https://res.cloudinary.com/dlmqbpout/image/upload/v1758826102/%E0%B8%AA%E0%B8%81%E0%B8%A3%E0%B8%B5%E0%B8%99%E0%B8%8A%E0%B9%87%E0%B8%AD%E0%B8%95_2025-09-26_014815_kmndbw.png)


---

