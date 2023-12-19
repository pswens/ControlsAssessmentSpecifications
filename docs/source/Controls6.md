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

There are some user activities that pose greater risk to an enterprise,
either because they are accessed from untrusted networks, or performing
administrator functions that allow the ability to add, change, or remove
other accounts, or make configuration changes to operating systems or
applications to make them less secure. This also enforces the importance
of using MFA and Privileged Access Management (PAM) tools.

Some users have access to enterprise assets or data they do not need for
their role; this might be due to an immature process that gives all
users all access, or lingering access as users change roles within the
enterprise over time. Local administrator privileges to users' laptops
is also an issue, as any malicious code installed or downloaded by the
user can have greater impact on the enterprise asset running as
administrator. User, administrator, and service account access should be
based on enterprise role and need.
