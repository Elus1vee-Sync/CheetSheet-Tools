<h1 align="center">Impacket SMBServer Cheat Sheet</h1>

<p align="center">
  Advanced reference guide for spinning up quick, on-the-fly SMB shares to transfer tools, exfiltrate data, and capture NTLMv2 authentication hashes.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Kali_Linux-111827?style=for-the-badge&logo=kalilinux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/Active_Directory-111827?style=for-the-badge&logo=microsoft&logoColor=00A4EF">
  <img src="https://img.shields.io/badge/Impacket-SMBServer-111827?style=for-the-badge&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/OffSec-Exfiltration_--_Hash_Capture-111827?style=for-the-badge&logoColor=FF003C">
  <img src="https://img.shields.io/badge/Type-CheatSheet-111827?style=for-the-badge&logoColor=00FFFF">
</p>


```
impacket-smbserver SMBfolder $(pwd) -smb2support
```

```
impacket-smbserver SMBfolder $(pwd) -smb2support -username pwn -password pwn
```
