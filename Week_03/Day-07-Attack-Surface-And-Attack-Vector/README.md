# Day 07 — Attack Surface and Attack Vectors

## Scenario Summary
BreachForge Demo Company is a fictional company with several digital resources such as a public website, employee login portal, public API, company email accounts, cloud storage, remote access service, file upload feature, and employee user accounts.
The provided simulated security logs show authentication and file-access activity involving `WEB-SERVER-01`, `VPN-GATEWAY`, and `FILE-SERVER-01`.
For this analysis, these three log-related systems are treated as the primary areas requiring security attention. The analysis is based only on the information provided in the scenario and simulated logs.

## Identified Attack Surface
1. WEB-SERVER-01 - Authentication-Enabled Web Server

   The logs show that the **admin** account was being used to log in to `WEB-SERVER-01`.
   There were four failed login attempts from `203.0.113.45`. After that, a successful login for the same **admin** account happened from another IP address, `192.168.1.25`.
   Since this system is accepting login attempts, it can be considered an area that needs security attention.

2. VPN-GATEWAY - Remote Access Service

   The logs show login activity for the **sarah** account on `VPN-GATEWAY`.
   There were three failed login attempts from `192.168.1.50`. After these attempts, a successful login happened from the same IP address. A password reset was also completed shortly afterward.
   Since the VPN gateway provides remote access, protecting it is important because unauthorized access could potentially provide access to company resources.

3. FILE-SERVER-01 - File Server/File Access

   The logs show login activity for the **finance** account on `FILE-SERVER-01`.
   There were five failed login attempts from `198.51.100.77`. A successful login happened afterward from the same IP address. Shortly after that, the account downloaded a file named `payroll_2026.xlsx`.
   Because this system is being used to access company files, it needs security attention, especially when sensitive-looking files are involved.

## Possible Attack Vectors
1. WEB-SERVER-01 -> Credential guessing or use of stolen credentials.

   There were several failed login attempts for the **admin** account before a successful login occurred. This could be a sign that someone was trying different credentials or that previously obtained credentials were being used.
   However, the logs alone are not enough to say that an attack definitely happened.

2. VPN-GATEWAY -> Stolen credentials or repeated login attempts.

   The **sarah** account had three failed login attempts and then a successful login. A password reset was also completed shortly afterward.
   This sequence is worth checking because it could be normal activity by the user, but it could also indicate suspicious account activity.

3. FILE-SERVER-01 -> Credential guessing or use of compromised credentials

   The **finance** account had five failed login attempts before a successful login. Shortly after the successful login, `payroll_2026.xlsx` was downloaded.
   This could be a legitimate action by the finance user, but because the activity happened after several failed login attempts, it would be worth reviewing.

## Attack Surface vs Attack Vector
**Attack Surface** means where a security risk may exist.
**Attack Vector** means how someone could potentially try to reach or take advantage of that risk.
So, the attack surface is the area being exposed, while the attack vector is the possible way of approaching it.
Also, just because something is part of the attack surface does not mean that it is automatically vulnerable.

## Risk Explanation
1. WEB-SERVER-01

   The repeated failed login attempts for the **admin** account could indicate suspicious authentication activity.

2. VPN-GATEWAY

   The repeated failed login attempts followed by a successful login and password reset should be reviewed.

3. FILE-SERVER-01

   The repeated failed login attempts followed by a successful login and download of a payroll-related file could require investigation.

## Basic Security Control
1. WEB-SERVER-01

   Use strong passwords, multi-factor authentication, and login rate limiting.

2. VPN-GATEWAY

   Use multi-factor authentication and monitor repeated failed VPN logins.

3. FILE-SERVER-01

   Use least-privilege access and monitor access to important files.

## Observation vs Assumptions
### Observations
There are things that are directly shown in the scenario or logs:
- **admin** had four failed login attempts on `WEB-SERVER-01`.
- A successful **admin** login happened afterward from a different IP address.
- **sarah** had three failed login attempts on `VPN-GATEWAY`.
- A successful **sarah** login happened afterward.
- A password reset was completed for **sarah**.
- **finance** had five failed login attempts on `FILE-SERVER-01`.
- A successful **finance** login happened afterward.
- `payroll_2026.xlsx` was downloaded after the successful finance login.

### Assumptions
These are things that the logs do not confirm:
- The failed login attempts were definitely an attack.
- The successful logins were unauthorized.
- Any account was compromised.
- The password reset was done by an attacker.
- The payroll file was downloaded without permission.
- `WEB-SERVER-01` is definitely the employee login portal.
- `FILE-SERVER-01` is definitely the cloud storage service.

I have kept these as assumptions because there is not enough evidence in the provided logs to confirm them.

## What I Learned
From this task, I learned that an attack surface and an attack vector are not the same thing.
The attack surface tells us which areas or systems may need security attention, while the attack vector tells us how someone could potentially approach a weakness in those areas.

I also learned that I should not immediately assume that suspicious-looking activity is definitely an attack. For example, repeated failed logins followed by a successful login can be suspicious, but more evidence is needed before saying that an account was compromised.

The main thing I learned is to separate what I can actually see in the logs from what I think might have happened. This helps in making a more accurate security analysis.
