# Setup-and-Using-Firewall-in-Windows

## The Objective of this project was to Configure and test basic firewall rules to allow or block traffic and understand network traffic filtering. In this setting Port 23 for Telnet was used.

## Tools, Environment and Commands used

### Tools
- Windows Defender
- Telnet Client
- Command Prompt

### Environment
- **OS**: Windows 11
- **Firewall Interfcae**: GUI (Windows Defender Firewall with Advanced Security)

### Commands
- `telnet localhost 23`

---
## Windows Firewall Configuration – GUI Steps

## Firewall Rule Details

- **Rule Name**: Block Telnet
- **Protocol**: TCP
- **Port**: 23
- **Direction**: Inbound
- **Action**: Block the connection
- **Profile**: All (Domain, Private, Public)


### Step 1: Open Firewall
- Go to Control Panel → System and Security → Windows Defender Firewall.
- Click "Advanced settings" on the left pane.

### Step 2: Create a New Inbound Rule
- Inbound Rules → Right-click → "New Rule..."
- Select "Port" → Click "Next"
- Choose "TCP", and type "23" in "Specific local ports"
- Select "Block the connection" → Click "Next"
- Apply to Domain, Private, and Public → Click "Next"
- Name the rule: `Block Telnet` → Click "Finish"

### Step 3: Test with Telnet
- Open Command Prompt → Type: `telnet localhost 23`


## Revert Step

After testing the firewall rule, I deleted the "Block Telnet" rule to return the firewall configuration to its original state.

### Windows Steps:
- Open Windows Defender Firewall → Advanced Settings → Inbound Rules
- Right-click on `Block Telnet` → Click "Delete"

---
## Key Findings

#### With the rule active (blocking):
- The connection failed as expected.
- Screenshot attached.

#### With the rule removed:
- The connection still failed.
- This is because no Telnet server was listening on port 23.
- The test confirms that the firewall rule affected the port, but the service was not available regardless.
Even though there was no actual Telnet server running, I demonstrated the firewall's effect by testing connectivity on the specified port.

---
## Summary Report
Firewalls filter network traffic by inspecting data packets against predefined security rules and deciding whether to allow or block them based on criteria such as IP addresses, ports, and protocols.


### How Firewalls Filter Traffic
- **Packet Inspection**: Firewalls analyze the headers of data packets, which contain information like source and destination IP addresses, source and destination ports, and the protocol used (e.g., TCP, UDP, Telnet) .

- **Rule Comparison**: Each packet is compared against a set of security rules or Access Control Lists (ACLs). These rules specify which traffic is permitted or denied based on the packet’s header information .

- **Decision Making**: If a packet matches an allowed rule (e.g., traffic to port 80 for HTTP), it is admitted; if it matches a blocked rule (e.g., traffic to port 23 for Telnet), it is denied and dropped .

- **Types of Filtering**: Firewalls can use different methods such as:

     - **Packet Filtering**: The simplest form, examining packet headers only .

    - **Stateful Inspection**: Tracking active connections to allow only legitimate response packets .

    - **Proxy Services**: Acting as an intermediary to control data flow .

- **Logging and Alerts**: Firewalls often log blocked attempts and can alert administrators about suspicious traffic .

### Blocking Telnet Traffic
- Telnet uses TCP port 23 for remote connections but is considered insecure, so most firewalls block traffic on this port to prevent unauthorized or insecure remote access . When you block Telnet (port 23) in a firewall, any incoming or outgoing packets destined for or originating from port 23 are dropped or rejected based on your firewall rules . 
- The behavior observed when Telnet is blocked depends on the firewall’s response mode:

    - **Deny**: The firewall silently drops packets, causing Telnet clients to hang or time out without immediate feedback .

    - **Reject**: The firewall actively sends a "connection refused" message back, causing Telnet to fail quickly with an error


In this task, I successfully configured and tested firewall rules to control network traffic using Windows Defender Firewall. I created an inbound rule to block traffic on port 23 (Telnet), tested the rule using the telnet command, and then reverted the configuration by deleting the rule. <br>
Through this process, I gained hands-on experience with:

- Creating and managing firewall rules via GUI and/or command line

- Testing port accessibility using Telnet

- Understanding how firewalls filter traffic based on ports, protocols, and connection direction

- Safely reverting changes to restore the system to its original state

---

## Attachments
- Screenshots of GUI in `screenshot_configuration` folder

