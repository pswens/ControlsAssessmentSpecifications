# CIS Control 5: Account Management

Use processes and tools to assign and manage authorization to
credentials for user accounts, including administrator accounts, as well
as service accounts to enterprise assets and software.

**Why is this CIS Control Critical?**

It is easier for an external or internal threat actor to gain
unauthorized access to enterprise assets or data through using valid
user credentials than through "hacking" the environment. There are many
ways to covertly obtain access to user accounts, including weak
passwords account still valid after a user leaves the enterprise,
dormant or lingering test accounts, shared accounts that have not been
changed in months or years, service accounts embedded in applications
for scripts, a user having the same password as one they use for an
an online account that has been compromised (in a public password dump),
social engineering a user to give their password or using malware to
capture passwords or tokens in memory or over the network.

Administrative or highly privileged accounts are a particular target,
because they allow attackers to add other accounts or make changes to
assets that could make them more vulnerable to other attacks. Service
accounts are also sensitive, as they are often shared among teams,
internal and external to the enterprise, and sometimes not known about,
only to be revealed in standard account management audits.

Finally, account logging and monitoring is a critical component of
security operations. While account logging and monitoring are covered in
CIS Control 8 (Audit Log Management) is important in the development
of a comprehensive Identity and Access Management (IAM) program.

---------------------------------------------------------------------------------

## 5.1: Establish and Maintain an Inventory of Accounts

Establish and maintain an inventory of all accounts managed in the enterprise. The inventory must include both user and administrator accounts. The inventory, at a minimum, should contain the person’s name, username, start/stop dates, and department. Validate that all active accounts are authorized on a recurring schedule at a minimum quarterly or more frequently.

| Asset Type | Security Function | Implementation Groups |
|------------|-------------------|-----------------------|
| Users      | Identify          | 1, 2, 3               |

### Dependencies

- Safeguard 2.1: Establish and Maintain a Software Inventory

### Inputs

1. `GV5`: Authorized software inventory
2. `GV22`: Inventory of accounts
3. Date of last review of the inventory of accounts

### Operations

1. Check if the enterprise maintains an inventory of user and administrative accounts (Input 2):

   1. If the inventory exists, M1 = 1
   2. If the inventory does not exist, M1 = 0

2. Using the inventory of accounts `GV22`, determine if the inventory captures the following elements: person's name, username, start/stop dates, and department:

   1. Each element is assigned a value of 1 if it exists and 0 if it does not. Total the number of elements that exist. (M3)

3. Using `GV22`, check each account for elements: person's name, username, start/stop dates, and department:

   1. Identify and enumerate accounts with all elements (M4)
   2. Identify and enumerate accounts missing or with incomplete elements (M5)

4. Use `GV5` to identify authentication systems or other software that manages accounts `GV23`.

5. Using the output of Operation 4, enumerate all current user and administrative accounts throughout the enterprise (M6)

6. Compare the output of Operation 5 with `GV22`:

   1. Identify and enumerate accounts that are supposed to be active/enabled (M7)
   2. Identify and enumerate accounts that are supposed to be disabled/removed (M8)

7. Compare the current date to the date provided in Input 3 and enumerate the timeframe in months (M9)

### Measures

- M1 = Does the account inventory exist (Output of Operation 1)
- M2 = Count of accounts in `GV22`
- M3 = Count of elements provided in the inventory
- M4 = Count of accounts in inventory with complete information
- M5 = Count of accounts in inventory with missing or incomplete information
- M6 = Count of current accounts identified through Operation 5
- M7 = Count of authorized accounts
- M8 = Count of unauthorized accounts
- M9 = Timeframe of the last update in months

### Metrics

- If M1 is 0, this safeguard receives a failing score, and other metrics don't apply.
- If M9 is greater than three, this safeguard is measured at a 0 and receives a failing score. The other metrics don't apply.

#### Completeness of Inventory

| **Metric**      | The percentage of minimum elements included in the inventory. |
|-----------------|-------------------------------------------------------------|
| **Calculation** | `M3 / 4`                                                    |

| **Metric**      | The percentage of accounts with complete information.       |
|-----------------|-------------------------------------------------------------|
| **Calculation** | `M4 / 2`                                                    |

#### Accuracy of Inventory

| **Metric**      | The percentage of accurately listed accounts in the inventory. |
|-----------------|---------------------------------------------------------------|
| **Calculation** | `M8 / M6`                                                     |

---------------------------------------------------------------------------------

## 5.2: Use Unique Passwords

Use unique passwords for all enterprise assets. Best practice implementation includes, at a minimum, an 8-character password for accounts using MFA and a 14-character password for accounts not using MFA.

| Asset Type | Security Function | Implementation Groups |
|------------|-------------------|-----------------------|
| Users      | Protect           | 1, 2, 3               |

### Dependencies

- None

### Inputs

1. `GV20`: Unique password policy for the enterprise

### Operations

1. Check if the enterprise has a unique password policy:

   1. If the policy is available, M1 = 1
   2. Otherwise M1 = 0

2. Review the policy and determine whether it includes password guidance for accounts without MFA:

   1. If guidance is included, M2 = 1

      1. Does guidance, at a minimum, require a fourteen-character password:

         1. If password guidance is fourteen characters or longer, M3 = 1
         2. Otherwise M3 = 0

   2. Otherwise M2 = 0

3. Review the policy and determine whether it includes password guidance for accounts with MFA:

   1. If guidance is included, M4 = 1

      1. Does guidance, at a minimum, require an eight-character password:

      1. If password guidance is eight characters or longer, M5 = 1
      2. Otherwise M5 = 0

   2. Otherwise M4 = 0

### Measures

- M1 = Does a password policy exist?
- M2 = Does guidance exist for accounts without MFA?
- M3 = Does guidance for accounts without MFA meet minimum guidance?
- M4 = Does guidance exist for accounts with MFA?
- M5 = Does guidance for accounts with MFA meet minimum guidance?

### Metrics

- If M1 is 0, the safeguard receives a failing score. Other metrics don\'t
apply

#### Completeness of Password Policy

| **Metric**      | The percentage of completeness of the unique password policy |
|-----------------|-----------------------------------------------------------------------------------|
| **Calculation** | `(M2 + M4) / 2`                                                                  |

#### Strength of Policy

| **Metric**      | The percentage of password guidance that meets minimum character length standards |
|-----------------|-----------------------------------------------------------------------------------|
| **Calculation** | `(M3 + M5) / 2`                                                                  |

---------------------------------------------------------------------------------
---------------------------------------------------------------------------------
---------------------------------------------------------------------------------
---------------------------------------------------------------------------------
---------------------------------------------------------------------------------
