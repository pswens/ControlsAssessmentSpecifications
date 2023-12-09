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

