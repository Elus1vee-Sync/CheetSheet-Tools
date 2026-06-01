<h1 align="center">Smbclient Cheat Sheet</h1>

<p align="center">
  Fast reference guide for SMB network share enumeration, anonymous null sessions, file transfers, and interactive shell navigation.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Kali_Linux-111827?style=for-the-badge&logo=kalilinux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/Linux-111827?style=for-the-badge&logo=linux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/SMB-Shares-111827?style=for-the-badge&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/OffSec-Recon-111827?style=for-the-badge&logoColor=FF003C">
  <img src="https://img.shields.io/badge/Type-CheatSheet-111827?style=for-the-badge&logoColor=00FFFF">
</p>


## Enumeración por Sesión Nula (Sin credenciales)
```
smbclient -L //10.129.14.128/ -N
```

## Enumeración con credenciales locales de la máquina
```
smbclient -L //10.129.14.128/ -U "Administrator%ClaveLocal123!"
```

## Enumeración con credenciales del Dominio (Active Directory)
```
smbclient -L //10.129.14.128/ -U "miempresa.local\juan.perez%Primavera2026*"
``` 

| Comando | Descripción / Acción |
| :--- | :--- |
| `ls` o `dir` | Lista los archivos y carpetas del directorio actual. |
| `cd <carpeta>` | Cambia de directorio dentro del servidor remoto. |
| `pwd` | Muestra la ruta actual en la que estás dentro del servidor. |
| `get <archivo>` | **Descarga** un archivo del servidor a tu máquina local. |
| `put <archivo>` | **Sube** un archivo de tu máquina local al servidor. |
| `mkdir <nombre>` | Crea una carpeta nueva en el servidor remoto. |
| `rm <archivo>` | Elimina un archivo del servidor remoto. |
| `exit` o `quit` | Cierra la sesión y sale de `smbclient`. |
