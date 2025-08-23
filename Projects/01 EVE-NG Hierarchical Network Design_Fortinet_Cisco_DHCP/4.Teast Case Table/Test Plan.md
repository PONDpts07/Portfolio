# Test Plan

| Test ID | Test Scenario                | Pre-Condition                  | Test Steps                                                                 | Expected Result                                  |
|---------|------------------------------|--------------------------------|----------------------------------------------------------------------------|-------------------------------------------------|
| TC-01   | VPN Tunnel Establishment     | VPN config complete on HQ & Branch | 1. Initiate VPN connection <br> 2. Check tunnel status                    | Tunnel should be **UP** (IKE Phase1/2 success)  |
| TC-02   | VPN Authentication (Valid)   | AD/LDAP integration configured  | 1. Connect VPN using valid AD account <br> 2. Verify assigned IP           | VPN should connect successfully, correct IP assigned |
| TC-03   | VPN Authentication (Invalid) | AD/LDAP integration configured  | 1. Connect VPN using invalid AD account                                    | Connection should be **denied**                 |
| TC-04   | Firewall Policy Enforcement  | Security policies configured    | 1. Access blocked site (e.g. Facebook) <br> 2. Access allowed site (Intranet) | Blocked site = Denied <br> Allowed site = Granted |
| TC-05   | WAN Failover                 | Dual WAN configured (SD-WAN/HA) | 1. Disconnect primary WAN <br> 2. Check connectivity                       | Traffic reroutes via backup WAN, downtime <2 sec |
| TC-06   | RADIUS Accounting Logs       | FreeRADIUS configured           | 1. Login VPN <br> 2. Logout VPN                                            | RADIUS logs show session Start/Stop, Username, Duration |
