 ### Slow Network Speeds

##  Objective

Analyze network connection limits, isolate local bandwidth hogs, and resolve interface negotiation speed caps on client machines.

##  Common Error Messages
-"Network connection timed out."
-"High latency detected."
-"Connection is unstable."
-Downloads crawling or video conference calls freezing frequently. 

##  Troubleshooting Steps
-Issue: Interface Card Auto-Negotiation Speed Cap

# Step 1: Check Local Link Speed Properties
-Press Windows Key + R → Type ncpa.cpl and press Enter
-Double-click your active connection adapter card layout profile (e.g., Ethernet)
-Look at the Speed value row reading panel
-If a Gigabit interface card is plugged into a Gigabit wall port but displays a hard cap limit of exactly 100.0 Mbps or 10.0 Mbps, the line negotiation profile is broken 

# Step 2: Force Speed Duplex Re-negotiation
-Click the Properties button on that network card configuration status panel
-Click Configure right under the physical network card descriptor string
-Navigate into the Advanced tab configuration column
-Select the property labeled "Speed & Duplex" from the options list
-Change the dropdown value configuration from "Auto Negotiation" to "1.0 Gbps Full Duplex" (or the maximum physical capability rating of the local card hardware layout)
-Click OK; the line link drop state will reset briefly. If it drops entirely, switch it back to "Auto Negotiation" as the physical cable or port is damaged 

## Issue: Local Background Process Bandwidth Hogging

# Symptoms:

-The computer shows extremely high ping latency response spikes or web resources stall, while other machines nearby perform normally.

# Resolution:
-Press Ctrl + Shift + Esc to access the Task Manager dashboard panel layout
-Click the Network column sorting tab to order all active system tasks by real-time bandwidth consumption metrics
-Isolate if cloud sync utilities, browser extensions, or rogue system updater components are eating up high traffic loads
-If a specific system task is running out of bounds, select that line path and click "End task" to restore capacity lines back to system apps 

##  Escalation Criteria

# Escalate to Level 2/3 if:
-Physical core switches face port configuration degradation or packet drops at the server room rack level
-The primary corporate internet service provider line drops below SLA delivery parameters
-Traffic shaping or Quality of Service (QoS) rule adjustments must be deployed across the core network layout to stabilize voice traffic routing channels

##  Security Notes
-Do not use unauthorized open-source network testing tool downloads that require installing untrusted deep system driver components
-Keep malware testing scans active if interface monitors display unexplained high volumetric upload traffic streams outbound from an idle system

## Expected Resolution Time

-Process traffic tracking analysis and termination runs: 4 minutes
-Interface adapter link speed adjustments: 5 minutes
-Local infrastructure patch cord testing and swaps: 5-10 minutes 

##  When to Escalate
-If bandwidth speed test metrics drop uniformly across all local workstations within a corporate building branch layout
-If physical cabling diagnostic instruments indicate structural wiring damage behind drywalls

##  What to Document in Ticket

-Real-time download/upload speed test metrics retrieved via official internal testing endpoints
-Connection media standard in use (Ethernet Cat5e/6 vs Wi-Fi Standard protocol iterations)
-Device Link speed rating values observed inside the Network Connection property dashboards
