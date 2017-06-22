# Ceph Cheat Sheet

## Authentication and Authorization

```bash
ceph auth list                 # list all users
ceph auth get-or-create        # Get user details, or create the user if it doesn't exist yet and return details 
ceph auth delete               # Delete a user
ceph auth caps                 # Add or remove permissions for a user. Permissions are grouped per daemon type (eg. mon, osd, mds)            
```

## Sevice Start

```bash
service ceph start  mon.node1    # start monitor at node1
service ceph start mds.node1     # start mds at node1
service ceph start osd.0         # start osd0
service ceph start osd           # start all osd in current node
service ceph -a start osd        # start all osd in all nodes
```

## Monitoring and Health

```bash
ceph -s               # status summary
ceph -w               # watch ongoing status
ceph --watch-warn     # watch going, only WARN message
ceph df               # disk usage
ceph health detail    # details about health issues
ceph osd df tree      # disk usage linked to the CRUSH tree
```


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

## Ceph MON

```bash

``` 



## Salt State

```bash

```