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
    based on the sensitivity of the data
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

Establish and maintain a data inventory based on the enterprise’s data management process. Inventory sensitive data, at a minimum. Review and update inventory annually, at a minimum, with a priority on sensitive data.

| Asset Type | Security Function | Implementation Groups |
|------------|-------------------|-----------------------|
| Data       | Identify          | 1, 2, 3               |

### Dependencies

- Sub-control 1.1: Establish and Maintain Detailed Enterprise Asset Inventory

### Inputs

1. `GV11`: Portion of data management process addressing data sensitivity
2. `GV12`: Data Inventory consisting of the data set of sensitive information for which the enterprise is responsible
3. `GV1`: Enterprise asset inventory
4. Date of the last update to the sensitive data inventory

### Operations

1. Use `GV11` to map Input 2 to sensitivity per the guidance in the data management process
   1. Identify and enumerate items in the data set that have a mapping (M2)
   2. Identify and enumerate items in the data set that do not have a mapping (M3)
2. Use `GV1` and M2 from Operation 1 to map the data set to assets storing data
   1. Identify and enumerate items that have complete and correct mapping to asset and sensitivity (M4)
   2. Identify and enumerate items that have partial mapping to sensitivity (M5)
3. Use `GV1` and M3 from Operation 2 to map the data set, without sensitivity mapping, to assets storing data
   1. Identify and enumerate items that have partial mapping to assets (M6)
   2. Identify and enumerate items that have no mapping at all (M7)
4. Compare the current date to Input 4 and capture the timeframe in months (M8)



### Measures

- M1 = `GV11`
- M2 = Count of sensitive data addressed in `GV11`
- M3 = Count of sensitive data not addressed in `GV11`
- M4 = Count of data with complete sensitivity and asset storage inventory
- M5 = Count of data with partial mapping to sensitivity
- M6 = Count of data with partial mapping to assets
- M7 = Count of data with no mapping to sensitivity or asset
- M8 = Timeframe since the last update to the sensitive data inventory in months
- M9 = Count of items in `GV12`

### Metrics

- If M1 is 0, this safeguard receives a failing score. The other metrics don't apply.
- If M9 is greater than 12 months, this safeguard is scored at zero and receives a failing score. The other metrics don't apply.

#### Completeness of Sensitive Data Inventory

| Metric          | Percentage of data with complete information |
|-----------------|--------------------------------------------|
| Calculation     | `M4 / M9`                                  |

#### Partial Completeness of Sensitive Data Inventory

| Metric          | Percentage of data with partial inventory |
|-----------------|-----------------------------------------|
| Calculation     | `(M5 + M6) / M9`                         |

-------------------------------------------------------------------------

## 3.3: Configure Data Access Control Lists

Configure data access control lists based on a user’s need to know. Apply data access control lists, also known as access permissions, to local and remote file systems, databases, and applications.

| Asset Type | Security Function | Implementation Groups |
|------------|-------------------|-----------------------|
| Data       | Protect           | 1, 2, 3               |

### Dependencies

- Safeguard 3.2: Establish and Maintain a Data Inventory
- Safeguard 4.1: Establish and Maintain a Secure Configuration Process
- Safeguard 5.1: Establish and Maintain an Inventory of Accounts

### Inputs

1. :code:`GV12`: Sensitive Data Inventory
2. :code:`GV1`: Enterprise asset inventory
3. :code:`GV3`: Configuration Standards
4. :code:`GV13`: Portion of data management process addressing data owners
5. :code:`GV14`: Portion of data management process addressing data handling
6. :code:`GV22`: Inventory of Accounts

### Assumptions

### Operations

1. Use the data management process, specifically :code:`GV13` and :code:`GV14`, as guidelines to map user accounts to sensitive data in :code:`GV12`.
   1. Identify and enumerate sensitive data correctly mapped to user accounts (M1)
   2. Identify and enumerate sensitive data not correctly mapped to user accounts (M2)
2. For each enterprise asset storing sensitive data, as outlined by :code:`GV12`,
   1. Identify and enumerate all assets storing sensitive data (M3)
   2. Use :code:`GV3` to check and enumerate assets that are properly configured to only allow users as identified in Operation 1 (M4)
   3. Use :code:`GV3` to check and enumerate assets that are improperly configured to only allow users as identified in Operation 1 (M5)

### Measures

- M1 = Count of sensitive data correctly mapped to user accounts per the data management process
- M2 = Count of sensitive data not correctly mapped to user accounts per the data management process
- M3 = Count of assets storing sensitive data
- M4 = Count of properly configured assets to support data access control
- M5 = Count of improperly configured assets to support data access control
- M6 = :code:`GV17`
- M7 = :code:`GV13`
- M8 = :code:`GV14`

### Metrics

If either M7 or M8 is 0, this safeguard receives a failing score. The other metrics don't apply.

#### Completeness of User Access Control

| Metric          | Percentage of user accounts properly mapped to sensitive data |
|-----------------|---------------------------------------------------------------|
| Calculation     | `M1 / M6`                                              |

## Properly Configured Assets

| Metric          | Percentage of assets properly configured to control access of sensitive data |
|-----------------|------------------------------------------------------------------------------|
| Calculation     | `M4 / M3`                                                            |


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

