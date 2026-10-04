# Ancora-Education-Ucertify-Lab10
# Implementing Port Security

Implementing port security involves setting up network security measures to restrict access to a specific network interface. This is achieved by specifying allowed media access control address (MAC) addresses and blocking all other traffic. It helps enhance network security by permitting only authorized devices to connect to the network through the designated access port, thereby preventing unauthorized access and potential security breaches.

> **Original Lab Source**
> This lab was available through:
> [https://ancoraeducation.ucertify.com/app/?func=navigate_items&item_sequence=2]

## Instructions
Lab/Machine Environment:The PuTTY SSH Client is used in this lab. It is a popular SSH and Telnet Client that provides a secure way to access remote systems.You are provided with the Linux virtual machine

**Topology** 

Used Topology refers to the arrangement or configuration of the virtual network connections within the virtual machine (VM) environment. It defines how the virtual network interfaces and components are interconnected and organized.

## Objective of the Lab
This lab session demonstrates the steps involved in implementing port security. Upon completion of this lab, you will be able to:

Understand the significance of configuring port security on an access port.

Configure port security on an access port. 

Execute cmdlets in Terminal.

## PART A: Accessing the IOU1 Terminal
Access the PuTTY console with IP address as 192.168.116.128, Port as 5016, and Connection type as Other.
### STEP 1
On the left sidebar, click the Putty SSH Client icon

### STEP 2
In the PuTTY Configuration dialog box, perform the following steps: 

a.Type Host Name (or IP address) as 192.168.116.128 

b.Type Port as 5016

c.Under Connection type, select Other. 

d.Click Open to connect.

### STEP 3
If you don't get a command line prompt in the IOU1 terminal window, then press Enter.

## PART B: Configuring Port Security on an Access Port

### STEP 1
Execute the following commands (Note: Enter one command at a time.):
```bash
configure terminal
```
```bash
interface e0/0
```
### NOTE

configure terminal: This command allows you to enter global mode/configuration commands.

interface e0/0: This command is used to access the Ethernet0/0 interface.

### STEP 2
Execute the following commands to configure port security on an access port (Note: Enter one command at a time.):
```bash
switchport mode access
```
```bash
switchport port-security
```
```bash
switchport port-security maximum 2
```
```bash
switchport port-security mac-address sticky
```
```bash
switchport port-security violation protect
```
```bash
end
```
```bash
copy running-config startup-config
```
**Caution**

Press the Enter key if asked Destination filename [startup-config]?. 

If asked Overwrite the previous NVRAM configuration?[confirm], press Enter.

### NOTE 
switchport mode access: This command sets the interface to "access" mode, which means it will be used for end devices and not for trunking. 

switchport port-security: This command enables port security on the interface, which helps control the number of MAC addresses allowed on the port.

switchport port-security maximum 2: This command sets the maximum number of allowed MAC addresses to 2. This means that only two MAC addresses can be learned and used on this port. If a third MAC address is detected, it will trigger a violation.

switchport port-security mac-address sticky: This command makes the switch learn and store the MAC addresses of devices that connect to the port dynamically. This helps in building the initial MAC address list based on the devices that connect to the port. 

switchport port-security violation protect: This command sets the port security violation mode to "protect." In this mode, if a violation occurs (e.g., more than the allowed number of MAC addresses is detected), the switch will not take any specific action other than logging the violation. 

end: This command exits the interface configuration mode and returns to the global configuration mode. 

copy running-config startup-config: This command saves the current running configuration to the startup configuration, effectively making these changes persistent across reboots.

### STEP 3
Execute the following commands to observe the port security:
```bash
show port-security
```

## LAB SUMMARY
This lab session provides you with a straightforward and practical understanding of how to configure port security on an access port. Here's a summary of what you have learned: 

How to execute cmdlets in Terminal.

How to configure port security on an access port.

Now, you are equipped with the knowledge and skills to configure port security on an access port to enhance the efficiency and scalability of your network infrastructure.

## Disclaimer

This repository is for **educational and personal learning purposes only**.  

The original lab content belongs to **uCertify / Ancora Education** and remains their copyrighted material.  
This repository is not affiliated with, endorsed by, or sponsored by uCertify or Ancora Education.  

No copyright infringement is intended.  
Use of any tools or techniques mentioned here should only be performed in authorized, legal environments.
