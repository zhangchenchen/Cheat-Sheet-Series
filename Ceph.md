**Table of Contents**  *generated with [DocToc](http://doctoc.herokuapp.com/)*

- [Ceph Cheat Sheet](#1)
    - [Authentication and Authorization](#2)
    - [Sevice Start](#3)
    - [Monitoring and Health](#4)
    - [Ceph OSD](#5)
    - [Ceph MON](#6)
    - [Placement Group](#7)
    - [Rados Object Storage](#8)
    - [RBD Block Storage](#9)

<a name="1"></a>
# Ceph Cheat Sheet

<a name="2"></a>
## Authentication and Authorization

```bash
ceph auth list                 # list all users
ceph auth get-or-create        # Get user details, or create the user if it doesn't exist yet and return details 
ceph auth delete               # Delete a user
ceph auth caps                 # Add or remove permissions for a user. Permissions are grouped per daemon type (eg. mon, osd, mds)            
```

<a name="3"></a>
## Sevice Start

```bash
service ceph start  mon.node1    # start monitor at node1
service ceph start mds.node1     # start mds at node1
service ceph start osd.0         # start osd0
service ceph start osd           # start all osd in current node
service ceph -a start osd        # start all osd in all nodes
```
<a name="4"></a>
## Monitoring and Health

```bash
ceph -s               # status summary
ceph -w               # watch ongoing status
ceph --watch-warn     # watch going, only WARN message
ceph df               # disk usage
ceph health detail    # details about health issues
ceph osd df tree      # disk usage linked to the CRUSH tree
```

<a name="5"></a>
## Ceph OSD

```bash
ceph osd tree                   # Dump the OSD map as a tree
ceph osd dump                   # Dump the OSD map
ceph osd find <osd-num>         # Display location of a given OSD (hostname, port, CRUSH details)
ceph osd pool ls                # List pools
ceph osd down <osd-num>         # Mark OSD down 
ceph osd up <osd-num>           # Mark OSD up
ceph osd out <osd-num>          # Take an OSD out of the cluster(still up), rebalancing it's data to other OSDs.
ceph osd in <osd-num>           # Reverse out
ceph osd reweight <osd-num> <weight>     # Permanently set weight instead of system-assigned value
ceph osd metadata <osd-num>              # Display OSD metadata (host and host info)
ceph osd map <pool-name> <object-name>   # Find out where a specific object is or would be stored in the system
```
<a name="6"></a>
## Ceph MON

```bash
ceph quorum_status        # Display mon quorum status
ceph mon dump             # Dump the MON map
ceph mon remove node1     # Remove a MON node
```



<a name="7"></a>
## Placement Group 

```bash
ceph pg dump                         # Display the statistics for all placement groups
ceph pg dump_stuck inactive|unclean|stale|undersized|degraded  # Display the statistics for all placement groups stuck in a specified state
```
<a name="8"></a>
## Rados Object Storage

```bash
rados -p <pool> ls                    # List all objects in specified pool
rados -p <pool> put <obj> <file>      # Upload a file into a pool, name the resulting obj
rados -p <pool> get <obj> <file>      # Download an object from a pool into a local file
rados -p <pool> rm <obj>              # Delete an object from a pool
```

<a name="9"></a>
## RBD Block Storage

```bash
rbd create <volume> --size              # Create a volume.
rbd map [--read-only] <volume-or-snap>  # Map a volume or snapshot to a block device on the local machine
rbd unmap <dev>                         # Unmap a mapped rbd device
rbd showmapped                          # Show mapped volumes / snapshots
rbd info <volume>                       # Print some metadata about a given volume.
rbd rm <volume>                         # Delete a volume
```
