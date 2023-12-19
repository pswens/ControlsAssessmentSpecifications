# CIS Control 8: Audit Log Management

Collect, alert, review, and retain audit logs of events that could help
detect, understand, or recover from an attack.

**Why is this CIS Control Critical?**

Log collection and analysis is critical for an enterprise's ability to
detect malicious activity quickly. Sometimes audit records are the only
evidence of a successful attack. Attackers know that many enterprises
keep audit logs for compliance purposes, but rarely analyze them.
Attackers use this knowledge to hide their location, malicious software,
and activities on victim machines. Due to poor or nonexistent log
analysis processes, attackers sometimes control victim machines for
months or years without anyone in the target enterprise knowing.

There are two types of logs that are generally treated and often
configured independently: system logs and audit logs. System logs
typically provide system-level events that show various system process
start/end times, crashes, etc. These are native to systems, and take
less configuration to turn on. Audit logs typically include user-level
events -- when a user logged in, accessed a file, etc. -- and take more
planning and effort to set up.

Logging records are also critical for incident response. After an attack
has been detected, log analysis can help enterprises understand the
extent of an attack. Complete logging records can show, for example,
when and how the attack occurred, what information was accessed, and if
data was exfiltrated. Retention of logs is also critical in case a
follow-up investigation is required or if an attack remained undetected
for a long period of time.

--------------------------------------------------------------------------------
--------------------------------------------------------------------------------
--------------------------------------------------------------------------------
--------------------------------------------------------------------------------
--------------------------------------------------------------------------------
--------------------------------------------------------------------------------
--------------------------------------------------------------------------------
--------------------------------------------------------------------------------
--------------------------------------------------------------------------------
