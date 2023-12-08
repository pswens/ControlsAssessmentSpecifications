1.4: Use Dynamic Host Configuration Protocol (DHCP) Logging to Update
Enterprise Asset Inventory 
====================================== 

Use DHCP logging on all DHCP servers or Internet Protocol (IP) address
management tools to update the enterprise's asset inventory. Review and
use logs to update the enterprise's asset inventory weekly, or more
frequently.

| Asset Type | Security Function | Implementation Groups |
|------------|-------------------|------------------------|
| Devices    | Identify          | 2, 3                   |

# Dependencies

-   Safeguard 1.1: Establish and Maintain Detailed Enterprise Asset
    Inventory

# Inputs

1.  List of DHCP servers
2.  `GV41`: List of CMDB servers

## Assumptions

1.  CMDB servers are configured to pull from DHCP logs

# Operations

-   For each DHCP server, enumerate those where DHCP logging is enabled
    (M2)
-   For each CMDB server, enumerate those where DHCP logs are used to
    update IP addresses (M4)

# Measures

-   M1 = Count of Input 1
-   M2 = Count of DHCP servers with logging enabled
-   M3 = Count of Input 2 `GV41`
-   M4 = Count of CMDB servers configured to use DHCP logs to update IP
    addresses
-   M5 = Count of devices in the DHCP server logs that are not included
    in the CMDB servers
-   M6 = Count of devices in the DHCP server logs that are included in
    the CMDB servers

# Metrics

-   M4 \> 0 indicates a non up-to-date asset inventory

## DHCP Logging Quality

| Metric       | Ratio of appropriately configured DHCP logging enabled to known DHCP servers |
|:-------------|:-----------------------------------------------------------------------------|
| Calculation  | `M2 / M1`                                                                   |

## CMDB Configuration Quality

| Metric          | Ratio of appropriately configured CMDB servers using DHCP logging to update IP addresses |
|:---------------:|:---------------------------------------------------------------------------------------------|
| Calculation     | `M4 / M3`                                                                                   |

