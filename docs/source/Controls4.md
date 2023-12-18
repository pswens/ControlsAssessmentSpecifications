# CIS Control 4: Secure Configuration of Enterprise Assets and Software

Establish and maintain the secure configuration of enterprise assets (end-user devices, including portable and mobile, network devices, non-computing/IoT devices, and servers) and software (operating systems and applications).

**Why is this CIS Control Critical?**

As delivered by manufacturers and resellers, the default configurations for enterprise assets and software are normally geared towards ease of deployment and ease of use rather than security. Basic controls, open services and ports, default accounts or passwords, pre-configured Domain Name System (DNS) settings, older (vulnerable) protocols, and pre-installation of unnecessary software can all be exploitable if left in their default state. Further, these security configuration updates need to be managed and maintained over the life cycle of enterprise assets and software. Configuration updates need to be tracked and approved through the configuration management workflow process to maintain a record that can be reviewed for compliance, leveraged for incident response, and support audits. This CIS Control is important to on-premises devices, as well as remote devices, network devices, and cloud environments.

Service providers play a key role in modern infrastructures, especially for smaller enterprises. They often are not set up by default in the most secure configuration to provide flexibility for their customers to apply their own security policies. Therefore, the presence of default accounts or passwords, excessive access, or unnecessary services are common in default configurations. These could introduce weaknesses that are under the responsibility of the enterprise that is using the software rather than the service provider. This extends to ongoing management and updates, as some Platform as a Service (PaaS) only extend to the operating system, so patching and updating hosted applications are under the responsibility of the enterprise.

Even after a strong initial configuration is developed and applied, it must be continually managed to avoid degrading security as software is updated or patched, new security vulnerabilities are reported, and configurations are “tweaked” to allow the installation of new software or to support new operational requirements.

-------------------------------------------------------------------------
## 4.1: Establish and Maintain a Secure Configuration Process

Establish and maintain a secure configuration process for enterprise assets (end-user devices, including portable and mobile, non-computing/IoT devices, and servers) and software (operating systems and applications). Review and update documentation annually or when significant enterprise changes occur that could impact this Safeguard.

| Asset Type | Security Function | Implementation Groups |
|------------|-------------------|-----------------------|
| Applications | Protect | 1, 2, 3 |

### Dependencies

- Safeguard 2.1: Establish and Maintain a Software Inventory

### Inputs

1. `GV2`: Authorized software inventory
2. `GV1`: Enterprise asset inventory
3. `GV3`: Configuration Standard: This should include any enterprise-approved deviations from industry-standard baselines such as CIS benchmarks, DISA Security Technical Implementation Guides (STIGs), or U.S. government configuration baselines (USGCB).
4. Date of last review and update of configuration standard

### Operations

1. Identify whether Input 2 exists:

    1. If it exists, M1 = 1
    2. If it does not exist, M1 = 0

2. Identify and enumerate end-user devices, including portable and mobile, non-computing/IoT devices, and servers in `GV1` (M2)

3. Using the output of Operation 2 (M2), identify and enumerate the software installed on the assets using `GV2` (M3)

4. For each software identified in Operation 3 (M3):

    1. Enumerate software that is listed in the configuration standard `GV3` (M4)
    2. Enumerate software that is not listed in the configuration standard `GV3` (M5)

5. Compare the current date to the date provided in Input 4. Note the timeframe in months (M6)

### Measures

-   M1 = Output of Operation 1
-   M2 = Count of applicable enterprise assets
-   M3 = Count of software installed on applicable enterprise assets
-   M4 = Count of software that is listed in the configuration standard
-   M5 = Count of software that is not listed in the configuration
    standard
-   M6 = Timeframe since last review and update in months

### Metrics

- If M1 is 0, this safeguard receives a failing score. The other metrics don't apply.
- If M6 is greater than twelve, this safeguard is measured at 0 and receives a failing score. The other metrics don't apply.

#### Standard Configuration Coverage

| **Metric**      | The percentage of authorized software with secure configuration standards documented and maintained. |
|-----------------|----------------------------------------------------------------------------------------------------|
| **Calculation** | `M4 / M3`                                                                                          |

-------------------------------------------------------------------------

## 4.2: Establish and Maintain a Secure Configuration Process for Network Infrastructure

Establish and maintain a secure configuration process for network devices. Review and update documentation annually, or when significant enterprise changes occur that could impact this Safeguard.

| Asset Type | Security Function | Implementation Groups |
|------------|-------------------|-----------------------|
| Network | Protect | 1, 2, 3 |

### Dependencies

- Safeguard 2.1: Establish and Maintain a Software Inventory

### Inputs

1. `GV2`: Authorized software inventory
2. `GV1`: Enterprise asset inventory
3. `GV3`: Configuration Standard: This should include any enterprise approved deviations from industry standard baselines such as CIS benchmarks, DISA Security Technical Implementation Guides (STIGs), or U.S. government configuration baselines (USGCB).
4. Date of last review and update of the configuration standard

### Operations

1. Identify whether Input 2 exists:

    1. If it exists, M1 = 1
    2. If it does not exist, M1 = 0

2. Identify and enumerate network infrastructure assets in `GV1` (M2)

3. Using the output of Operation 2 (M2), identify and enumerate the software installed on the assets using `GV2` (M3)

4. For each software identified in Operation 3 (M3):

    1. Enumerate software that is listed in the configuration standard `GV3` (M4)
    2. Enumerate software that is not listed in the configuration standard `GV3` (M5)

5. Compare the current date to the date provided in Input 4. Note the timeframe in months (M6)

### Measures

-   M1 = Output of Operation 1
-   M2 = Count of applicable enterprise assets
-   M3 = Count of software installed on applicable enterprise assets
-   M4 = Count of software that is listed in the configuration standard
-   M5 = Count of software that is not listed in the configuration
    standard
-   M6 = Timeframe since last review and update in months

### Metrics

- If M1 is 0, this safeguard receives a failing score. The other metrics don't apply.
- If M6 is greater than twelve, this safeguard is measured at 0 and receives a failing score. The other metrics don't apply.

#### Standard Configuration Coverage

| **Metric**      | The percentage of authorized software with secure configuration standards documented and maintained. |
|-----------------|----------------------------------------------------------------------------------------------------|
| **Calculation** | `M4 / M3`                                                                                          |

-------------------------------------------------------------------------

## 4.3: Configure Automatic Session Locking on Enterprise Assets

Configure automatic session locking on enterprise assets after a defined period of inactivity. For general-purpose operating systems, the period must not exceed 15 minutes. For mobile end-user devices, the period must not exceed 2 minutes.

| Asset Type | Security Function | Implementation Groups |
|------------|-------------------|-----------------------|
| Users | Protect | 1, 2, 3 |

### Dependencies

- Safeguard 1.1: Establish and Maintain Detailed Enterprise Asset Inventory
- Safeguard 2.1: Establish and Maintain a Software Inventory
- Safeguard 4.1: Establish and Maintain a Secure Configuration Process

### Inputs

1. `GV1`: Enterprise asset inventory
2. `GV5`: Authorized Software Inventory
3. `GV3`: Configuration standard

### Operations

1. Identify and enumerate assets within `GV1` that support automatic locking due to inactivity (M1)

2. Use `GV5` to identify and enumerate assets from Operation 1 with authorized software installed (M2)

3. Check the configurations for the software using `GV3`:

    1. For general computing assets, enumerate those assets with properly configured automatic locking (15 minutes or less) (M3)
    2. For general computing assets, enumerate those assets with improperly configured automatic locking (greater than 15 minutes) (M4)
    3. For mobile assets, enumerate those assets with properly configured automatic locking (2 minutes or less) (M5)
    4. For mobile assets, enumerate those assets with improperly configured automatic locking (greater than 2 minutes) (M6)

### Measures

- M1 = Count of assets capable of supporting automatic lockout
- M2 = Count of assets with authorized software installed to allow a lockout
- M3 = Count of general computing assets with properly configured lockout
- M4 = Count of general computing assets with improperly configured lockout
- M5 = Count of mobile assets with properly configured lockout
- M6 = Count of mobile assets with improperly configured lockout

### Metrics

#### Properly Configured Assets

| **Metric**      | The percentage of assets properly configured for automatic lockout. |
|-----------------|---------------------------------------------------------------|
| **Calculation** | `(M3 + M5) / M1`                                              |

-------------------------------------------------------------------------

## 4.4: Implement and Manage a Firewall on Servers

Implement and manage a firewall on servers where supported. Example implementations include a virtual firewall, an operating system firewall, or a third-party firewall agent.

| Asset Type | Security Function | Implementation Groups |
|------------|-------------------|-----------------------|
| Devices    | Protect           | 1, 2, 3               |

### Dependencies

- Safeguard 1.1: Establish and Maintain Detailed Enterprise Asset Inventory
- Safeguard 2.1: Establish and Maintain a Software Inventory
- Safeguard 4.1: Establish and Maintain a Secure Configuration Process

### Inputs

1. `GV1`: Enterprise asset inventory
2. `GV5`: Authorized software inventory
3. `GV3`: Configuration standard

### Operations

1. Identify and enumerate servers capable of hosting a firewall using `GV1` (M1)

2. Identify and enumerate applications capable of hosting a firewall using `GV5` (M2)

3. Using configuration standards to check if firewalls are properly configured:

    1. Enumerate servers from Operation 1 with properly configured firewalls (M3)
    2. Enumerate servers from Operation 1 with improperly configured firewalls (M4)
    3. Enumerate applications from Operation 2 with properly configured firewalls (M3)
    4. Enumerate applications from Operation 2 with improperly configured firewalls (M4)

### Measures

- M1 = Count of servers enterprise assets capable of hosting a firewall
- M2 = Count of applications software capable of hosting a firewall
- M3 = Count of servers with properly configured firewalls
- M4 = Count of servers with improperly configured firewalls
- M5 = Count of applications with properly configured firewalls
- M6 = Count of applications with improperly configured firewalls

### Metrics

#### Implementation of Firewalls

| **Metric**      | The percentage of properly configured firewalls within the enterprise |
|-----------------|-----------------------------------------------------------------------|
| **Calculation** | `(M3 + M5) / (M1 + M2)`                                              |

-------------------------------------------------------------------------

## 4.5: Implement and Manage a Firewall on End-User Devices

Implement and manage a host-based firewall or port-filtering tool on end-user devices with a default-deny rule that drops all traffic except those services and ports that are explicitly allowed.

| Asset Type | Security Function | Implementation Groups |
|------------|-------------------|-----------------------|
| Devices    | Protect           | 1, 2, 3               |

### Dependencies

- Safeguard 1.1: Establish and Maintain Detailed Enterprise Asset Inventory
- Safeguard 2.1: Establish and Maintain a Software Inventory
- Safeguard 4.1: Establish and Maintain a Secure Configuration Process

### Inputs

1. `GV1`: Enterprise asset inventory
2. `GV5`: Authorized software inventory
3. `GV3`: Configuration standard

### Operations

1. Identify and enumerate end-user devices capable of hosting a firewall or a deny rule using `GV1` (M1)

2. Using configuration standards `GV3` to check if firewalls or deny rules are properly configured on end-user devices:

    1. Enumerate assets from Operation 1 with properly configured firewalls or a configured default deny rule (M3)
    2. Enumerate assets from Operation 1 with improperly configured firewalls and lacking a configured default deny rule (M4)
M4)

### Measures

- M1 = Count of end-user devices capable of hosting a firewall
- M2 = Count of end-user devices with a properly configured firewall or default deny rule
- M3 = Count of end-user devices with an improperly configured firewall and lacking a configured default deny rule

### Metrics

#### Coverage

| **Metric**      | The percentage of properly configured firewalls or deny rule on end-user devices |
|-----------------|-------------------------------------------------------------------------------|
| **Calculation** | `M2 / M1`                                                                     |

-------------------------------------------------------------------------
-------------------------------------------------------------------------
-------------------------------------------------------------------------
-------------------------------------------------------------------------
-------------------------------------------------------------------------
-------------------------------------------------------------------------
-------------------------------------------------------------------------
-------------------------------------------------------------------------
-------------------------------------------------------------------------
-------------------------------------------------------------------------
