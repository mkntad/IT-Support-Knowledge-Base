 # Device Manager & Driver Issues

##  Objective
Identify, update, and repair faulty hardware drivers and resolve device recognition issues.

##  Common Error Messages
- "Device descriptor request failed"
- "This device cannot start (Code 10)"
- "The drivers for this device are not installed (Code 28)"
- "Windows has stopped this device because it has reported problems (Code 43)"

---

##  Troubleshooting Steps

### **Issue: Device Showing Yellow Triangle / Code 10 / Code 28**

**Step 1: Identify the Missing Driver**
- Open Device Manager (`devmgmt.msc`)
- Look for items with a yellow exclamation mark or listed under "Other devices"
- Right-click the problem device and select Properties
- Go to the Details tab, change the dropdown to "Hardware Ids"
- Copy the shortest string containing the VEN (Vendor) and DEV (Device) codes (e.g., VEN_8086&DEV_15B8)
- Use a trusted lookup database or vendor site to identify the exact hardware model

**Step 2: Update the Driver**
- Right-click the device in Device Manager → Update driver
- Select "Search automatically for drivers"
- If Windows cannot find it, download the official driver package from the OEM website (Dell, HP, Lenovo, etc.)
- Run the installer or use "Browse my computer for drivers" to point directly to the extracted driver folder

---

### **Issue: Hardware Stopped Working After an Update (Code 43)**

**Symptoms:**
- Port, audio, or video components suddenly stop functioning
- Device manager shows error code 43

**Resolution:**
1. Open Device Manager and find the malfunctioning device
2. Right-click the device and select Properties
3. Go to the Driver tab
4. Click "Roll Back Driver" if the option is available
5. If Roll Back is greyed out, click "Uninstall Device"
6. Check the box that says "Attempt to remove the driver for this device" and click Uninstall
7. Click Action in the top menu bar of Device Manager and select "Scan for hardware changes" to reinstall the stock driver

---

### **Issue: USB Device Not Recognized**

**Symptoms:**
- External mouse, keyboard, or storage device fails to respond when plugged in
- USB error notification pops up in the system tray

**Resolution:**
1. Unplug the device and test it in a different physical USB port (preferably on the back of the machine if using a desktop)
2. Connect the device to a different computer to verify if the hardware itself is defective
3. In Device Manager, expand "Universal Serial Bus controllers"
4. Right-click each "USB Root Hub" → Properties → Power Management tab
5. Uncheck "Allow the computer to turn off this device to save power"
6. Restart the machine

---

##  Escalation Criteria

**Escalate to Level 2/3 if:**
- Updating or replacing the driver results in a system-wide crash (BSOD)
- The physical port or internal motherboard component is physically damaged
- Firmware or BIOS updates are required but blocked by a supervisor password
- Mass deployment of a specific driver is needed across multiple remote endpoints

---

##  Security Notes

- Only download drivers from official manufacturer websites (e.g., Intel, AMD, Dell)
- **NEVER** use third-party "Driver Updater" software utilities found online
- Ensure administrative credentials are used to install kernel-level drivers

---

##  Expected Resolution Time
- Simple driver update/rollback: 5-10 minutes
- Hardware ID lookup and manual install: 10-20 minutes
- Deep driver cleaning and reinstallation: 20-30 minutes

---

##  When to Escalate
- If the hardware fails to work on multiple known-good machines (hardware death)
- If installing a driver loop-crashes the machine into a Blue Screen
- If enterprise peripheral security policies (e.g., BitLocker/GPO port blocks) prevent device access

---

##  What to Document in Ticket
- Device name and Hardware ID (VEN/DEV codes)
- Error code shown in Device Manager properties
- Version of the driver before and after troubleshooting
- Physical ports tested during troubleshooting
