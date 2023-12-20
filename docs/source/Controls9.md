# CIS Control 9: Email and Web Browser Protections

Improve protections and detections of threats from email and web
vectors, as these are opportunities for attackers to manipulate human
behavior through direct engagement.

**Why is this CIS Control Critical?**

Web browsers and email clients are very common points of entry for
attackers because of their direct interaction with users inside an
enterprise. Content can be crafted to entice or spoof users into
disclosing credentials, providing sensitive data, or providing an open
channel to allow attackers to gain access, thus increasing the risk to the
enterprise. Since email and the web are the main means that which users interact
with external and untrusted users and environments, these are prime
targets for both malicious code and social engineering. Additionally, as
enterprises move to web-based email or mobile email access, users no
longer use traditional full-featured email clients, which provide
embedded security controls like connection encryption, strong
authentication, and phishing reporting buttons.

---------------------------------------------------------------------

## 9.1: Ensure Use of Only Fully Supported Browsers and Email Clients

Ensure only fully supported browsers and email clients are allowed to
execute in the enterprise, only using the latest version of browsers and
email clients provided through the vendor.

| Asset Type     | Security Function   | Implementation Groups |
| -------------- | ------------------- | --------------------- |
| Applications   | Protect             | 1, 2, 3               |

### Dependencies

-   Safeguard 2.1: Establish and Maintain a Software Inventory

### Inputs

1.  `GV5`: Authorized software inventory
2.  Authoritative source of information indicating supported/unsupported
    details by product.

### Operations

1.  Use `GV5` to identify and enumerate web browser and email client
    software (M1)

2.  Compare each software identified in Operation 1 to Input 2

    1.  Identify and enumerate software labeled as "supported" that is currently supported (M2)
    2.  Identify and enumerate software labeled as "supported" that is currently unsupported (M3)
    3.  Identify and enumerate software labeled as "unsupported" that is currently unsupported (M4)
    4.  Identify and enumerate software labeled as "unsupported" that is currently supported (M5)

### Measures

-   M1 = Count of authorized web browser and email client software
-   M2 = Count of software labeled as "supported" and currently
    supported
-   M3 = Count of software labeled as "supported" and currently
    unsupported
-   M4 = Count of software labeled as "supported" and currently
    unsupported
-   M5 = Count of software labeled as "supported" and currently
    supported

### Metrics

#### Percentage of Unsupported Web Browser/Email Client Software in Use

| **Metric**      | The percentage of unsupported web browser and email client software in use |
|-----------------|------------------------------------------------------------------------------|
| **Calculation** | `(M3 + M4) / M1`                                                   |

#### Rate of False Positives

| **Metric**      | The percentage of authorized web browser and email client software labeled as "supported" but found to be unsupported |
|-----------------|-------------------------------------------------------------------------------------------------------------------------|
| **Calculation** | `M3 / M1`                                                                                                        |


#### Rate of False Negatives

| **Metric**      | The percentage of authorized web browser and email client software labeled as "unsupported" but found to be supported |
|-----------------|-------------------------------------------------------------------------------------------------------------------------|
| **Calculation** | `M5 / M1`                                                                                                        |

---------------------------------------------------------------------

## 9.2: Use DNS Filtering Services

Use DNS filtering services on all enterprise assets to block access to
known malicious domains.

| Asset Type   | Security Function   | Implementation Groups |
| ------------ | ------------------- | --------------------- |
| Network      | Protect             | 1, 2, 3               |

### Dependencies

-   Safeguard 1.1: Establish and Maintain Detailed Enterprise Asset
    Inventory
-   Safeguard 4.1: Establish and Maintain a Secure Configuration Process

### Inputs

1.  `GV1`: Enterprise asset inventory
2.  `GV5`: Authorized software inventory
3.  `GV3`: Configuration standards

### Operations

1.  Use `GV1` to identify and enumerate assets that support DNS
    filtering (M1)

2.  Use `GV5` to identify and enumerate authorized DNS filtering
    services

3. For each asset identified in Operation 1, check to see if it is configured properly `GV3` to support authorized DNS filtering services from Operation 2

    1.  Identify and enumerate assets properly configured (M2)
    2.  2.  Identify and enumerate assets not properly configured (M3)

### Measures

-   M1 = Count of enterprise assets capable of supporting DNS filtering
-   M2 = Count of assets properly configured to support DNS filtering
-   M3 = Count of assets not properly configured to support DNS
    filtering

### Metrics

#### DNS Filtering Coverage

| **Metric**      | The percentage of assets configured to use authorized DNS filtering services |
|-----------------|-------------------------------------------------------------------------------|
| **Calculation** | `M2 / M1`                                                              |

---------------------------------------------------------------------
---------------------------------------------------------------------
---------------------------------------------------------------------
---------------------------------------------------------------------
