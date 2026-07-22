# WiFi Connectivity Problems

##  Objective
Fix client wireless authentication failures, IP allocation drops, and persistent disconnection loops on enterprise or home networks.

## ⚠ Common Error Messages
- "Can't connect to this network"
- "No Internet, secured"
- "Action Needed" or stuck on "Identifying..."
- "Wi-Fi doesn't have a valid IP configuration"

---

##  Troubleshooting Steps

### **Issue: "No Internet, Secured" / APIPA IP Assignment (169.254.x.x)**

**Step 1: Inspect Assigned IP Address Configuration**
- Open Command Prompt
- Run `ipconfig /all`
- Locate the Wireless Network Adapter entry
- If the IPv4 Address starts with `169.254.x.x`, the machine cannot talk to a DHCP server to lease a network profile

**Step 2: Force New IP Lease**
- From the same Command Prompt, release the current assignment by running:
  `ipconfig /release`
- Force a fresh lease request over the airwaves by running:
  `ipconfig /renew`
- Confirm that the new address drops into your standard local subnet mask profile (e.g., `192.168.x.x` or `10.x.x.x`)

---

### **Issue: Corrupted Corporate Wireless Profile**

**Symptoms:**
- The machine fails to connect to the office network after an internal password update or security profile alteration.

**Resolution:**
1. Click the Wi-Fi icon in the bottom right corner of the Windows taskbar
2. Click "Network & Internet settings" → Select "Wi-Fi" → Click "Manage known networks"
3. Find the SSID name of your corporate or home network
4. Click the "Forget" button next to it
5. Toggle the Wi-Fi card adapter switch to Off, wait 5 seconds, and toggle it back to On
6. Select the network name again from the discovery array, enter your fresh credentials, and verify connection status

---

##  Escalation Criteria

**Escalate to Level 2/3 if:**
- Physical Wi-Fi radio switches fail to switch on via software or physical keyboard triggers
- Mass disconnect events occur concurrently across an entire physical office floor or corporate building wing
- Enterprise 802.1X certificate provisioning fails to apply to machines over Group Policy

---

##  Security Notes

- Do not configure administrative endpoints to connect to unencrypted public Wi-Fi access points without an active VPN tunnel running
- Ensure WPA3 or WPA2 Enterprise settings are enforced across all standard corporate issued laptops

---

##  Expected Resolution Time
- Network profile deletion and re-auth: 3 minutes
- DHCP release and renewal cycles: 5 minutes
- Advanced network stack reset and system reboot: 10 minutes

---

##  When to Escalate
- If multiple corporate laptops lose access to a single specific physical access point location
- If network adapters throw Code 10 hardware errors that persist after driver rollbacks

---

##  What to Document in Ticket
- Current wireless signal strength metrics and frequency band (2.4GHz vs 5GHz)
- Wireless network interface card model and driver version
- Assigned IP, gateway, and DNS addresses retrieved from the `ipconfig` log dump

--- 
