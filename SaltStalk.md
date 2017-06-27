**Table of Contents**  

- [SaltStalk Cheat Sheet](#1)
    - [Minions Authentication](#2)
    - [Minions Management](#3)
        - [Minions Status](#4)
        - [Minion Packages](#5)
        - [Minion Services](#6)
        - [Minion Network](#7)
    - [Remote Control CLI](#8)
        - [Execute CMD/Script](#9)
        - [Copy File](#10)
    - [Grains in Salt](#11)
    - [Jobs in Salt](#12)
    - [Salt State](#13)

<a name="1"></a>
# SaltStalk Cheat Sheet
<a name="2"></a>
## Minions Authentication

```bash
salt-key  -L                  # list all public keys
salt-key  -a <PUB-KEY>        # accept the specified public key
salt-key  -A                  # accept all public key
salt-key  -d <PUB-KEY>        # delete the specified public key
salt-key  -D                  # delete all public key
```
<a name="3"></a>
## Minions Management
<a name="4"></a>
### Minions Status

```bash
salt-run manage.status  # What is the status of all my minions? (both up and down)
salt-run manage.up      # Any minions that are up?
salt-run manage.down    # Any minions that are down?
salt-run manage.alived  # Show all alive minions
salt '*' test.version   # Display salt version
salt '*' test.ping      # Use test module to check if minion is up and responding.
                        # (Not an ICMP ping!)
```
<a name="5"></a>
### Minion Packages

```bash
salt '*' pkg.list_upgrades             # get a list of packages that need to be upgrade
salt '*' pkg.upgrade                   # Upgrades all packages via apt-get dist-upgrade (or similar)

salt '*' pkg.version bash              # get current version of the bash package
salt '*' pkg.install bash              # install or upgrade bash package
salt '*' pkg.install bash refresh=True # install or upgrade bash package but
                                       # refresh the package database before installing.
``` 

<a name="6"></a>
### Minion Services

```bash
salt '*' service.status <service name>
salt '*' service.available <service name>
salt '*' service.start <service name>
salt '*' service.restart <service name>
salt '*' service.stop <service name>
```
<a name="7"></a>
### Minion Network

```bash
salt 'minion1' network.ip_addrs          # Get IP of your minion
salt 'minion1' network.ping <hostname>   # Ping a host from your minion
salt 'minion1' network.traceroute <hostname>   # Traceroute a host from your minion
salt 'minion1' network.get_hostname      # Get hostname
salt 'minion1' network.mod_hostname      # Modify hostname
```
<a name="8"></a>
## Remote Control CLI
<a name="9"></a>
### Execute CMD/Script

```bash
salt '*' cmd.run 'ls -l'               # the specified minion execute command
salt '*' cmd.script salt://test.sh     # upload the script to the specified minion then execute script

```
<a name="10"></a>
###  Copy File

```bash
salt-cp '*'  /etc/hosts   /etc/hosts   # copy  /etc/hosts from master to specified minion
```
<a name="11"></a>
## Grains in Salt

```bash
salt '*' grains.ls           # List all grains on all minions
salt '*' grains.item os      # Show the value of the OS grain for every minion
salt '*' grains.item roles   # Show the value of the roles grain for every minion
salt 'minion1' grains.setval mygrain True  # Set mygrain to True (create if it doesn't exist yet)
salt 'minion1' grains.delval mygrain       # Delete the value of the grain

```
<a name="12"></a>
## Jobs in Salt

```bash
salt-run jobs.active      # get list of active jobs
salt-run jobs.list_jobs   # get list of historic jobs
salt-run jobs.lookup_jid <job id number>  # get details of this specific job
```
<a name="13"></a>
## Salt State

```bash
salt '*' state.sls mystatefile       # mystatefile.sls will be applied to *
salt 'node1.com' state.highstate     # all sls will be applied to node1.com
```

