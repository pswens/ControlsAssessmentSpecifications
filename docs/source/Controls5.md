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
