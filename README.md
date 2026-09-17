 ## Basic Switch Configuration

## Objective

Configure a Cisco switch with basic settings using the Cisco IOS command-line interface (CLI).

The lab focuses on :

* Accessing the switch CLI
* Understanding Cisco IOS modes
* Setting a device hostname
* Configuring a Message of the Day (MOTD) banner
* Setting an enable secret password
* Checking the active configuration


## Scenario

A new Cisco switch has been added to a small network.

Before using the switch, a network administrator needs to apply some basic configuration so the device can be identified and protected from unauthorized access.

In this lab, the switch is named `SW1_lab1` and configured with a basic security warning and privileged-mode password.


## Topology

text

PC1
 |
 |
SW1


PC1 is connected to `SW1_lab1` using an Ethernet cable.


## Devices Used

| Device | Model      | Name |
| ------ | ---------- | ---- |
| Switch | Cisco 2960 | SW1  |
| PC     | Generic PC | PC1  |


## Configuration

The switch was configured with the following settings:

| Setting       | Value                  |
| ------------- | ---------------------- |
| Hostname      | SW1_lab1               |
| MOTD Banner   | AUTHORIZED ACCESS ONLY |
| Enable Secret | Configured             |

Configuration commands:

bash

enable
configure terminal

hostname SW1_lab1

banner motd #AUTHORIZED ACCESS ONLY#

enable secret class123

end

> `class123` is used only for this lab. A real network should use a strong password that follows the organization's security policy.


## Commands Used

### Enter Privileged EXEC Mode

```bash
enable
```

Changes from User EXEC mode to Privileged EXEC mode.

```text
SW1_lab1>
```

becomes:

```text
SW1_lab1#
```

### Enter Global Configuration Mode

```bash
configure terminal
```

Short form:

```bash
conf t
```

### Set the Hostname

```bash
hostname SW1_lab1
```

### Configure the MOTD Banner

```bash
banner motd #AUTHORIZED ACCESS ONLY#
```

### Configure the Enable Secret

```bash
enable secret class123
```

### Return to Privileged EXEC Mode

```bash
end
```

### Display the Current Configuration

```bash
show running-config
```

---

## Verification

The configuration was checked using:

```bash
show running-config
```

The output should contain the configured hostname, MOTD banner, and enable secret.

The enable password was also tested by leaving Privileged EXEC mode and entering it again:

```bash
disable
enable
```

The switch should request the configured password before returning to:

```text
SW1_lab1#
```

---

## Expected Result

After completing the lab:

* The switch hostname should be `SW1_lab1`.
* The MOTD banner should display `AUTHORIZED ACCESS ONLY`.
* The enable secret should be configured.
* `show running-config` should display the active configuration.
* The switch should request the enable password when entering Privileged EXEC mode.

---

## Troubleshooting

### Hostname did not change

Check that the command was entered from Global Configuration Mode:

```bash
configure terminal
hostname SW1
```

### Password is not working

Check that the password was configured correctly:

```bash
show running-config
```

Then test:

```bash
disable
enable
```

### Configuration commands are not accepted

Check the current IOS mode.

```text
SW1_lab1>
```

User EXEC Mode

```text
SW1_lab1#
```

Privileged EXEC Mode

```text
SW1_lab1(config)#
```

Global Configuration Mode

Use the correct command for the current mode.

---

## What Learned

This lab introduced the basic Cisco IOS configuration workflow.

I learned how to:

* Navigate between Cisco IOS modes
* Configure a switch hostname
* Add an access warning using an MOTD banner
* Configure an enable secret
* Check the current running configuration
* Verify that a configuration is working as expected

I also learned that Cisco IOS configuration is performed through different command modes, and the available commands depend on the current mode.

---

## Real-World Application

Basic switch configuration is normally performed when a new network device is installed or when an existing device needs to be prepared for use.

In a real network, administrators may configure:

* Device names
* Management access
* Authentication
* Security settings
* Interface settings
* VLANs
* Remote access such as SSH
* Monitoring and logging

A clear hostname and proper access controls also make network administration and troubleshooting easier, especially when many devices are involved.

---
 
