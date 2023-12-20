# CIS Control 8: Audit Log Management

Collect, alert, review, and retain audit logs of events that could help
detect, understand, or recover from an attack.

**Why is this CIS Control Critical?**

Log collection and analysis is critical for an enterprise's ability to
detect malicious activity quickly. Sometimes, audit records are the only
evidence of a successful attack. Attackers know that many enterprises
keep audit logs for compliance purposes but rarely analyze them.
Attackers use this knowledge to hide their location, malicious software,
and activities on victim machines. Due to poor or nonexistent log
analysis processes, attackers sometimes control victim machines for
months or years without anyone in the target enterprise knowing.

There are two types of logs that are generally treated and often
configured independently: system logs and audit logs. System logs
typically provide system-level events that show various system process
start/end times, crashes, etc. These are native to systems and take
less configuration to turn on. Audit logs typically include user-level
events -- when a user logs in, accesses a file, etc. -- and takes more
planning and effort to set up.

Logging records are also critical for incident response. After an attack
has been detected, log analysis can help enterprises understand the
extent of an attack. Complete logging records can show, for example,
when and how the attack occurred, what information was accessed, and if
data was exfiltrated. Retention of logs is also critical in case a
follow-up investigation is required or if an attack remains undetected
for a long period of time.

--------------------------------------------------------------------------------

## 8.1: Establish and Maintain an Audit Log Management Process

Establish and maintain an audit log management process that defines the enterprise's logging requirements. At a minimum, address the collection, review, and retention of audit logs for enterprise assets. Review and update documentation annually, or when significant enterprise changes occur, that could impact this Safeguard.

| Asset Type | Security Function | Implementation Groups |
|------------|-------------------|-----------------------|
| Network    | Protect           | 1, 2, 3               |

### Dependencies

- None

### Inputs

1. `GV26`: Enterprise's audit log management process
2. Date of the last review of the audit log management process

### Operations

1. Check if `GV26` the audit log management process exists

   1. If it exists, M1 = 1
   2. If it does not exist, M1 = 0

2. Review `GV26` for elements of the process and, at a minimum, address the collection, review, and retention of audit logs for enterprise assets.

    1. For each element that exists, assign a value of 1. Sum the values of existing elements. (M2)

3.  Compare the date from Input 2 and the current date. Capture the timeframe in terms of months. (M3)

### Measures

- M1 = Output of Operation 1
- M2 = Count of elements included in the audit log management process
- M3 = Timeframe since the last review of the audit log management process

### Metrics

If M1 is 0, this safeguard receives a failing score. The other metrics don't apply. If M3 is greater than twelve, this safeguard is measured at a 0 and receives a failing score. The other metrics don't apply.

#### Completeness

| **Metric**      | The percentage of elements included in the audit log |
|-----------------|-----------------------------------------------------|
| **Calculation** | `M2 / 3`                                            |

--------------------------------------------------------------------------------
--------------------------------------------------------------------------------
--------------------------------------------------------------------------------
--------------------------------------------------------------------------------
--------------------------------------------------------------------------------
--------------------------------------------------------------------------------
--------------------------------------------------------------------------------
--------------------------------------------------------------------------------
