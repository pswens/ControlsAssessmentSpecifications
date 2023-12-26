# CIS Control 18: Penetration Testing

Test the effectiveness and resiliency of enterprise assets through
identifying and exploiting weaknesses in controls (people, processes,
and technology), and simulating the objectives and actions of an
attacker.

**Why is this CIS Control Critical?**

A successful defensive posture requires a comprehensive program of
effective policies and governance, strong technical defenses combined
with appropriate action from people. However, it is rarely perfect. In
a complex environment where technology is constantly evolving and new
attacker tradecraft appears regularly; enterprises should periodically
test their controls to identify gaps and assess their resiliency.
This test may be from an external network, internal network, application,
system, or device perspective. It may include social engineering of
users or physical access control bypasses.

Often, penetration tests are performed for specific purposes, like as a
"dramatic" demonstration of an attack, usually to convince
decision-makers of their enterprise's weaknesses and as a means to test
the correct operation of enterprise defenses ("verification") • To test
that the enterprise has built the right defenses in the first place
("validation")

Independent penetration testing can provide valuable and objective
insights about the existence of vulnerabilities in enterprise assets and
humans and the efficacy of defenses and mitigating controls to protect
against adverse impacts to the enterprise. They are part of a
comprehensive, ongoing program of security management and improvement.
They can also reveal process weaknesses, such as incomplete or
inconsistent configuration management or end-user training.

Penetration testing differs from vulnerability testing, described in CIS
Control 7. Vulnerability testing just checks for the presence of known,
insecure enterprise assets and stops there. Penetration testing goes
further to exploit those weaknesses to see how far an attacker could
get and what business process or data might be impacted through
the exploitation of that vulnerability. This is an important detail, and
often penetration testing and vulnerability testing are incorrectly used
interchangeably. Vulnerability testing is exclusively automated scanning
with sometimes manual validation of false positives, whereas penetration
testing requires more human involvement and analysis, sometimes
supported through the use of custom tools or scripts. However,
vulnerability testing is often a starting point for a penetration test.

Another common term is "Red Team" exercises. These are similar to
penetration tests in that vulnerabilities are exploited; however, the
the difference is the focus. Red Teams simulate specific attacker TTPs to
evaluate how an enterprise's environment would withstand an attack from
a specific adversary or category of adversaries.

-----------------------------------------------------------------------

## 18.1: Establish and Maintain a Penetration Testing Program

Establish and maintain a penetration testing program appropriate to the size,
complexity, and maturity of the enterprise. Penetration testing program
characteristics include scope, such as network, web application,
Application Programming Interface (API), hosted services, and physical
premise controls, frequency; limitations, such as acceptable hours, and
excluded attack types; point of contact information; remediation, such
as how findings will be routed internally and retrospective
requirements.

| Asset Type   | Security Function   | Implementation Groups |
| ------------ | ------------------- | --------------------- |
| N/A          | Identify            | 2, 3                  |

### Dependencies

-   None

### Inputs

1.  `GV53` Penetration Testing Program Documentation
2.  Date of last update to the penetration testing program documentation

### Operations

1.  Determine if Input 1 `GV53` exists within the enterprise

    1.  If Input 1 exists, M1 = 1
    2.  If Input 1 does not exist, M1 = 0

2.  Check Input 1 for completeness. At a minimum, it should include the scope of the program, frequency, point of contact information, remediation, and retrospective requirements.

    1.  For each component included in the documentation, assign a value of 1. Sum the values. (M2)

3.  Compare Input 2 to the current date. Capture timeframe in months (M3)

### Measures

-   M1 = Output of Operation 1
-   M2 = Sum of components included in the documentation
-   M3 = Timeframe in months since the last update to the documentation

### Metrics

-   If M1 is 0, this safeguard receives a failing score. The other
    metrics don\'t apply.
-   If M3 is greater than twelve months, then this safeguard is measured
    at a 0 and receives a failing score. The other metrics don\'t apply.

#### Completeness

| **Metric**      | The percentage of minimum components included in the program documentation |
|-----------------|----------------------------------------------------------------------------|
| **Calculation** | `M2 / 5`                                                            |

-----------------------------------------------------------------------

## 18.2: Perform Periodic External Penetration Tests

Perform periodic external penetration tests based on program
requirements, no less than annually. External penetration testing must
include enterprise and environmental reconnaissance to detect
exploitable information. Penetration testing requires specialized skills
and experience and must be conducted through a qualified party. The
testing may be in a clear box or an opaque box.

| Asset Type   | Security Function   | Implementation Groups |
| ------------ | ------------------- | --------------------- |
| Network      | Identify            | 2, 3                  |

### Dependencies

-   Safeguard 18.1: Establish and Maintain a Penetration Testing Program

### Inputs

1.  `GV54`: Most Recent External Penetration Report

### Operations

1.  Check Input 1 `GV54` for the date of the most recent external penetration
    test. Compare the date to the current date and capture the timeframe in months (M1)

### Measures

-   M1 = Timeframe since the last external penetration test

### Metrics

-   If M1 is greater than twelve months, then this safeguard is measured
    at a 0 and receives a failing score. The other metrics don't apply.
    
-----------------------------------------------------------------------

## 18.3: Remediate Penetration Test Findings

Remediate penetration test findings based on the enterprise's policy for
remediation scope and prioritization.

| Asset Type   | Security Function   | Implementation Groups |
| ------------ | ------------------- | --------------------- |
| Network      | Protect             | 2, 3                  |

### Dependencies

-   Safeguard 18.2: Perform Periodic External Penetration Tests

### Inputs

1.  :code:\`GV53: Penetration Testing Program Documentation
2.  `GV54`: Most Recent External Penetration Report
3.  External penetration report prior to most recent report

### Operations

1.  Use the findings in Input 3 to identify and enumerate the
    vulnerabilities outlined (M1)

2.  Use the findings in Input 2 `GV54` to identify the vulnerabilities
    outlined

3.  Compare the output of Operation 1 and Operation 1

    1.  Identify and enumerate vulnerabilities found in Input 3 that continue to be in Input 2 (M2)
    2.  Identify and enumerate vulnerabilities found in Input 3 that no longer appear in Input 2 (M3)

4.  Using the program documentation from Input 1 `GV53`, determine whether the output of Operation 3.2 is still within scope based on enterprise\'s policy

    1.  Identify and enumerate vulnerabilities within scope (M4)
    2.  Identify and enumerate vulnerabilities out of scope (M5)

### Measures

-   M1 = Count of initial vulnerabilities identified by a penetration test
-   M2 = Count of successfully remediated vulnerabilities
-   M3 = Count of vulnerabilities that have not been remediated
-   M4 = Count of unremediated vulnerabilities still in scope
-   M5 = Count of unremediated vulnerabilities out of scope

### Metrics

#### Compliance

| **Metric**      | The percent of successfully remediated or still within scope vulnerabilities identified in the initial penetration test findings. |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------|
| **Calculation** | `(M3 + M4) / M1`                                                                                                                        |

-----------------------------------------------------------------------

## 18.4: Validate Security Measures

Validate security measures after each penetration test. If deemed
necessary, modify rulesets and capabilities to detect the techniques
used during testing.

| Asset Type   | Security Function   | Implementation Groups |
| ------------ | ------------------- | --------------------- |
| Network      | Protect             | 3                     |

### Dependencies

-   Safeguard 18.1: Establish and Maintain a Penetration Testing Program

### Inputs

1.  `GV53`: Penetration Testing Program Documentation
2.  `GV54`: Most Recent External Penetration Report
3.  `GV55`: Most Recent Internal Penetration Report

### Operations

1.  Check Input 1 `GV53` to determine if it includes an enterprise process for validating security measures after a penetration test

    1.  If the process exists, M1 = 1
    2.  If the process does not exist, M1 = 0

2.  Using the findings from both Input 2 `GV54` and Input 3 `GV55`, as
    applicable, identify and enumerate security measures that are required modification (M2)

3.  For each security measure identified in Operation 2, check if modifications have been made

    1.  Identify and enumerate security measures that have been modified per the enterprise\'s defined process (M3)
    2.  Identify and enumerate security measures not yet modified per the enterprise\'s defined process (M4)

### Measures

-   M1 = Output of Operation 1
-   M2 = Count of security measures requiring modification
-   M3 = Count of security measures requiring modification that are
    properly addressed
-   M4 = Count of security measures requiring modification that are not
    yet addressed

### Metrics

-   If M1 is 0, this safeguard receives a failing score. The other
    metrics don\'t apply.

#### Compliance

| **Metric**      | The percentage of security measures requiring modification that have been properly addressed. |
|-----------------|--------------------------------------------------------------------------------------------------|
| **Calculation** | `M3 / M2`                                                                                        |

-----------------------------------------------------------------------

## 18.5: Perform Periodic Internal Penetration Tests

Perform periodic internal penetration tests based on program
requirements, no less than annually. The testing may be a clear box or
an opaque box.

| Asset Type   | Security Function   | Implementation Groups |
| ------------ | ------------------- | --------------------- |
| N/A          | Identify            | 3                     |

### Dependencies

-   Safeguard 18.1: Establish and Maintain a Penetration Testing Program

### Inputs

1.  `GV55`: Most Recent Internal Penetration Report

### Operations

1.  Check Input 1 `GV55` for the date of the most recent internal penetration
    test. Compare the date to the current date and capture the timeframe in months
    (M1)

### Measures

-   M1 = Timeframe since the last internal penetration test

### Metrics

-   If M1 is greater than twelve months, then this safeguard is measured
    at a 0 and receives a failing score. The other metrics don\'t apply.
    
-----------------------------------------------------------------------

## 18.6: Ensure Software Development Personnel Are Trained in Secure Coding

Ensure that all software development personnel receive training in
writing secure code for their specific development environment and
responsibilities.

| Asset Type   | Security Function   | Implementation Groups |
| ------------ | ------------------- | --------------------- |
| N/A          | N/A                 | 2, 3                  |


### Dependencies

-   None

### Inputs

1.  List of software development personnel, including assigned
    development environments and roles
2.  List of secure coding training courses required for each development
    environment and role
3.  List of secure coding training courses that each person has
    completed

### Operations

1.  For each person in Input 1, use the development environments and
    roles assigned to that person to determine which secure coding
    training courses the person is required to take; note these
    individual lists of required courses in M1.

2.  For each person in Input 1, compare the courses that person is required to take from M1 to the courses that person has completed from Input 3.

    1.  Create a list of the required courses the person has completed (M2)
    2.  Create a list of the required courses the person has not completed (M3).

### Measures

-   M1 = List of courses that software development personnel are
    required to take, by individual
-   M2 = List of required courses that software development personnel
    have completed, by individual (compliant list)
-   M3 = List of required courses that software development personnel
    have not been completed by the individual (non-compliant list)
-   M4 = Count of required courses by individual (count of M1)
-   M5 = Count of completed required courses by the individual (count of M2)

### Metrics

#### Coverage

| **Metric**      | The ratio of completed required courses to total required courses by individual. |
|-----------------|--------------------------------------------------------------------------------------|
| **Calculation** | `Individual's M5 / Individual's M4`                                               |

**NOTE**: An organizational average completion rate can be calculated by
averaging the individual completion ratios from the above \"Coverage\"
metric.

-----------------------------------------------------------------------

## 18.7: Apply Static and Dynamic Code Analysis Tools

Apply static and dynamic analysis tools to verify that secure coding
practices are being adhered to for internally developed software.

| Asset Type   | Security Function   | Implementation Groups |
| ------------ | ------------------- | --------------------- |
| N/A          | N/A                 | 2, 3                  |

### Dependencies

-   Sub-control 2.1: Maintain Inventory of Authorized Software

### Inputs

1.  The inventory of internally-developed software (from the
    organization\'s software inventory)
2.  The inventory of static analysis tools (from the organization\'s
    software inventory)
3.  The inventory of dynamic analysis tools (from the organization\'s
    software inventory)

### Operations

1.  Map the inventory of internally developed software to the applicable
    static/dynamic analysis tools that are used for verification.

### Measures

-   M1(i) = (For each software \"i\" from Input 1) 1 if the software is
    verified by static analysis tool(s); 0 otherwise
-   M2(i) = (For each software \"i\" from Input 1) 1 if the software is
    verified by dynamic analysis tool(s); 0 otherwise
-   M3 = Count of internally developed software (the count of Input 1)

### Metrics

#### Static Analysis Tool Coverage

| **Metric**      | The ratio of internally developed software verified by static analysis tools to the total number of internally developed software applications. |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Calculation** | `(SUM from i=1..M3 (M1(i))) / M3`                                                                                                                      |

#### Dynamic Analysis Tool Coverage

| **Metric**      | The ratio of internally developed software verified by dynamic analysis tools to the total number of internally developed software applications. |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Calculation** | `(SUM from i=1..M3 (M2(i))) / M3`                                                                                                                        |

-----------------------------------------------------------------------

## 18.8: Establish a Process to Accept and Address Reports of Software Vulnerabilities

Establish a process to accept and address reports of software
vulnerabilities, including providing a means for external entities to
contact your security group.

| Asset Type   | Security Function   | Implementation Groups |
| ------------ | ------------------- | --------------------- |
| N/A          | N/A                 | 2, 3                  |

### Dependencies

-   None

### Inputs

1.  Written process for accepting and addressing software
    vulnerabilities

### Operations

1.  Determine whether a written process for accepting and addressing
    software vulnerabilities exist (M1).

2.  Manually review the written process for accepting and addressing software vulnerabilities (Input 1).

    1.  Identify whether the document provides a means for external entities to contact your security group (M2)
    2.  Identify whether the document adequately describes the process for accepting reports of software vulnerabilities (M3)
    3.  Identify whether the document adequately describes the process for addressing those reports (M4)

### Measures

-   M1 = Boolean value indicating whether a written process for
    accepting and addressing software vulnerabilities exists; 1 if it
    exists, 0 if it does not
-   M2 = Boolean value indicating whether the document provides a means
    for external entities to contact your security group; 1 if the
    document provides this info, 0 if it does not
-   M3 = Boolean value indicating whether the document adequately
    describes the process for accepting reports of software
    vulnerabilities; 1 if the document adequately describes this
    process, 0 if it does not
-   M4 = Boolean value indicating whether the document adequately
    describes the process for addressing reports of software
    vulnerabilities; 1 if the document adequately describes this
    process, 0 if it does not

### Metrics

#### Process Completeness

| **Metric**      | Does the written process for accepting and addressing reports of software vulnerabilities exist, and is it complete? |
|-----------------|-----------------------------------------------------------------------------------------------------------------------|
| **Calculation** | `M1 AND M2 AND M3 AND M4`                                                                                             |

-----------------------------------------------------------------------

## 18.9: Separate Production and Non-Production Systems

Maintain separate environments for production and non-production
systems. Developers should not have unmonitored access to production
environments.

| Asset Type   | Security Function   | Implementation Groups |
| ------------ | ------------------- | --------------------- |
| N/A          | N/A                 | 2, 3                  |

### Dependencies

-   Sub-control 1.4: Maintain Detailed Asset Inventory
-   Sub-control 1.5: Maintain Asset Inventory Information
-   Sub-control 2.1: Maintain Inventory of Authorized Software
-   Sub-control 2.5: Integrate Software and Hardware Asset Inventories

### Inputs

1.  The inventory of systems used for production and non-production
    deployments
2.  The inventory of user accounts
3.  The mechanism for monitoring user account access to systems

### Operations

1.  From Input 1, categorize the deployments of systems into those with
    production deployments and those with non-production deployments.
    Note that systems *should* have both production and 1..n
    non-production deployments (including development, staging,
    integration testing, etc).
2.  From Input 2, determine the list of user accounts with access to
    production environments

### Measures

-   M1(i) = (For each system with a production deployment "i") 1 if at
    At least one non-production deployment environment exists for that
    system, 0 otherwise.
-   M2 = Count of systems with a production deployment
-   M3 = Count of user accounts whose access to production environments
    is monitored by the mechanism defined by Input 3.
-   M4 = Count of user accounts with access to production environments
    (the count from Operation 2).

### Metrics

#### Environment Coverage

| **Metric**      | The ratio of production systems where at least one non-production deployment exists to the total number of production systems |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------|
| **Calculation** | `(SUM from i=1..M2 (M1(i))) / M2`                                                                                         |

#### Monitored Account Coverage

| **Metric**      | The ratio of accounts with production system access that are monitored to the total accounts with production system access |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------|
| **Calculation** | `M3 / M4`                                                                                                                   |

-----------------------------------------------------------------------

## 18.10: Deploy Web Application Firewalls

Protect web applications by deploying web application firewalls (WAFs)
that inspect all traffic flowing to the web application for common web
application attacks. For applications that are not web-based, specific
application firewalls should be deployed if such tools are available for
the given application type. If the traffic is encrypted, the device
should either sit behind the encryption or be capable of decrypting the
traffic prior to analysis. If neither option is appropriate, a
host-based web application firewall should be deployed.

| Asset Type   | Security Function   | Implementation Groups |
| ------------ | ------------------- | --------------------- |
| N/A          | N/A                 | 2, 3                  |

### Dependencies

-   Sub-control 2.1: Maintain Inventory of Authorized Software

### Inputs

1.  The inventory of authorized software

### Operations

1.  Enumerate all in-house owned and operated software (i.e. applications in the software inventory that are developed in-house and/or acquired) for which there is an application-level firewall technology exists
2.  Enumerate all application-level firewalls (including WAF and host-based firewalls)
3.  For each application-level firewall, enumerate the covered software applications
4.  Complement the set of software applications identified in the first operation with the covered software applications

### Measures

-   M1 = Enumerated list of all software in the inventory for which an
    application-level firewall technology exists
-   M2 = Enumerated list of all application-level firewalls
-   M3 = Enumerated list of applications covered by application-level
    firewalls
-   M4 = Enumerated list of applications not covered by software
    applications (fourth operation)
-   M5 = Count of software for which an application-level firewall
    technology exists (count of M1)
-   M6 = Count of application-level firewalls (count of M2)
-   M7 = Count of applications covered by application-level firewalls
    (count of M3)
-   M8 = Count of applications not covered by software applications
    (count of M4)

### Metrics

#### Coverage

| **Metric**      | The ratio of the number of applications covered by an application-level firewall to the number of eligible applications in the enterprise. |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| **Calculation** | `M7 / M5`                                                                                                                                      |

-----------------------------------------------------------------------

## 18.11: Use Standard Hardening Configuration Templates for Databases

For applications that rely on a database, use standard hardening
configuration templates. All systems that are part of critical business
processes should also be tested.

| Asset Type   | Security Function   | Implementation Groups |
| ------------ | ------------------- | --------------------- |
| N/A          | N/A                 | 2, 3                  |

### Dependencies

-   Sub-control 1.4: Maintain Detailed Asset Inventory
-   Sub-control 1.5: Maintain Asset Inventory Information
-   Sub-control 2.1: Maintain Inventory of Authorized Software
-   Sub-control 2.5: Integrate Software and Hardware Asset Inventories
-   Sub-control 5.1: Establish Secure Configurations

### Inputs

1.  The list of database management software being used in the
    organization
2.  The list of systems on which database instances reside
3.  The list of enterprise security configuration standards

### Operations

1.  Determine, from the list of enterprise security configuration
    standards, which are applicable to database management software (M1)
2.  From the list of enterprise security configuration standards,
    calculate the number of database management software that are
    covered by the standards (perform the intersection of the results of
    Operation 1 with Input 1; the result is M2)

### Measures

-   M1 = List of enterprise security configuration standards specific to
    database management systems
-   M2 = Count of M1
-   M3 = List of database management software covered by applicable
    enterprise security configuration standards
-   M4 = Count of M3
-   M5 = List of database management software not covered by applicable
    enterprise security configuration standards
-   M6 = Count of M5
-   M7 = Count of database management software being used in the
    organization (from Input 1)

### Metrics

#### Coverage

| **Metric**      | The ratio of database management software covered by applicable enterprise security configuration standards to the total number of database management software. |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Calculation** | `M4 / M7`                                                                                                                                                         |

**NOTE**: The second ask of this sub-control speaks to the assessment of Input 2 against security configuration standards determined by Operation 1.
