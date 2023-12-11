# CIS Control 3: Data Protection

Develop processes and technical controls to identify, classify, securely
handle, retain, and dispose of data.

**Why is this CIS Control Critical?**

Data is no longer only contained within an enterprise's border, it is in
the cloud, on portable end-user devices where users work from home, and
is often shared with partners or online services who might have it
anywhere in the world. In addition to sensitive data an enterprise holds
related to finances, intellectual property, and customer data, there
also might be numerous international regulations for the protection of
personal data. Data privacy has become increasingly important, and
enterprises are learning that privacy is about the appropriate use and
management of data, not just encryption. Data must be appropriately
managed through its entire lifecycle. These privacy rules can be
complicated for multi-national enterprises of any size. However, there
are fundamentals that can apply to all.

Once attackers have penetrated an enterprise's infrastructure, one of
their first tasks is to find and exfiltrate data. Enterprises might not
be aware that sensitive data is leaving their environment because they
are not monitoring data outflows.

While many attacks occur on the network, others involve physical theft
of portable end-user devices, attacks on service providers, or other
partners holding sensitive data. Other sensitive enterprise assets may
also include non-computing devices that provide management and control
of physical systems, such as Supervisory Control and Data Acquisition
(SCADA) systems.

The enterprise's loss of control over protected or sensitive data is a
serious and often reportable business impact. While some data is
compromised or lost as a result of theft or espionage, the vast majority
are a result of poorly understood data management rules and user error.
The adoption of data encryption, both in transit and at rest, can
provide mitigation against data compromise and, more importantly, is a
regulatory requirement for most controlled data.

-------------------------------------------------------------------------

## 3.1: Establish and Maintain a Data Management Process

Establish and maintain a data management process. In the process, address data sensitivity, data owner, handling of data, data retention limits, and disposal requirements based on sensitivity and retention standards for the enterprise. Review and update documentation annually, or when significant enterprise changes occur, that could impact this Safeguard.

| Asset Type   | Security Function | Implementation Groups |
|--------------|-------------------|------------------------|
| Applications | Identify          | 1, 2, 3                |

### Dependencies

-   None

### Inputs

1.  `GV10`: Enterprise\'s data management process
2.  Date of last update to the data management process

### Operations

1. Review `GV10` to determine if, at a minimum, it includes:
   
  1. Addressing data sensitivity. If so, M1 = 1. Otherwise M1 = 0. (`GV11`)
  2. Captures data owner. If so, M2 = 1. Otherwise M2 = 0. (`GV13`)
  3. Handling of data. If so, M3 = 1. Otherwise, M3 = 0. (`GV14`)
  4. Data retention limits based on the sensitivity of data. If so, M4 = 1. Otherwise, M4 = 0. (`GV15`)
  5. Disposal requirements based on the sensitivity of data. If so, M5 = 1. Otherwise, M5 = 0. (`GV16`)

### Measures

-   M1 = Does the process address data sensitivity
-   M2 = Does the process capture data owners
-   M3 = Does the process include guidance for handling of data
-   M4 = Does the process include data retention limits based on
    sensitivity of data
-   M5 = Does the process include guidance on disposal requirements
    based on the sensitivity of data
-   M6 = `GV10`

### Metrics

-   If M6 is not available or does not exist, this safeguard is measured
    at a 0 and receives a failing score. The other metrics don\'t apply.

#### Completeness of Data Management Process

| **Metric**      | The percentage of completeness for the enterprise's data management process.                  |
| :-------------- | :----------------------------------------------------------------------------------------------- |
| **Calculation** | `(M1 + M2 + M3 + M4 + M5) / 5`                                                           |

-------------------------------------------------------------------------

## 3.2: Establish and Maintain a Data Inventory

-------------------------------------------------------------------------

## 3.3: Configure Data Access Control Lists

-------------------------------------------------------------------------

## 3.4: Enforce Data Retention

-------------------------------------------------------------------------

## 3.5: Securely Dispose of Data

-------------------------------------------------------------------------

## 3.6: Encrypt Data on End-User Devices

-------------------------------------------------------------------------

## 3.7: Establish and Maintain a Data Classification Scheme

-------------------------------------------------------------------------

## 3.8: Document Data Flows

-------------------------------------------------------------------------

## 3.9: Encrypt Data on Removable Media

-------------------------------------------------------------------------

## 3.10: Encrypt Sensitive Data in Transit

-------------------------------------------------------------------------

## 3.11: Encrypt Sensitive Data At Rest

-------------------------------------------------------------------------

## 3.12: Segment Data Processing and Storage Based on Sensitivity

-------------------------------------------------------------------------

## 3.13: Deploy a Data Loss Prevention Solution

-------------------------------------------------------------------------

## 3.14: Log Sensitive Data Access

