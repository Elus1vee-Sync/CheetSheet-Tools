<h1 align="center">LDAPDomainDump Cheat Sheet</h1>

<p align="center">
  Fast reference guide for Active Directory enumeration, group mapping, password policy extraction, and user harvesting via LDAP queries.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Kali_Linux-111827?style=for-the-badge&logo=kalilinux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/Active_Directory-111827?style=for-the-badge&logo=microsoft&logoColor=00A4EF">
  <img src="https://img.shields.io/badge/LDAP-Recon-111827?style=for-the-badge&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/OffSec-Internal_Attacks-111827?style=for-the-badge&logoColor=FF003C">
  <img src="https://img.shields.io/badge/Type-CheatSheet-111827?style=for-the-badge&logoColor=00FFFF">
</p>

>  Herramienta que vuelca toda la estructura de Active Directory (LDAP) a archivos visuales HTML y JSON. Funciona con cualquier usuario del dominio (no requiere admin).

```
ldapdomaindump -u 'miempresa.local\juan.perez' -p 'Primavera2026*' 192.168.1.10
```

```
ldapdomaindump -u 'miempresa.local\juan.perez' -p 'Primavera2026*' --ldaps 192.168.1.10
```

```
mkdir /tmp/ldap_loot
ldapdomaindump -u 'miempresa.local\juan.perez' -p 'Primavera2026*' -o /tmp/ldap_loot 192.168.1.10
```

