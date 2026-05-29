<h1 align="center">Enum4linux Cheat Sheet</h1>

<p align="center">
  Fast reference guide for SMB and Samba enumeration, user harvesting, share discovery, and RID cycling workflows.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Kali_Linux-111827?style=for-the-badge&logo=kalilinux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/Linux-111827?style=for-the-badge&logo=linux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/SMB-Enumeration-111827?style=for-the-badge&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/OffSec-Recon-111827?style=for-the-badge&logoColor=FF003C">
  <img src="https://img.shields.io/badge/Type-CheatSheet-111827?style=for-the-badge&logoColor=00FFFF">
</p>

| Flag | Función |
| :--- | :--- |
| **`-a`** | Ejecuta **todos** los escaneos (Recomendado). |
| **`-U`** | Obtiene la lista de **usuarios**. |
| **`-S`** | Lista los **recursos compartidos** (Shares). |
| **`-G`** | Lista los **grupos**. |
| **`-P`** | Muestra la **política de contraseñas**. |
| **`-r`** | Fuerza la enumeración de usuarios mediante **RID**. |
| **`-u <user>`** | Especifica el **usuario** para autenticarse. |
| **`-p <pass>`** | Especifica la **contraseña** para autenticarse. |

```
enum4linux -a 10.10.10.10
```

enum4linux -S 10.10.10.10

enum4linux -U 10.10.10.10

enum4linux -G 10.10.10.10

enum4linux -P 10.10.10.10

enum4linux -o 10.10.10.10

enum4linux -u "guest" -p "" -a 10.10.10.10

enum4linux -r 10.10.10.10

