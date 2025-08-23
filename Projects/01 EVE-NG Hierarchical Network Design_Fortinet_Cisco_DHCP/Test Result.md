# Test Result

| Test ID | Expected Result                                  | Actual Result                                  | Status | Evidence                |
|---------|-------------------------------------------------|------------------------------------------------|--------|-------------------------|
| TC-01   | Tunnel UP                                       | Tunnel UP (IKE SA established)                 | ✅ Pass | ![VPN_Status.png]       |
| TC-02   | VPN connected, correct IP assigned              | User `ad_user01` connected, IP 10.10.10.5      | ✅ Pass | ![VPN_User_Login.png]   |
| TC-03   | Connection denied                               | Access denied message                          | ✅ Pass | ![VPN_Invalid_User.png] |
| TC-04   | Blocked = Denied, Allowed = Granted             | Facebook.com Denied, Intranet OK               | ✅ Pass | ![Firewall_Policy.png]  |
| TC-05   | Failover working, downtime <2 sec               | Traffic rerouted to WAN2, downtime ~1.5s       | ✅ Pass | ![WAN_Failover.png]     |
| TC-06   | Logs recorded (Start/Stop, User, Duration)      | RADIUS log shows Start/Stop for `user01`       | ✅ Pass | ![Radius_Log.png]       |
