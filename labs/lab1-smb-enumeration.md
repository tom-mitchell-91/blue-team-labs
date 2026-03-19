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
1. Created two users (emmatest, noahtest) 
2. Created shared folders (Public and Private)
3. Configured share and NTFS permissions
4. Tested access from Kali using smbclient

## Commands Used
```bash
nmap -p 445 <windows-ip>
smbclient -L //<windows-ip> -U emmatest
smbclient //<windows-ip>/LabShare_Public -U emmatest
