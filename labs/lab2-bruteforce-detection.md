# Lab 2: Brute Force Detection (SMB)

## Objective
To simulate and detect a brute force attack by generating repeated failed SMB login attempts and analyzing Windows logs.

## Lab Setup
- Windows 11 VM
- Kali Linux VM
- VirtualBox NAT Network

## Tools Used
- smbclient
- Windows Event Viewer

## Scenario
A potential attacker attempts to gain access to a Windows SMB share by repeatedly guessing credentials from a remote machine.

## Steps Taken
1. Initiated multiple SMB login attempts from Kali using incorrect passwords
2. Repeated the process several times to simulate brute force behaviour
3. Monitored Windows Security logs in Event Viewer
4. Identified relevant authentication events

## Commands Used
```bash
smbclient //<windows-ip>/LabShare_Public -U testuser1
```

## Results
- Multiple failed login attempts were generated from the Kali VM  
- Authentication attempts consistently failed due to incorrect credentials  
- Windows logged each failed attempt in the Security log  

## Log Analysis Findings
- Event ID 4625 recorded each failed login attempt  
- Multiple 4625 events occurred within a short timeframe  
- All attempts originated from the same source IP (Kali VM)  
- The same username was targeted repeatedly  

## Key Findings
- Repeated failed login attempts are a strong indicator of brute force activity  
- Windows logs provide clear visibility into authentication failures  
- Patterns in log data (frequency, source IP, targeted account) are critical for detection  

## Blue Team Perspective
- Monitoring failed login attempts is essential for identifying brute force attacks  
- A high number of 4625 events in a short period should trigger investigation  
- Source IP correlation helps identify the attacking system  
- Implementing account lockout policies can mitigate this type of attack  

## Incident Simulation: Brute Force Attempt

### Description
Multiple failed SMB login attempts were generated from a Kali Linux machine targeting a Windows SMB share.

### Evidence
- Event ID 4625 (failed logins)
- Repeated attempts from the same source IP
- Consistent targeting of a single username

### Analysis
The pattern of repeated failed authentication attempts within a short timeframe is consistent with a brute force or credential guessing attack.

### Conclusion
This activity represents suspicious behaviour and should be detected and mitigated using monitoring and security controls in a real environment.

## Next Steps
- Implement account lockout policies
- Explore detection thresholds for failed logins
- Simulate additional attack scenarios
