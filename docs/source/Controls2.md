# CIS Control 2: Inventory and Control of Software Assets

Actively manage (inventory, track, and correct) all software (operating
systems and applications) on the network so that only authorized
software is installed and can execute, and that unauthorized and
unmanaged software is found and prevented from installation or
execution.

**Why is this CIS Control Critical?**

A complete software inventory is a critical foundation for preventing
attacks. Attackers continuously scan target enterprises looking for
vulnerable versions of software that can be remotely exploited. For
example, if a user opens a malicious website or attachment with a
vulnerable browser, an attacker can often install backdoor programs and
bots that give the attacker long-term control of the system. Attackers
can also use this access to move laterally through the network. One of
the key defenses against these attacks is updating and patching
software. However, without a complete inventory of software assets, an
enterprise cannot determine if they have vulnerable software, or if
there are potential licensing violations.

Even if a patch is not yet available, a complete software inventory list
allows an enterprise to guard against known attacks until the patch is
released. Some sophisticated attackers use "zero-day exploits", which
take advantage of previously unknown vulnerabilities that have yet to
have a patch released by the software vendor. Depending on the severity
of the exploit, an enterprise can implement temporary mitigation
measures to guard against attacks until the patch is released.

Management of software assets is also important to identify unnecessary
security risks. An enterprise should review their software inventory to
identify any enterprise assets running software that is not needed for
business purposes. For example, an enterprise asset may come installed
with default software that creates a potential security risk and
provides no benefit to the enterprise. It is critical to inventory,
understand, assess, and manage all software connected to an enterprise's
infrastructure.

-------------------------------------------------------------------------

## 2.1: Establish and Maintain a Software Inventory

Establish and maintain a detailed inventory of all licensed software installed on enterprise assets. The software inventory must document the title, publisher, initial install/use date, and business purpose for each entry; where appropriate, include the Uniform Resource Locator (URL), app store(s), version(s), deployment mechanism, and decommission date. Review and update the software inventory bi-annually, or more frequently.

| Asset Type   | Security Function | Implementation Groups |
|--------------|-------------------|------------------------|
| Applications | Identify          | 1, 2, 3                |

### Dependencies

-   None

### Inputs

1.  `GV5`: The authorized software inventory with detailed information
    including: timestamp indicating both last updated and last verified
    values, timestamp indicating installation date, operating system,
    software name, software version, software publisher, authorization
    status, business purpose, supported/unsupported. Where applicable,
    additionally include URL, app store(s), deployment mechanism, and
    decommission date.
2.  `GV6`: The date of the last update to the authorized software
    inventory.

### Operations

1. Check `GV5` for completeness of detailed information.
    1. Note items that have complete detailed information (M2).
    2. Note items that have missing or incomplete information (M3).

2.  Compare the current date to `GV6` and note timeframe in months (M4).

### Measures

-   M1 = Count of `GV5`
-   M2 = Count of items in `GV5` with complete information
-   M3 = Count of items in `GV5` with incomplete or missing information
-   M4 = Timeframe in months since last update `GV6`

### Metrics

-   If M1 is not provided or available, then this safeguard is measured
    at a 0 and receives a failing score. The other metrics don\'t apply.
-   If M4 is greater than six months, then this safeguard is measured at
    a 0 and receives a failing score. The other metrics don\'t apply.

#### Accuracy Score

| **Metric**      | What percentage of the current enterprise asset inventory contains necessary detailed information? |
|:---------------:|-------------------------------------------------------------------------------------------------------------|
| **Calculation** | `M2 / M1`                                                                                                 |

-------------------------------------------------------------------------

##2.2: Ensure Authorized Software is Currently Supported

Ensure that only currently supported software is designated as authorized in the software inventory for enterprise assets. If software is unsupported yet necessary for the fulfillment of the enterprise's mission, document an exception detailing mitigating controls and residual risk acceptance. For any unsupported software without an exception documentation, designate as unauthorized. Review the software list to verify software support at least monthly, or
more frequently.

| Asset Type   | Security Function | Implementation Groups |
|--------------|-------------------|------------------------|
| Applications | Identify          | 1, 2, 3                |

### Dependencies

-   Safeguard 2.1: Establish and Maintain a Software Inventory

### Inputs

1.  `GV5`: The authorized software inventory with detailed information.
    deployment mechanism, and decommission date.
2.  Authoritative source of information indicating supported/unsupported
    details by product.
3.  Exception documentation for unsupported software that is necessary
    for the fulfillment of the enterprise's mission.
4.  `GV6`: Date of last update to the authorized software inventory

### Assumptions

1. Authorized software inventory with detailed information exists for the enterprise.

### Operations

1. For each item in `GV5`, perform a lookup in Input 2 to verify supported/unsupported status.
    1. Enumerate each item labeled "unsupported" but "supported" based on Input 2 (M2)
    2. Enumerate each item labeled "supported" but is "unsupported" based on Input 2 (M3).

2. Identify and note truly "unsupported" items from Input 1 after conducting Operation 1 (M4).

3. For each unsupported item identified in Operation 2, conduct a check using Input 3.
    1. Note items that do not have appropriate exception documentation (M5).
    2. Note items that do have appropriate exception documentation (M6).

4.  Compare date of `GV6` to the current date and note timeframe in
    weeks (M7).

### Measures

-   M1 = Count of Input 1
-   M2 = Count of items in Input 1 that are mislabeled as unsupported
-   M3 = Count of items in Input 1 that are mislabeled as supported
-   M4 = Count of unsupported items
-   M5 = Count of items in Input 1 with that are no longer supported but
    exception documentation exists
-   M6 = Count of items in Input 1 with that are no longer supported and
    exception documentation does not exist
-   M7 = Timeframe in weeks of last update to the authorized software
    inventory

### Metrics

-   If M7 is greater than four, then this safeguard is measured at a 0
    and receives a failing score. The other metrics don\'t apply.

#### Percentage of Unsupported Software in Use

| **Metric**      | What percentage of authorized software inventory in use is unsupported? |
|:---------------:|-------------------------------------------------------------------------|
| **Calculation** | `M4 / M1`                                                               |


#### Rate of False Positives

| **Metric**      | What percentage of software listed as supported is actually not supported? |
|:---------------:|-----------------------------------------------------------------------------|
| **Calculation** | `M3 / M1`                                                                   |

#### Rate of False Negatives

| **Metric**      | What percentage of software listed as unsupported is actually supported? |
|:---------------:|-------------------------------------------------------------------------|
| **Calculation** | `M2 / M1`                                                               |


#### Percentage of unsupported software with exception documentation

| **Metric**      | What percentage of software listed as unsupported but appropriate exception documentation exists? |
|:---------------:|-----------------------------------------------------------------------------------------------------------|
| **Calculation** | `M5 / M4`                                                                                                 |

--------------------------------------------------------------------------

## 2.3: Address Unauthorized Software

Ensure that unauthorized software is either removed from use on
enterprise assets or receives a documented exception. Review monthly, or
more frequently..

  Asset Type     Security Function   Implementation Groups
  -------------- ------------------- -----------------------
  Applications   Respond             1, 2, 3

### Dependencies

-   Safeguard 1.1: Establish and Maintain Detailed Enterprise Asset
    Inventory
-   Safeguard 2.1: Establish and Maintain a Software Inventory

### Inputs

1.  `GV5`: Authorized software inventory
2.  `GV1`: Enterprise asset Invetory
3.  Enterprise defined timeframe for scanning of enterprise assets.
4.  Enterprise defined allowable timeframe for resolution of discovered
    unauthorized software (recommend at least monthly)

### Assumptions

1. The scanning schedule timeframe is greater than the enterprise defined allowable timeframe for resolution of discovered unauthorized software.

### Operations

1. Identify the software capable enterprise
assets in `GV1` (`GV7`)
2. Scan the assets identified in Operation 1 and
note software present on each asset (M1)
3. Compare the scan results to
the authorized software list in `GV5`
    1. Enumerate unauthorized software identified on assets (M2)
4. Conduct subsquent scan of assets identified in Operation 1 as dictated by timeframe in Input 3
    1. Compare to list generated in Operation 3 (M2) 
5. For each software still present in Operation 4, check the authorized software list in `GV5`
    1. Software that remains installed and is not listed in `GV5` is placed on the unaddressed software list (M3) for that asset.

### Measures

-   M1 = The count of software installed on a given asset
-   M2 = The count of unauthorized software installed on a given asset
-   M3 = The count of unaddressed software installed on a given asset,
    identified by follow-up scan.
-   M4 = Timeframe for resolution of discovered unauthorized software in
    weeks

### Metrics

-   If M4 is greater than four weeks, then this safeguard is measured at
    a 0 and receives a failing score. The other metrics don't apply.

#### Unauthorized software Per Asset

| **Metric**      | Ensure unauthorized software installations are addressed                                        |
|:---------------:|------------------------------------------------------------------------------------------------------|
| **Calculation** | `(M2-M3) / M3`                                                                                |


#### Unauthorized software for the enterprise

- The enterprise metric is calculated through averaging the results calculated above perasset.
