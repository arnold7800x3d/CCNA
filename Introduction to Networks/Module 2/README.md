# Packet Tracer - Navigate the IOS
## Part 1: Establish Basic Connections, Access the CLI and Explore Help
### Step 2: Establish a terminal session with S1
b. Click the __Terminal__ application icon. Verify that the Port Configuration default settings are correct.
Question:
What is the setting for bits per second?What is the setting for bits per second?
```
9600
```
c. The screen that appears may have several messages displayed. Somewhere on the screen there should be a Press RETURN to get started! message. Press ENTER.
Question:
What is the prompt displayed on the screen?
```
S1>
```

### Step 3: Explore the IOS Help
a. The IOS can provide help for commands depending on the level accessed. The prompt currently
displayed is called __User EXEC__, and the device is waiting for a command. The most basic form of help is
to type a question mark (?) at the prompt to display a list of commands.
Open Configuration Window
S1> __?__
Question:
Which command begins with the letter ‘C’?
```
connect
```
b. At the prompt, type t and then a question mark (?).
S1> __t?__
Question:
Which commands are displayed?
```
telnet terminal traceroute
```
c. At the prompt, type te and then a question mark (?).
S1> __te?__
Question:
Which commands are displayed?
```
telnet terminal
```

## Part 2: Explore EXEC Modes
### Step 1: Enter privileged EXEC mode
a. At the prompt, type the question mark (?).
S1> __?__
Question:
What information is displayed for the __enable__ command?
```
Turn on privileged commands
```
b. Type __en__ and press the __Tab__ key.
S1> __en<\Tab>__
Question:
What displays after pressing the __Tab__ key?
```
The command is auto-completed to enable on a new line.
```
What would happen if you typed __te<\Tab>__ at the prompt?
```
The command is not auto-completed since the characters provided do not point to a unique command. Te could either be telnet or terminal.
```
c. Enter the __enable__ command and press ENTER.
Question:
How does the prompt change?
```
It goes from S1> to S1#
```
d. When prompted, type the question mark (?).
S1# __?__
One command starts with the letter ‘C’ in user EXEC mode.
Question:
How many commands are displayed now that privileged EXEC mode is active?
```
5 commands - clear clock configure connect copy
```
### Step 2: Enter Global Configuration mode
a. When in privileged EXEC mode, one of the commands starting with the letter ‘C’ is __configure__. Type either
the full command or enough of the command to make it unique. Press the __<\Tab>__ key to issue the
command and press ENTER.
S1# __configure__<br>
Question:
What is the message that is displayed?
```
Configuring from terminal, memory or network [terminal]?
```
b. Press Enter to accept the default parameter that is enclosed in brackets __[\terminal]__.<br>
Question:
How does the prompt change?
```
It changes from S1# to S1(config)#
```

## Part 3: Set the Clock
### Step 1: Use the clock command
a. Use the __clock__ command to further explore Help and command syntax. Type __show clock__ at the privileged
EXEC prompt.<br>
S1# __show clock__<br>
Question:
What information is displayed?
```
Date and time information
```
What is the year that is displayed?
```
1993
```
b. Use the context-sensitive help and the ___clock__ command to set the time on the switch to the current time.
Enter the command __clock__ and press ENTER.<br>
S1# __clock<\ENTER>__<br>
Question
What information is displayed?
```
% Incomplete command
```
c. The “% Incomplete command” message is returned by the IOS. This indicates that the __clock__ command
needs more parameters. Any time more information is needed, help can be provided by typing a space
after the command and the question mark (?).<br>
S1# __clock ?__<br>
Question:
What information is displayed?
```
set  Set the time and date
```
d. Set the clock using the __clock set__ command. Proceed through the command one step at a time.<br>
S1# __clock set ?__<br>
Questions:
What information is being requested?
```
hh:mm:ss  Current Time
```
What would have been displayed if only the __clock set__ command had been entered, and no request for help was made by using the question mark?
```
% Incomplete command
```
### Step 2: Explore additional command messages
b. Issue the following commands and record the messages:<br>
S1# __cl<\tab>__<br>
Questions:
What information was returned?
```
The command is not auto-completed since the characters provided do not point to a unique command. It could either be clear or clock.
```
S1# __clock__<br>
Question:
What information was returned?
```
% Incomplete command
```
S1# __clock set 25:00:00__<br>
Question:
What information was returned?
```
% Invalid input detected at '^' marker. with the caret being below the 2. The final hour in the 24-hour clock valid to begin with a 2 is 23.
```
S1# clock set 15:00:00 32<br>
Question:
What information was returned?
```
% Invalid input detected at '^' marker. with the caret being below the 3.
```

# Packet Tracer - Navigate the IOS using a Terminal Client for Console Connectivity - Physical Mode
## Part 2: Display the Switch IOS Image version
### Step 1: Display the switch IOS image version.
While you are in the user EXEC mode, use the __show version__ command to display the IOS version for the switch.<br>
Switch> __show version__<br>
Question:
Which IOS image and version is currently in use by the switch?
```
IOS Image- C2960-LANBASE-M, IOS Version-12.2
```

## Reflection Question
1. How do you prevent unauthorized personnel from accessing the Cisco device through the console port?
```
Setting up a console password which requires authentication prior to granting access
```

2. What are the advantages and disadvantages of using the serial console connection compared to the USB console connection to a Cisco router or switch?
```

```

# Packet Tracer - Configure Initial Switch Settings
## Part 1: Verify the Default Switch Configuration
### Step 2: Examine the current switch configuration.
Enter the show running-config command.<br>

Switch# __show running-config__<br>

Answer the following questions:
How many Fast Ethernet interfaces does the switch have?
```
24
```
How many Gigabit Ethernet interfaces does the switch have?
```
2
```
What is the range of values shown for the vty lines?
```
0-4
5-15
```
Which command will display the current contents of non-volatile random-access memory (NVRAM)?
```
show startup-config
```
Why does the switch respond with “startup-config is not present?”
```

```

## Part 2: Create a Basic Switch Configuration
### Step 2: Secure access to the console line.
To secure access to the console line, access config-line mode and set the console password to __letmein__.<br>

S1# __configure terminal__<br>
Enter configuration commands, one per line. End with CNTL/Z.<br>
S1(config)# __line console 0__<br>
S1(config-line)# __password letmein__<br>
S1(config-line)# __login__<br>
S1(config-line)# __exit__<br>
S1(config)# __exit__<br>
%SYS-5-CONFIG_I: Configured from console by console<br>
S1#<br>

Question:<br>
Why is the __login__ command required?
```
To enable the password for use when accessing the switch later on.
```

### Step 7: Verify that the enable secret password is added to the configuration file.
Enter the show running-config command again to verify the new enable secret password is configured.
__Note__: You can abbreviate __show running-config__ as
S1# __show run__<br>
Questions:
What is displayed for the enable secret password?
```
$1$mERr$ILwq/b7kc.7X/ejA4Aosn0
```
Why is the enable secret password displayed differently from what we configured?
```
The password has been encrypted.
```

### Step 8: Encrypt the enable and console passwords.
As you noticed in Step 7, the __enable secret__ password was encrypted, but the __enable__ and __console__ passwords were still in plain text. We will now encrypt these plain text passwords using the __service password-encryption__ command.<br>
S1# __config t__<br>
S1(config)# __service password-encryption__<br>
S1(config)# __exit__<br>
Question:
If you configure any more passwords on the switch, will they be displayed in the configuration file as plain text or in encrypted form? Explain.
```
They will be displayed in encrypted form. This is because the password encryption service has been enabled on the switch thus all forthcoming passwords will be secured via encryption.
```

## Part 3: Configure a MOTD Banner
### Step 1: Configure a message of the day (MOTD) banner.
The Cisco IOS command set includes a feature that allows you to configure messages that anyone logging onto the switch sees. These messages are called message of the day, or MOTD banners. Enclose the banner text in quotations or use a delimiter different from any character appearing in the MOTD string.<br>

S1# __config t__<br>
S1(config)# __banner motd "This is a secure system. Authorized Access Only!"__<br>
S1(config)# __exit__<br>
%SYS-5-CONFIG_I: Configured from console by console<br>
S1#<br>
Questions:
When will this banner be displayed?
```
When a user attempts to access the user EXEC mode. Basically upon initial device access.
```
Why should every switch have a MOTD banner?
```
It can aid in legal proceedings where users can be informed of the authorization level(s) set for the device, and the consequences of violating the set authorization(s).
```

## Part 4: Save and Verify Configuration Files to NVRAM
### Step 1: Verify that the configuration is accurate using the show run command.
Save the configuration file. You have completed the basic configuration of the switch. Now back up the running configuration file to NVRAM to ensure that the changes made are not lost if the system is rebooted or loses power.<br>
S1# __copy running-config startup-config__<br>
Destination filename [\startup-config]?__[\Enter]__<br>
Building configuration...<br>
[\OK]<br>
Questions:
What is the shortest, abbreviated version of the __copy running-config startup-config__ command?
```
copy run start
```
Examine the startup configuration file.

Which command will display the contents of NVRAM?
```
show startup-config
```
Are all the changes that were entered recorded in the file?
```
Yes
```

## Part 5: Configure S2
You have completed the configuration on S1. You will now configure S2. If you cannot remember the commands, refer to Parts 1 to 4 for assistance.
Configure S2 with the following parameters:
Open Configuration Window for S2<br>
a. Device name: __S2__
```
Switch>en
Switch#conf t
Switch(config)#hostname S2
```
b. Protect access to the console using the __letmein__ password.
```
S2(config)#line console 0
S2(config-line)#password letmein
S2(config-line)#login
S2(config-line)#end
```
c. Configure an enable password of c1$c0 and an enable secret password of itsasecret.
```
S2#conf t
S2(config)#enable password c1$c0
S2(config)#enable secret itsasecret
S2(config)#end
```
d. Configure an appropriate message to those logging into the switch.
```
S2(config)#banner motd "Authorized personnel only!"
```
e. Encrypt all plain text passwords.
```
S2(config)# service password-encryption
```
f. Ensure that the configuration is correct.
```
S2(config)#end
S2#show run
```
g. Save the configuration file to avoid loss if the switch is powered down.
```
copy run start
```

# Packet Tracer - Implement Basic Connectivity
## Part 1: Perform a Basic Configuration on S1 and S2
### Step 1: Configure S1 with a hostname.<br>
a. Click S1 and then click the CLI tab.<br>
b. Enter the correct command to configure the hostname as S1.<br>
```
Switch>en
Switch#conf t
Switch(config)#hostname S1
```
### Step 2: Configure the console and encrypted privileged EXEC mode passwords.
a. Use __cisco__ for the console password.
```
S1(config)#line console 0
S1(config-line)#password cisco
S1(config-line)#login
S1(config-line)#end
```
b. Use __class__ for the privileged EXEC mode password.
```
S1#conf t
S1(config)#enable secret class
S1(config)#end
```
### Step 3: Verify the password configurations for S1.
Question:
How can you verify that both passwords were configured correctly?
```
By returning back to the user EXEC mode. It should show a Password: prompt and after entering cisco and attempting to access privileged EXEC mode, it should also request for a password/
```
Use an appropriate banner text to warn unauthorized access. The following text is an example:<br>

__Authorized access only. Violators will be prosecuted to the full extent of the law.__
```
S1#conf t
S1(config)#banner motd "Authorized access only. Violators will be prosecuted to the full extent of the law."
```
### Step 4: Save the configuration file to NVRAM.
Question:
Which command do you issue to accomplish this step?
```
S1#copy run start
```

## Part 2: Configure the PCs
### Step 2: Test connectivity to switches.
a. Click PC1. Close the IP Configuration window if it is still open. In the Desktop tab, click Command Prompt.<br>
b. Type the ping command and the IP address for S1 and press Enter.
```
Packet Tracer PC Command Line 1.0
PC> ping 192.168.1.253
```
Question:
Were you successful? Explain.
```
No. The request times out since we are attempting to ping an IP address that has not yet been configured on the SVI for S1
```

## Part 3: Configure the Switch Management Interface
### Step 1: Configure S1 with an IP address.
Switches can be used as plug-and-play devices. This means that they do not need to be configured for them to work. Switches forward information from one port to another based on MAC addresses.<br>
Question:
If this is the case, why would we configure it with an IP address?
```
To allow remote management over a network.
```
Use the following commands to configure S1 with an IP address.
```
S1# configure terminal
Enter configuration commands, one per line. End with CNTL/Z.
S1(config)# interface vlan 1
S1(config-if)# ip address 192.168.1.253 255.255.255.0
S1(config-if)# no shutdown
%LINEPROTO-5-UPDOWN: Line protocol on Interface Vlan1, changed state to up
S1(config-if)#
S1(config-if)# exit
S1#
```
Question:
Why do you enter the __no shutdown__ command?
```
To enable the interface
```
### Step 2: Configure S2 with an IP address.
Use the information in the Addressing Table to configure S2 with an IP address.
```
S2# configure terminal
Enter configuration commands, one per line. End with CNTL/Z.
S2(config)# interface vlan 1
S2(config-if)# ip address 192.168.1.254 255.255.255.0
S2(config-if)# no shutdown
%LINEPROTO-5-UPDOWN: Line protocol on Interface Vlan1, changed state to up
S2(config-if)#
S2(config-if)# exit
S2#
```
### tep 3: Verify the IP address configuration on S1 and S2.
Use the __show ip interface brief__ command to display the IP address and status of all the switch ports and interfaces. You can also use the __show running-config__ command<br>
S1
```
S1#show ip int brief
Interface              IP-Address      OK? Method Status                Protocol 
FastEthernet0/1        unassigned      YES manual up                    up 
FastEthernet0/2        unassigned      YES manual up                    up 
FastEthernet0/3        unassigned      YES manual down                  down 
FastEthernet0/4        unassigned      YES manual down                  down 
FastEthernet0/5        unassigned      YES manual down                  down 
FastEthernet0/6        unassigned      YES manual down                  down 
FastEthernet0/7        unassigned      YES manual down                  down 
FastEthernet0/8        unassigned      YES manual down                  down 
FastEthernet0/9        unassigned      YES manual down                  down 
FastEthernet0/10       unassigned      YES manual down                  down 
FastEthernet0/11       unassigned      YES manual down                  down 
FastEthernet0/12       unassigned      YES manual down                  down 
FastEthernet0/13       unassigned      YES manual down                  down 
FastEthernet0/14       unassigned      YES manual down                  down 
FastEthernet0/15       unassigned      YES manual down                  down 
FastEthernet0/16       unassigned      YES manual down                  down 
FastEthernet0/17       unassigned      YES manual down                  down 
FastEthernet0/18       unassigned      YES manual down                  down 
FastEthernet0/19       unassigned      YES manual down                  down 
FastEthernet0/20       unassigned      YES manual down                  down 
FastEthernet0/21       unassigned      YES manual down                  down 
FastEthernet0/22       unassigned      YES manual down                  down 
FastEthernet0/23       unassigned      YES manual down                  down 
FastEthernet0/24       unassigned      YES manual down                  down 
GigabitEthernet0/1     unassigned      YES manual down                  down 
GigabitEthernet0/2     unassigned      YES manual down                  down 
Vlan1                  192.168.1.253   YES manual up                    up
```
S2
```

S2#show ip int brief
Interface              IP-Address      OK? Method Status                Protocol 
FastEthernet0/1        unassigned      YES manual up                    up 
FastEthernet0/2        unassigned      YES manual up                    up 
FastEthernet0/3        unassigned      YES manual down                  down 
FastEthernet0/4        unassigned      YES manual down                  down 
FastEthernet0/5        unassigned      YES manual down                  down 
FastEthernet0/6        unassigned      YES manual down                  down 
FastEthernet0/7        unassigned      YES manual down                  down 
FastEthernet0/8        unassigned      YES manual down                  down 
FastEthernet0/9        unassigned      YES manual down                  down 
FastEthernet0/10       unassigned      YES manual down                  down 
FastEthernet0/11       unassigned      YES manual down                  down 
FastEthernet0/12       unassigned      YES manual down                  down 
FastEthernet0/13       unassigned      YES manual down                  down 
FastEthernet0/14       unassigned      YES manual down                  down 
FastEthernet0/15       unassigned      YES manual down                  down 
FastEthernet0/16       unassigned      YES manual down                  down 
FastEthernet0/17       unassigned      YES manual down                  down 
FastEthernet0/18       unassigned      YES manual down                  down 
FastEthernet0/19       unassigned      YES manual down                  down 
FastEthernet0/20       unassigned      YES manual down                  down 
FastEthernet0/21       unassigned      YES manual down                  down 
FastEthernet0/22       unassigned      YES manual down                  down 
FastEthernet0/23       unassigned      YES manual down                  down 
FastEthernet0/24       unassigned      YES manual down                  down 
GigabitEthernet0/1     unassigned      YES manual down                  down 
GigabitEthernet0/2     unassigned      YES manual down                  down 
Vlan1                  192.168.1.254   YES manual up                    up
```
### Step 4: Save configurations for S1 and S2 to NVRAM.
Question:
Which command is used to save the configuration file in RAM to NVRAM?
```
copy run start
```
# Packet Tracer - Basic Switch and End Device Configuration
## Instructions
Configure the devices to fulfill the requirements below.

## Requirements
Use a console connection to access each switch.<br>
Name ASw-1 and ASw-2 switches.<br>
Use the 8ubRu password for all lines.<br>
Use the C9WrE secret password.<br>
Encrypt all clear text passwords.<br>
Configure an appropriate message-of-the-day (MOTD) banner.<br>
Configure addressing for all devices according to the Addressing Table.<br>
Save your configurations.<br>
Verify connectivity between all devices.<br>
*ASw-1*
```
Switch>en
Switch#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#hostname ASw-1
ASw-1(config)#line console 0
ASw-1(config-line)#password 8ubRu
ASw-1(config-line)#login
ASw-1(config-line)#exit
ASw-1(config)#enable secret C9WrE
ASw-1(config)#service password-encryption
ASw-1(config)#banner motd "Authorized users only. Violators will be prosecuted to the full extent of the law."
ASw-1(config)#int vlan 1
ASw-1(config-if)#ip add 128.107.20.10 255.255.255.0
ASw-1(config-if)#no shut

ASw-1(config-if)#
%LINK-3-UPDOWN: Interface Vlan1, changed state to down

%LINEPROTO-5-UPDOWN: Line protocol on Interface Vlan1, changed state to up

ASw-1(config-if)#exit
ASw-1(config)#end
ASw-1#
%SYS-5-CONFIG_I: Configured from console by console

ASw-1#copy run start
Destination filename [startup-config]? 
Building configuration...
[OK]
ASw-1#
```
*ASw-2*
```
Switch>en
Switch#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#host ASw-2
ASw-2(config)#line console 0
ASw-2(config-line)#password 8ubRu
ASw-2(config-line)#login
ASw-2(config-line)#exit
ASw-2(config)#enable secret C9WrE
ASw-2(config)#service password-en
ASw-2(config)#service password-encryption 
ASw-2(config)#banner motd "Authorized users only! Violators will be prosecuted to the full extent of the law"
ASw-2(config)#int vlan 1
ASw-2(config-if)#ip add 128.107.20.15 255.255.255.0
ASw-2(config-if)#no shut

ASw-2(config-if)#
%LINK-3-UPDOWN: Interface Vlan1, changed state to down

%LINEPROTO-5-UPDOWN: Line protocol on Interface Vlan1, changed state to up

ASw-2(config-if)#end
ASw-2#
```

# Packet Tracer - Basic Switch and End Device Configuration - Physical Mod
## Part 3: Configure and Verify Basic Switch Settings
a. On the Cable Pegboard, click a Console cable. Connect the console cable between S1 and PC-A.<br>
b. Establish a console connection to the switch S1 from PC-A using the Packet Tracer generic Terminal program (PC-A > Desktop > Terminal). Press ENTER to get the Switch> prompt.<br>
c. You can access all switch commands in privileged EXEC mode. The privileged EXEC command set includes those commands contained in user EXEC mode, as well as the configure command through which access to the remaining command modes are gained. Enter privileged EXEC mode by entering the enable command.<br>
Open Configuration Window<br>
d.     The prompt changed from Switch> to Switch# which indicates privileged EXEC mode. Enter global configuration mode.<br>
e.     The prompt changed to Switch(config)# to reflect global configuration mode. Give the switch a name according to the Addressing Table.
*S1*
```
Switch>en
Switch#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#hostname S1
```
*S2*
```
Switch>en
Switch#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)#hostname S2
```
f. Enter local passwords. Use class as the privileged EXEC password and cisco as the password for console access.
*S1*
```
S1(config)#line console 0
S1(config-line)#password cisco
S1(config-line)#login
S1(config-line)#exit
S1(config)#enable secret class
```
*S2*
```
S2(config)#line console 0
S2(config-line)#password cisco
S2(config-line)#login
S2(config-line)#exit
S2(config)#enable secret class
```
g. Configure and enable the VLAN 1 interface according to the Addressing Table.
*S1*
```
S1(config)#int vlan 1
S1(config-if)#ip add 192.168.1.1 255.255.255.0
S1(config-if)#no shut

S1(config-if)#
%LINK-3-UPDOWN: Interface Vlan1, changed state to down

%LINEPROTO-5-UPDOWN: Line protocol on Interface Vlan1, changed state to up

S1(config-if)#
```
*S2*
```
S1(config)#int vlan 1
S2(config-if)#ip add 192.168.1.2 255.255.255.0
S2(config-if)#no shut

S2(config-if)#
%LINK-3-UPDOWN: Interface Vlan1, changed state to down

%LINEPROTO-5-UPDOWN: Line protocol on Interface Vlan1, changed state to up

S2(config-if)#
```
h. A login banner, known as the message of the day (MOTD) banner, should be configured to warn anyone accessing the switch that unauthorized access will not be tolerated. Configure an appropriate MOTD banner to warn about unauthorized access.
*S1*
```
S1(config-if)#exit
S1(config)#banner motd "Authorized access only! Violators will be prosecuted to the full extent of the law."
```
*S2*
```
S2(config-if)#exit
S2(config)#banner motd "Authorized access only! Violators will be prosecuted to the full extent of the law."
```
i. Save the configuration to the startup file on non-volatile random access memory (NVRAM).
*S1*
```
S1(config)#end
S1#
%SYS-5-CONFIG_I: Configured from console by console

S1#copy run start
```
*S2*
```
S2(config)#end
S2#
%SYS-5-CONFIG_I: Configured from console by console

S2#copy run start
```
j. Display the current configuration.
*S1*
```
S1#show run
S1#show running-config 
Building configuration...

Current configuration : 1258 bytes
!
version 12.2
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname S1
!
enable secret 5 $1$mERr$9cTjUIEqNGurQiFU.ZeCi1
!
!
!
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
interface FastEthernet0/1
!
interface FastEthernet0/2
!
interface FastEthernet0/3
!
interface FastEthernet0/4
!
interface FastEthernet0/5
!
interface FastEthernet0/6
!
interface FastEthernet0/7
!
interface FastEthernet0/8
!
interface FastEthernet0/9
!
interface FastEthernet0/10
!
interface FastEthernet0/11
!
interface FastEthernet0/12
!
interface FastEthernet0/13
!
interface FastEthernet0/14
!
interface FastEthernet0/15
!
interface FastEthernet0/16
!
interface FastEthernet0/17
!
interface FastEthernet0/18
!
interface FastEthernet0/19
!
interface FastEthernet0/20
!
interface FastEthernet0/21
!
interface FastEthernet0/22
!
interface FastEthernet0/23
!
interface FastEthernet0/24
!
interface GigabitEthernet0/1
!
interface GigabitEthernet0/2
!
interface Vlan1
 ip address 192.168.1.1 255.255.255.0
!
banner motd ^CAuthorized access only! Violators will be prosecuted to the full extent of the law^C
!
!
!
line con 0
 password cisco
 login
!
line vty 0 4
 login
line vty 5 15
 login
!
!
!
!
end
```
*S2*
```
S2#show run
Building configuration...

Current configuration : 1259 bytes
!
version 15.0
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname S2
!
enable secret 5 $1$mERr$9cTjUIEqNGurQiFU.ZeCi1
!
!
!
!
!
!
spanning-tree mode pvst
spanning-tree extend system-id
!
interface FastEthernet0/1
!
interface FastEthernet0/2
!
interface FastEthernet0/3
!
interface FastEthernet0/4
!
interface FastEthernet0/5
!
interface FastEthernet0/6
!
interface FastEthernet0/7
!
interface FastEthernet0/8
!
interface FastEthernet0/9
!
interface FastEthernet0/10
!
interface FastEthernet0/11
!
interface FastEthernet0/12
!
interface FastEthernet0/13
!
interface FastEthernet0/14
!
interface FastEthernet0/15
!
interface FastEthernet0/16
!
interface FastEthernet0/17
!
interface FastEthernet0/18
!
interface FastEthernet0/19
!
interface FastEthernet0/20
!
interface FastEthernet0/21
!
interface FastEthernet0/22
!
interface FastEthernet0/23
!
interface FastEthernet0/24
!
interface GigabitEthernet0/1
!
interface GigabitEthernet0/2
!
interface Vlan1
 ip address 192.168.1.2 255.255.255.0
!
banner motd ^CAuthorized access only! Violators will be prosecuted to the full extent of the law.^C
!
!
!
line con 0
 password cisco
 login
!
line vty 0 4
 login
line vty 5 15
 login
!
!
!
!
end
```
k. Display the IOS version and other useful switch information.
*S1*
```
S1#show ver
Cisco IOS Software, C2960 Software (C2960-LANBASE-M), Version 12.2(25)FX, RELEASE SOFTWARE (fc1)
Copyright (c) 1986-2005 by Cisco Systems, Inc.
Compiled Wed 12-Oct-05 22:05 by pt_team

ROM: C2960 Boot Loader (C2960-HBOOT-M) Version 12.2(25r)FX, RELEASE SOFTWARE (fc4)

System returned to ROM by power-on

Cisco WS-C2960-24TT (RC32300) processor (revision C0) with 21039K bytes of memory.


24 FastEthernet/IEEE 802.3 interface(s)
2 Gigabit Ethernet/IEEE 802.3 interface(s)

63488K bytes of flash-simulated non-volatile configuration memory.
Base ethernet MAC Address       : 00E0.F780.A6A8
Motherboard assembly number     : 73-9832-06
Power supply part number        : 341-0097-02
Motherboard serial number       : FOC103248MJ
Power supply serial number      : DCA102133JA
Model revision number           : B0
Motherboard revision number     : C0
Model number                    : WS-C2960-24TT
System serial number            : FOC1033Z1EY
Top Assembly Part Number        : 800-26671-02
Top Assembly Revision Number    : B0
Version ID                      : V02
CLEI Code Number                : COM3K00BRA
Hardware Board Revision Number  : 0x01


Switch   Ports  Model              SW Version              SW Image
------   -----  -----              ----------              ----------
*    1   26     WS-C2960-24TT      12.2                    C2960-LANBASE-M

Configuration register is 0xF
```
*S2*
```
S2#show ver
Cisco IOS Software, C2960 Software (C2960-LANBASEK9-M), Version 15.0(2)SE4, RELEASE SOFTWARE (fc1)
Technical Support: http://www.cisco.com/techsupport
Copyright (c) 1986-2013 by Cisco Systems, Inc.
Compiled Wed 26-Jun-13 02:49 by mnguyen

ROM: Bootstrap program is C2960 boot loader
BOOTLDR: C2960 Boot Loader (C2960-HBOOT-M) Version 12.2(25r)FX, RELEASE SOFTWARE (fc4)

Switch uptime is 39 minutes
System returned to ROM by power-on
System image file is "flash:c2960-lanbasek9-mz.150-2.SE4.bin"


This product contains cryptographic features and is subject to United
States and local country laws governing import, export, transfer and
use. Delivery of Cisco cryptographic products does not imply
third-party authority to import, export, distribute or use encryption.
Importers, exporters, distributors and users are responsible for
compliance with U.S. and local country laws. By using this product you
agree to comply with applicable laws and regulations. If you are unable
to comply with U.S. and local laws, return this product immediately.

A summary of U.S. laws governing Cisco cryptographic products may be found at:
http://www.cisco.com/wwl/export/crypto/tool/stqrg.html

If you require further assistance please contact us by sending email to
export@cisco.com.

cisco WS-C2960-24TT-L (PowerPC405) processor (revision B0) with 65536K bytes of memory.
Processor board ID FOC1010X104
Last reset from power-on
1 Virtual Ethernet interface
24 FastEthernet interfaces
2 Gigabit Ethernet interfaces
The password-recovery mechanism is enabled.

64K bytes of flash-simulated non-volatile configuration memory.
Base ethernet MAC Address       : 00:01:64:7B:46:B6
Motherboard assembly number     : 73-10390-03
Power supply part number        : 341-0097-02
Motherboard serial number       : FOC10093R12
Power supply serial number      : AZS1007032H
Model revision number           : B0
Motherboard revision number     : B0
Model number                    : WS-C2960-24TT-L
System serial number            : FOC1010X104
Top Assembly Part Number        : 800-27221-02
Top Assembly Revision Number    : A0
Version ID                      : V02
CLEI Code Number                : COM3L00BRA
Hardware Board Revision Number  : 0x01


Switch Ports Model              SW Version            SW Image
------ ----- -----              ----------            ----------
*    1 26    WS-C2960-24TT-L    15.0(2)SE4            C2960-LANBASEK9-M


Configuration register is 0xF
```
l. Display the status of the connected interfaces on the switch.
*S1*
```
S1# show ip int brief
Interface              IP-Address      OK? Method Status                Protocol 
FastEthernet0/1        unassigned      YES manual up                    up 
FastEthernet0/2        unassigned      YES manual down                  down 
FastEthernet0/3        unassigned      YES manual down                  down 
FastEthernet0/4        unassigned      YES manual down                  down 
FastEthernet0/5        unassigned      YES manual down                  down 
FastEthernet0/6        unassigned      YES manual up                    up 
FastEthernet0/7        unassigned      YES manual down                  down 
FastEthernet0/8        unassigned      YES manual down                  down 
FastEthernet0/9        unassigned      YES manual down                  down 
FastEthernet0/10       unassigned      YES manual down                  down 
FastEthernet0/11       unassigned      YES manual down                  down 
FastEthernet0/12       unassigned      YES manual down                  down 
FastEthernet0/13       unassigned      YES manual down                  down 
FastEthernet0/14       unassigned      YES manual down                  down 
FastEthernet0/15       unassigned      YES manual down                  down 
FastEthernet0/16       unassigned      YES manual down                  down 
FastEthernet0/17       unassigned      YES manual down                  down 
FastEthernet0/18       unassigned      YES manual down                  down 
FastEthernet0/19       unassigned      YES manual down                  down 
FastEthernet0/20       unassigned      YES manual down                  down 
FastEthernet0/21       unassigned      YES manual down                  down 
FastEthernet0/22       unassigned      YES manual down                  down 
FastEthernet0/23       unassigned      YES manual down                  down 
FastEthernet0/24       unassigned      YES manual down                  down 
GigabitEthernet0/1     unassigned      YES manual down                  down 
GigabitEthernet0/2     unassigned      YES manual down                  down 
Vlan1                  192.168.1.1     YES manual up                    up
```
*S2*
```
S2#show ip int brief
Interface              IP-Address      OK? Method Status                Protocol 
FastEthernet0/1        unassigned      YES manual up                    up 
FastEthernet0/2        unassigned      YES manual down                  down 
FastEthernet0/3        unassigned      YES manual down                  down 
FastEthernet0/4        unassigned      YES manual down                  down 
FastEthernet0/5        unassigned      YES manual down                  down 
FastEthernet0/6        unassigned      YES manual down                  down 
FastEthernet0/7        unassigned      YES manual down                  down 
FastEthernet0/8        unassigned      YES manual down                  down 
FastEthernet0/9        unassigned      YES manual down                  down 
FastEthernet0/10       unassigned      YES manual down                  down 
FastEthernet0/11       unassigned      YES manual down                  down 
FastEthernet0/12       unassigned      YES manual down                  down 
FastEthernet0/13       unassigned      YES manual down                  down 
FastEthernet0/14       unassigned      YES manual down                  down 
FastEthernet0/15       unassigned      YES manual down                  down 
FastEthernet0/16       unassigned      YES manual down                  down 
FastEthernet0/17       unassigned      YES manual down                  down 
FastEthernet0/18       unassigned      YES manual up                    up 
FastEthernet0/19       unassigned      YES manual down                  down 
FastEthernet0/20       unassigned      YES manual down                  down 
FastEthernet0/21       unassigned      YES manual down                  down 
FastEthernet0/22       unassigned      YES manual down                  down 
FastEthernet0/23       unassigned      YES manual down                  down 
FastEthernet0/24       unassigned      YES manual down                  down 
GigabitEthernet0/1     unassigned      YES manual down                  down 
GigabitEthernet0/2     unassigned      YES manual down                  down 
Vlan1                  192.168.1.2     YES manual up                    up
```
m. Close Configuration Window.<br>
n. Repeat the previous steps to configure switch S2. Make sure the hostname is configured as S2.<br>
o. Record the interface status for the following interfaces.
|Interface|S1 Status|S1 Protocol|S2 Status|S2 Protocol|
|:--------|:--------|:----------|:--------|:----------|
|F0/1|up|up|up|up|
|F0/6|up|up|down|down|
|F0/18|down|down|up|up|
|VLAN 1|up|up|up|up|

## Reflection Question
Why are some FastEthernet ports on the switches up while others are down?
```
Those that are up were enabled using the no shutdown command, while those that are down have not been enabled (yet).
```
What could prevent a ping from being sent between the PCs?
```
1. Misconfiguration of an IP address or subnet mask
2. If either PC is off
```
