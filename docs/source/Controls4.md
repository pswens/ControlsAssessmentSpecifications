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

## Dependencies

- Safeguard 2.1: Establish and Maintain a Software Inventory

## Inputs

1. `GV2`: Authorized software inventory
2. `GV1`: Enterprise asset inventory
3. `GV3`: Configuration Standard: This should include any enterprise-approved deviations from industry-standard baselines such as CIS benchmarks, DISA Security Technical Implementation Guides (STIGs), or U.S. government configuration baselines (USGCB).
4. Date of last review and update of configuration standard

## Operations

1. Identify whether Input 2 exists:

   1. If it exists, M1 = 1
   2. If it does not exist, M1 = 0

2. Identify and enumerate end-user devices, including portable and mobile, non-computing/IoT devices and servers in `GV1` (M2).

3. Using the output of Operation 2 (M2), identify and enumerate the software installed on the assets using `GV2` (M3)

4. For each software identified in Operation 3 (M3):

   1. Enumerate software that is listed in the configuration standard `GV3` (M4)
   2. Enumerate software that is not listed in the configuration standard `GV3` (M5)

5. Compare the current date to the date provided in Input 4. Note the timeframe in months (M6)

## Measures

-   M1 = Output of Operation 1
-   M2 = Count of applicable enterprise assets
-   M3 = Count of software installed on applicable enterprise assets
-   M4 = Count of software that is listed in the configuration standard
-   M5 = Count of software that is not listed in the configuration
    standard
-   M6 = Timeframe since last review and update in months

## Metrics

- If M1 is 0, this safeguard receives a failing score. The other metrics don't apply.
- If M6 is greater than twelve, this safeguard is measured at 0 and receives a failing score. The other metrics don't apply.

## Standard Configuration Coverage

| **Metric**      | The percentage of authorized software with secure configuration standards documented and maintained. |
|:---------------:|:--------------------------------------------------------------------------------------------------:|
| **Calculation** | `M4 / M3`                                                                                        |


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
-------------------------------------------------------------------------
-------------------------------------------------------------------------
-------------------------------------------------------------------------
-------------------------------------------------------------------------
