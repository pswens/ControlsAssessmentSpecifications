# CIS Control 11: Data Recovery

Establish and maintain data recovery practices sufficient to restore
in-scope enterprise assets to a pre-incident and trusted state.

**Why is this CIS Control Critical?**

In the cybersecurity triad -- Confidentiality, Integrity, and
Availability (CIA) -- the availability of data is, in some cases, more
critical than its confidentiality. Enterprises need many types of data
to make business decisions, and when that data is not available or is
untrusted, then it could impact the enterprise. An easy example is
weather information to a transportation enterprise.

When attackers compromise assets, they make changes to configurations,
add accounts, and often add software or scripts. These changes are not
always easy to identify, as attackers might have corrupted or replaced
trusted applications with malicious versions, or the changes might
appear to be standard-looking account names. Configuration changes can
include adding or changing registry entries, opening ports, turning off
security services, deleting logs, or other malicious actions that make a
system insecure. These actions do not have to be malicious; human error
can cause each of these as well. Therefore, it is important to have an
ability to have recent backups or mirrors to recover enterprise assets
and data back to a known trusted state.

There has been an exponential rise in ransomware over the last few
years. It is not a new threat, though it has become more commercialized
and organized as a reliable method for attackers to make money. If an
attacker encrypts an enterprise's data and demands ransom for its
restoration, having a recent backup to recover to a known, trusted state
can be helpful. However, as ransomware has evolved, it has also become
an extortion technique, where data is exfiltrated before being
encrypted, and the attacker asks for payment to restore the enterprise's
data, as well as to keep it from being sold or publicized. In this case,
restoration would only solve the issue of restoring systems to a trusted
state and continuing operations. Leveraging the guidance within the CIS
Controls will help reduce the risk of ransomware through improved cyber
hygiene, as attackers usually use older or basic exploits on insecure
systems.

--------------------------------------------------------------------------

## 11.1: Establish and Maintain a Data Recovery Process 

Establish and maintain a data recovery process. In the process, address
the scope of data recovery activities, recovery prioritization, and the
security of backup data. Review and update documentation annually, or
when significant enterprise changes occur, that could impact this
Safeguard.

| Asset Type   | Security Function   | Implementation Groups |
| ------------ | ------------------- | --------------------- |
| Data         | Recover             | 1, 2, 3               |

### Dependencies

-   None

### Inputs

1.  Data recovery process for the enterprise
2.  Date of last update to the data recovery process

### Operations

1. Check if the enterprise has a data recovery process Input 1

    1.  If so, M1 = 1
    2.  2.  If not, M1 = 0

2. Examine the enterprise\'s data recovery process and determine if it addresses, at a minimum, the scope of data recovery activities, recovery prioritization, and the security of backup data

    1.  For each element included within the process, assign the element a value of 1. M2 = sum of all the values.

3.  Compare the date of the last update to the data recovery process to the curren date and capture the timeframe in months (M3)

### Measures

-   M1 = Output of Operation 1
-   M2 = Sum of elements included in the data recovery process
-   M3 = Timeframe in months of the last update to the data recovery process

### Metrics

If M1 is 0, the safeguard receives a failing score. The other metrics
don\'t apply. If M3 is greater than twelve, this safeguard is measured
at a 0 and receives a failing score. The other metrics don\'t apply.

#### Completeness 

| **Metric**      | The percentage of elements included in the data recovery process |
|-----------------|---------------------------------------------------------------|
| **Calculation** | `M2 / M3`                                              |

--------------------------------------------------------------------------
--------------------------------------------------------------------------
--------------------------------------------------------------------------
--------------------------------------------------------------------------
--------------------------------------------------------------------------
