CIS Control 1: Inventory and Control of Enterprise Assets
=======================================================

Actively manage (inventory, track, and correct) all enterprise assets
(end-user devices, including portable and mobile; network devices;
non-computing/Internet of Things (IoT) devices; and servers) connected
to the infrastructure, physically, virtually, remotely, and those within
cloud environments, to accurately know the totality of assets that need
to be monitored and protected within the enterprise. This will also
support identifying unauthorized and unmanaged assets to remove or
remediate.

### Why is this CIS Control Critical?

Enterprises cannot defend what they do not know they have. Managed
control of all enterprise assets also plays a critical role in security
monitoring, incident response, system backup, and recovery. Enterprises
should know what data is critical to them, and proper asset management
will help identify those enterprise assets that hold or manage this
critical data, so appropriate security controls can be applied.

External attackers are continuously scanning the internet address space
of target enterprises, premise-based or in the cloud, identifying
possibly unprotected assets attached to enterprises\' networks.
Attackers can take advantage of new assets that are installed, yet not
securely configured and patched. Internally, unidentified assets can
also have weak security configurations that can make them vulnerable to
web or email-based malware; and adversaries can leverage weak security
configurations for traversing the network, once they are inside.

Additional assets that connect to the enterprise's network (e.g.,
demonstration systems, temporary test systems, guest networks, etc.)
should be identified and/or isolated, in order to prevent adversarial
access from affecting the security of enterprise operations.

Large, complex, dynamic enterprises understandably struggle with the
challenge of managing intricate, fast-changing environments. However,
attackers have shown the ability, patience, and willingness to
"inventory and control" our enterprise assets at very large scale in
order to support their opportunities.

Another challenge is that portable end-user devices will periodically
join a network and then disappear, making the inventory of currently
available assets very dynamic. Likewise, cloud environments and virtual
machines can be difficult to track in asset inventories when they are
shut down or paused. Another benefit of complete enterprise asset
management is supporting incident response. Both when investigating the
origination of network traffic from an asset on the network, and to be
able to identify all potentially vulnerable, or impacted, assets of
similar type or location during an incident.

## 1.1: Establish and Maintain Detailed Enterprise Asset Inventory

Establish and maintain an accurate, detailed, and up-to-date inventory
of all enterprise assets with the potential to store or process data, to
include: end-user devices (including portable and mobile), network
devices, non-computing/IoT devices, and servers. Ensure the inventory
records the network address (if static), hardware address, machine name,
enterprise asset owner, department for each asset, and whether the asset
has been approved to connect to the network. For mobile end-user
devices, MDM type tools can support this process, where appropriate.
This inventory includes assets connected to the infrastructure
physically, virtually, remotely, and those within cloud environments.
Additionally, it includes assets that are regularly connected to the
enterprise's network infrastructure, even if they are not under control
of the enterprise. Review and update the inventory of all enterprise
assets bi-annually, or more frequently.

Asset Type | Security Function | Implementation Groups
------------ | ------------- | ------------
Devices | Identify | 1, 2, 3


# Dependencies

-   None

# Inputs

1.  `GV1`: Detailed Enterprise Asset Inventory - The enterprise\'s list
    of current approved inventory to include all assests as outlined in
    the safeguard. This list is a mix of manual and tool-generated
    endpoints that includes information such as authorized,
    non-authorized, IP address, device type and any other information as
    defined by the enterprise.
2.  Aggregate Enterprise Asset Inventory - The enterprise\'s list of all
    devices detected, manually or through automated scans, since the
    last update to `GV1`.
3.  Date of last update to the Detailed Enterprise Asset Inventory

## Assumptions

1.  Devices belonging to the organization, but not connected to the
    organization's network, require manual discovery in order to be
    included in the aggregate inventory.

# Operations

1.  

    Calculate the intersection of `GV1` and Input 2

    :   1.  Enumerate items in `GV1` that are not in Input 2 (M4)
        2.  Enumerate items in Input 2 not in Input 1 (`GV2`: M5). These
            assets are considered unauthorized.

2.  

    Check items in Input 1 for complete or missing detailed information

    :   1.  Enumerate items that have complete information (M6)
        2.  Enumerate items that do not have complete information or
            missing information (M7).

3.  Calculate the time (in months) since the last update to Input 1 by
    using current date and Input 4 (M8).

# Measures

-   M1 = `GV1`
-   M2 = Count of items in Input 2
-   M3 = Count of items in the intersection of `GV1` and Input 2
-   M4 = Count of items in `GV1` not found in Input 2
-   M5 = `GV2`
-   M6 = Count of items in `GV1` that contain all necessary detailed
    information
-   M7 = Count of items in `GV1` that do not contain detailed
    information
-   M8 = Months since the last update to `GV1`

# Metrics

-   If M1 is not provided or available, then this safeguard is measured
    at a 0 and receives a failing score. The other metrics don\'t apply.
-   If M8 is greater than six months, then this safeguard is measured at
    a 0 and receives a failing score. The other metrics don\'t apply.

## Accuracy Score

+-----------------+---------------------------------------------------+
| **Metric**      | | What percentage of the aggregate endpoint       |
|                 |   inventory is accounted for in the current       |
|                 |   enterprise asset inventory?                     |
+-----------------+---------------------------------------------------+
| **Calculation** | `M3 / M2`                                         |
+-----------------+---------------------------------------------------+

## Completeness Score

+-----------------+---------------------------------------------------+
| **Metric**      | | What percentage of the current enterprise asset |
|                 |   inventory contains necessary detailed           |
|                 |   information?                                    |
+-----------------+---------------------------------------------------+
| **Calculation** | `M8 / M1`                                         |
+-----------------+---------------------------------------------------+

## Procedural Review

Manual review/rating of the inventory procedures, to include adding and
removing assets, and the time allowable or expected, after acquisition
or disposal of assets.


