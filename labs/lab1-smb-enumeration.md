# Lab 1: SMB Enumeration & Access Control

## Objective
To understand how SMB shares are discovered and how access is controlled using different user accounts.

## Lab Setup
- Windows 11 VM
- Kali Linux VM
- VirtualBox NAT Network

## Tools Used
- nmap
- smbclient

## Steps Taken
1. Created two local users, (emmatest, noahtest) 
2. Created shared folders (Public and Private)
3. Configured share and NTFS permissions - Public folder shared to everyone. Private folder only shared to emmatest.
4. Tested access from Kali using smbclient

## Commands Used
```bash
nmap -p 445 <windows-ip>
smbclient -L //<windows-ip> -U emmatest
smbclient //<windows-ip>/LabShare_Public -U emmatest
```
## Results
- emmatest - Full access to both shares
- noahtest - Only access to the public share
- Access denied when attempting private share with restricted user

## Key Findings
- Authentication does not guarantee access (authorization required)
- Both share and NTFS permissions must allow access
- Misconfigured permissions can expose sensitive data
