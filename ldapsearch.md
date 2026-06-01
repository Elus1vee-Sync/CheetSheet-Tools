<h1 align="center">LDAPSearch Cheat Sheet</h1>

<p align="center">
  Comprehensive reference guide for querying Active Directory via native LDAP administration tools, using advanced search filters and credential techniques.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Kali_Linux-111827?style=for-the-badge&logo=kalilinux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/Active_Directory-111827?style=for-the-badge&logo=microsoft&logoColor=00A4EF">
  <img src="https://img.shields.io/badge/LDAP-Queries-111827?style=for-the-badge&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/OffSec-AD_Exploitation-111827?style=for-the-badge&logoColor=FF003C">
  <img src="https://img.shields.io/badge/Type-CheatSheet-111827?style=for-the-badge&logoColor=00FFFF">
</p>


```
ldapsearch -x -H ldap://192.168.1.10 -D 'juan.perez@miempresa.local' -w 'Primavera2026*' -b "DC=miempresa,DC=local"
```

```
ldapsearch -x -H ldap://192.168.1.10 -D 'juan.perez@miempresa.local' -w 'Primavera2026*' -b "DC=miempresa,DC=local" "(objectClass=user)" sAMAccountName
```
> Extrae todos los usuarios

```
ldapsearch -x -H ldap://192.168.1.10 -D 'juan.perez@miempresa.local' -w 'Primavera2026*' -b "DC=miempresa,DC=local" "(memberOf=CN=Domain Admins,CN=Users,DC=miempresa,DC=local)" sAMAccountName
```
> Muestra todos los miembros del grupo Domain Admins

```
ldapsearch -x -H ldap://192.168.1.10 -D 'juan.perez@miempresa.local' -w 'Primavera2026*' -b "DC=miempresa,DC=local" "(description=*password*)" sAMAccountName description
```
> Muestra las descripciones de los usuarios , para saber el ROL o contraseña

```
ldapsearch -x -H ldap://192.168.1.10 -D 'juan.perez@miempresa.local' -w 'Primavera2026*' -b "DC=miempresa,DC=local" "(objectClass=computer)" name operatingSystem
```
> Inventario de Servidores, PCs y Sistemas operativos

```
ldapsearch -x -H ldap://192.168.1.10 -D 'juan.perez@miempresa.local' -w 'Primavera2026*' -b "DC=miempresa,DC=local" "(userAccountControl:1.2.840.113556.1.4.803:=65536)" sAMAccountName
```
> Usuarios con contraseña que NUMCA expira

```
ldapsearch -x -H ldap://192.168.1.10 -D 'juan.perez@miempresa.local' -w 'Primavera2026*' -b "DC=miempresa,DC=local" "(&(objectClass=user)(servicePrincipalName=*))" sAMAccountName servicePrincipalName
```
> Cuentas vulnerables a Kerberoasting (SPN configurado)

```
ldapsearch -x -H ldap://192.168.1.10 -D 'juan.perez@miempresa.local' -w 'Primavera2026*' -b "DC=miempresa,DC=local" "(userAccountControl:1.2.840.113556.1.4.803:=4194304)" sAMAccountName
```
> Cuentas vulnerables a AS-REP Roasting (Sin preautenticacion de Kerberos)

```
ldapsearch -x -H ldap://192.168.1.10 -D 'juan.perez@miempresa.local' -w 'Primavera2026*' -b "DC=miempresa,DC=local" "(userAccountControl:1.2.840.113556.1.4.803:=524288)" sAMAccountName userAccountControl
```
> Busca delegaciones sin restricciones (Unconstrained Delegation)

```
ldapsearch -x -H ldap://192.168.1.10 -D 'juan.perez@miempresa.local' -w 'Primavera2026*' -b "DC=miempresa,DC=local" "(userAccountControl:1.2.840.113556.1.4.803:=2)" sAMAccountName
```
> Cuentas deshabilitadas pero activas en la red

## Search delegation

```
ldapsearch -x -H ldap://192.168.1.10 -D 'juan.perez@miempresa.local' -w 'Primavera2026*' -b "DC=miempresa,DC=local" "(msDS-AllowedToActOnBehalfOfOtherIdentity=*)" sAMAccountName msDS-AllowedToActOnBehalfOfOtherIdentity
```
> Buscar Delegación Restringida basada en Recursos (RBCD)

```
ldapsearch -x -H ldap://192.168.1.10 -D 'juan.perez@miempresa.local' -w 'Primavera2026*' -b "DC=miempresa,DC=local" "(msDS-AllowedToDelegateTo=*)" sAMAccountName msDS-AllowedToDelegateTo
```
> Buscar Delegación Restringida Clásica (Constrained Delegation)

```
ldapsearch -x -H ldap://192.168.1.10 -D 'juan.perez@miempresa.local' -w 'Primavera2026*' -b "OU=Domain Controllers,DC=miempresa,DC=local" "(objectClass=computer)" name
```
> Listar todos los Controladores de Dominio (DCs)

```
ldapsearch -x -H ldap://192.168.1.10 -D 'juan.perez@miempresa.local' -w 'Primavera2026*' -b "DC=miempresa,DC=local" "(&(objectClass=computer)(|(operatingSystem=*2008*)(operatingSystem=*2012*)(operatingSystem=*Windows 7*)))" name operatingSystem
```
> Localizar Sistemas Operativos obsoletos (Legacy) de forma rápida
