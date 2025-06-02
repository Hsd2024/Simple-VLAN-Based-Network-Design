# Simple-VLAN-Based-Network-Design
This project is the design and implementation of a basic VLAN-based network to logically separate the HR, Finance and IT departments in the network switch by using Cisco Packet Tracer. The goal is to segment a small office network into multiple logical groups to enhance security, traffic management, and network efficiency.

# Why VLANs?
Improved Security: VLANs isolate broadcast domains. Devices in HR cannot communicate with Finance or IT  without routing, reducing potential attack surfaces.

Easier Management: Departments are logically separated, making it easier to troubleshoot and apply policies.

Reduced Broadcast Traffic: Each VLAN acts as its own broadcast domain, increasing network efficiency.

# Network Diagram
(place the network diagram here)

# Example structure:

3 VLANs: VLAN 10 (HR),......VLAN 20 (Finance),......VLAN 30 (IT)

1 Layer 2 switch, 1 Router-on-a-Stick configuration, 1 DHCP server

3 PCs per VLAN

Key Configurations

## Switch Configuration (VLANs & Trunk Port)
First I renamed the switch to Bulding A switch as abbrevation of  ( B_A_Switch )

# Step one  rename your Switch:
Go to the switch CLI and type bellow code.

Switch>

Switch>enable

Switch#configure terminal

Enter configuration commands, one per line.  End with CNTL/Z.

Switch(config)#

Switch(config)#hostname B_A_Switch

B_A_Switch(config)#

# Step 2 secure the Switch
Set Console and Enable Passwords:

Purpose: Secure the switch by setting passwords for the console and enable modes.
Set the Console Password:

B_A_Switch(config)# line console 0

B_A_Switch(config-line)# password cisco

B_A_Switch(config-line)# login

B_A_Switch(config-line)# exit

B_A_Switch(config)#

# Creat VLAN

B_A_Switch(config)#

B_A_Switch(config)# vlan 10

B_A_Switch(config-vlan)# name HR

B_A_Switch(config)# vlan 20

B_A_Switch(config-vlan)# name Finance

B_A_Switch(config)# vlan 30

B_A_Switch(config-vlan)# name IT


# Assign ports to VLANs
B_A_Switch(config)# interface fa0/1

B_A_Switch(config-if)# switchport access vlan 10

B_A_Switch(config)# interface fa0/2

B_A_Switch(config-if)# switchport access vlan 20

B_A_Switch(config)# interface fa0/3

B_A_Switch(config-if)# switchport access vlan 20


# Trunk to router
Switch(config)# interface fa0/24

Switch(config-if)# switchport mode trunk

# Router Configuration (Router-on-a-Stick)

Router(config)# interface fa0/0.10

Router(config-subif)# encapsulation dot1Q 10

Router(config-subif)# ip address 192.168.10.1 255.255.255.0

Router(config)# interface fa0/0.20

Router(config-subif)# encapsulation dot1Q 20

Router(config-subif)# ip address 192.168.20.1 255.255.255.0

Router(config)# interface fa0/0.30

Router(config-subif)# encapsulation dot1Q 30

Router(config-subif)# ip address 192.168.30.1 255.255.255.0


