 # DNS Resolution Issues

##  Objective
Diagnose hostname address lookups, correct namespace translation drops, and bypass bad domain caches blocking corporate cloud platform visibility.

##  Common Error Messages
- "DNS Server Not Responding."
- "Server IP address could not be found (ERR_NAME_NOT_RESOLVED)."
- "The site cannot be reached."
-"Ping request could not find host. Please check the name and try again."

### Troubleshooting Steps

# Issue: Localized DNS Cache Pollution

Step 1: Flush and Verify Name Translation Resolution
-Open Command Prompt as Administrator
-Execute the flush engine sequence:
ipconfig /flushdns
-Test the lookup functionality of your target external target website domain by executing:
nslookup ://microsoftonline.com
-Check if the command structure successfully reports the translated public IP endpoints rather than throwing lookup errors 

Step 2: Query Your Assigned Namespace Server Directory
-Run ipconfig /all and check the explicit IP strings defined next to "DNS Servers" 
-Verify the listed IP target strings perfectly match your standard active corporate Domain Controller or secure internal gateway endpoints
-Fire a direct path ping confirmation check against the listed server address string to make sure it is responding across your network interface layout path:
ping <DNS_Server_IP>

# Issue: Bad Static Alternative DNS Entries

# Symptoms:

-The client computer maps traffic paths perfectly to external internet websites but fails to resolve internal intranet names or map group path directories.

# Resolution:

-Press Windows Key + R → Type ncpa.cpl and hit Enter to display the active Network Connections control board 
-Right-click your active Ethernet or Wireless interface network adapter profile card layout and choose Properties 
-Select "Internet Protocol Version 4 (TCP/IPv4)" and click the Properties button 
-Ensure the toggle selection configuration is explicitly set to "Obtain DNS server address automatically" unless specifically required by fixed technical infrastructure definitions
-If alternative diagnostic routing setups are required for troubleshooting, input public nameserver strings (e.g., Cloudflare: 1.1.1.1 or Google: 8.8.8.8) into the fields to test if the localized block vanishes

#  Escalation Criteria

Escalate to Level 2/3 if:

-Internal Active Directory DNS zone configurations become corrupted or drop record tables
-External corporate domain registrars lose structural synchronization or suffer upstream distributed denial-of-service blockades
-Global internal routing profile adjustments break namespace resolution paths across site-to-site WAN segments

#  Security Notes

-Do not alter configuration details to route production traffic routes over untrusted or unverified open-source public DNS resolver providers
-Enforce DNS over HTTPS (DoH) profiles across endpoint systems wherever required by organizational cybersecurity frameworks 

# ⏱ Expected Resolution Time

-Cache purge and basic nslookup verification checks: 3 minutes
-Network Adapter property card corrections: 5 minutes
-Routing path tracking and diagnostic isolation checks: 10 minutes

#  When to Escalate
-If an entire subnet branch profile loses standard visibility to key application server names at the same time
-If domain verification checks indicate record tables are dropping across the enterprise platform layer

#  What to Document in Ticket
-Current internal and public IP target path configurations of your local host system
-Complete output dump from your nslookup target diagnostic testing runs
-Names and address strings of the DNS server profiles currently tied to the endpoint configuration
