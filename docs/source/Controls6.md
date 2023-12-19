# CIS Control 6: Access Control Management

Use processes and tools to create, assign, manage, and revoke access
credentials and privileges for user, administrator, and service accounts
for enterprise assets and software.

**Why is this CIS Control Critical?**

Where CIS Control 5 deals specifically with account management, CIS
Control 6 focuses on managing what access these accounts have, ensuring
users only have access to the data or enterprise assets appropriate for
their role, and ensuring that there is strong authentication for
critical or sensitive enterprise data or functions. Accounts should only
have the minimal authorization needed for the role. Developing
consistent access rights for each role and assigning roles to users is a
best practice. Developing a program for complete provision and
de-provisioning access is also important. Centralizing this function is
ideal.

There are some user activities that pose a greater risk to an enterprise,
either because they are accessed from untrusted networks or performing
administrator functions that allow the ability to add, change, or remove
other accounts, or make configuration changes to operating systems or
applications to make them less secure. This also enforces the importance
of using MFA and Privileged Access Management (PAM) tools.

Some users have access to enterprise assets or data they do not need for
their role; this might be due to an immature process that gives all
users all access or lingering access as users change roles within the
enterprise over time. Local administrator privileges to users' laptops
are also an issue, as any malicious code installed or downloaded by the
user can have a greater impact on the enterprise asset running as
administrator. User, administrator, and service account access should be
based on enterprise role and need.

------------------------------------------------------------------------------------

# 6.1: Establish an Access Granting Process

Establish and follow a process, preferably automated, for granting
access to enterprise assets upon new hire, rights grant, or role change
of a user.

 | Asset Type  | Security Function |  Implementation Groups |
 | ------------|-------------------|----------------------- |
 | Users       | Protect           | 1, 2, 3                |

## Dependencies

-   None

## Inputs

1.  Enterprise process for granting access to enterprise assets

## Operations

1. Check to see if Input 1 exists:
   
      1. If the enterprise has an access granting process, M1 = 1
      2. If the enterprise does not have an access granting process, M1 = 0

3. Using Input 1, check to see if the process includes, at a minimum, a way to grant access upon new hire, rights grat, and role change of a user:
   
      1. For each element that is included, assign a value of 1. Sum the value of the elements included. (M2)

## Measures

-   M1 = Output of Operation 1
-   M2 = Count of elements included in the access granting process

## Metrics

If M1 is 0, the safeguard receives a failing score. The other metric
don\'t apply.

### Completeness of Process

| **Metric**      | The percentage of elements included in the access granting process |
|-----------------|--------------------------------------------------------------------|
| **Calculation** | `M2 / 3`                                          |
