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
