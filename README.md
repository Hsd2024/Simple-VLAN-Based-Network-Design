# Simple-VLAN-Based-Network-Design
This project is the design and implementation of a basic VLAN-based network to logically separate the HR, Finance and IT departments in the network switch by using Cisco Packet Tracer. The goal is to segment a small office network into multiple logical groups to enhance security, traffic management, and network efficiency.

# Why VLANs?
Improved Security: VLANs isolate broadcast domains. Devices in HR cannot communicate with Finance or IT  without routing, reducing potential attack surfaces.

Easier Management: Departments are logically separated, making it easier to troubleshoot and apply policies.

Reduced Broadcast Traffic: Each VLAN acts as its own broadcast domain, increasing network efficiency.

# Network Diagram
<img width="958" alt="Screenshot 2025-06-02 223701" src="https://github.com/user-attachments/assets/431cff1a-2bfe-4a6c-a775-1ebb0c26091a" />


# Example structure:

 3 VLANs: VLAN 10 (HR),......VLAN 20 (Finance),......VLAN 30 (IT)

 1 Layer 2 switch, 1 Router-on-a-Stick configuration, 1 DHCP server

 3 PCs per VLAN

Key Configurations

## Switch Configuration
First I renamed the switch to Bulding A switch as abbrevation of  ( B_A_Switch )

# Step one  rename your Switch:
<img width="520" alt="Screenshot 2025-06-02 231015 Rename switch" src="https://github.com/user-attachments/assets/90053e19-9ab1-47b1-8c15-43aaedd0e607" />

Go to the switch CLI and type bellow code.

Switch>

Switch>enable

Switch#configure terminal

Enter configuration commands, one per line.  End with CNTL/Z.

Switch(config)#

Switch(config)#hostname B_A_Switch

B_A_Switch(config)#

# Step 2 secure the Switch
<img width="521" alt="Screenshot 2025-06-02 225026-Enable mode password" src="https://github.com/user-attachments/assets/b8becdc9-f7fa-4cda-b86a-0c058323515a" />

Set Enable Passwords:

Purpose: Secure the switch by setting passwords for the enable modes.

Set the  Password:

B_A_Switch>enable

B_A_Switch#

B_A_Switch#configure terminal 

Switch(config)#

Switch(config)#Enable secret xxxx

Switch(config)#exit

Switch#write

Building configuration...

Done [OK]

# Step 3 Creat VLAN
![Vlan Configutation](https://github.com/user-attachments/assets/16c6d1ba-1e12-482e-ba33-26e65d29cca7)

B_A_Switch(config)#

B_A_Switch(config)# vlan 10

B_A_Switch(config-vlan)# name HR

B_A_Switch(config-vlan)# exit

B_A_Switch(config)# vlan 20

B_A_Switch(config-vlan)# name Finance

B_A_Switch(config-vlan)# exit

B_A_Switch(config)# vlan 30

B_A_Switch(config-vlan)# name IT

B_A_Switch(config-vlan)# exit

B_A_Switch(config-vlan)# 

# Step 4 Assign ports to VLANs
![Vlan Configutation2](https://github.com/user-attachments/assets/f895f532-c3c0-466f-9681-d8f9dd9b12d8)

B_A_Switch(config)# interface fa0/1 - 3

B_A_Switch(config-if)# switchport mode access

B_A_Switch(config-if)# switchport access vlan 10

B_A_Switch(config-if)# exit

B_A_Switch(config)# interface fa0/4 - 6

B_A_Switch(config-if)# switchport mode access

B_A_Switch(config-if)# switchport access vlan 20

B_A_Switch(config-if)# exit

B_A_Switch(config)# interface fa0/7 - 9

B_A_Switch(config-if)# switchport mode access

B_A_Switch(config-if)# switchport access vlan 30

B_A_Switch(config-if)# exit

# Step 5 Save configuration

<img width="524" alt="Screenshot 2025-06-03 213230- write configuration" src="https://github.com/user-attachments/assets/9e35a1c7-0799-4add-bd55-4e2800292044" />

