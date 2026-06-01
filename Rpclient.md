<h1 align="center">RPCclient Cheat Sheet</h1>

<p align="center">
  Advanced reference guide for enumerating Windows environments, user bases, domain policies, and system structures via MS-RPC endpoints.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Kali_Linux-111827?style=for-the-badge&logo=kalilinux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/Active_Directory-111827?style=for-the-badge&logo=microsoft&logoColor=00A4EF">
  <img src="https://img.shields.io/badge/Protocol-MS--RPC-111827?style=for-the-badge&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/OffSec-Internal_Recon-111827?style=for-the-badge&logoColor=FF003C">
  <img src="https://img.shields.io/badge/Type-CheatSheet-111827?style=for-the-badge&logoColor=00FFFF">
</p>

```
rpcclient -U "" 192.168.1.50
```

```
rpcclient -U "miempresa.local\juan.perez%Primavera2026*" 192.168.1.50
```

```
rpcclient -U "Administrator" --hashes "aad3b435b51404eeaad3b435b51404ee:7afe0344c34e0e4745864c235c03c52e" 192.168.1.50
```

```
rpcclient -U "" 192.168.1.50 -c "enumdomusers" | grep "user:"
```

```
for i in $(seq 500 1100);do rpcclient -N -U "" 10.129.14.128 -c "queryuser 0x$(printf '%x\n' $i)" | grep "User Name\|user_rid\|group_rid" && echo "";done
```
> A veces el comando global enumdomusers está capado o bloqueado por el servidor, pero el endpoint queryuser individual sigue respondiendo. Este script "salta" esa restricción barriendo los IDs uno a uno de forma automática.

| Categoría | Comando | Descripción / Utilidad |
| :--- | :--- | :--- |
| **Usuarios** | `enumdomusers` | Lista **todos** los usuarios con su respectivo RID. |
| **Usuarios** | `queryuser <RID>` | Información detallada de un usuario (ej: `queryuser 0x1f4`). |
| **Grupos** | `enumdomgroups` | Lista todos los grupos de seguridad creados. |
| **Grupos** | `querygroup <RID>` | Muestra los detalles y descripción de un grupo específico. |
| **Grupos** | `querygroupmem <RID>` | Muestra qué usuarios (RIDs) pertenecen a ese grupo. |
| **Políticas / Info** | `querydominfo` | Devuelve el nombre del dominio y número total de usuarios. |
| **Políticas / Info** | `getdompwinfo` | Muestra la **política de contraseñas** (longitud, complejidad). |
| **Políticas / Info** | `srvinfo` | Muestra la versión exacta del Sistema Operativo de la máquina. |
| **Traducción / SIDs**| `lookupnames <usuario>` | Traduce el nombre de un usuario a su código SID/RID. |
| **Traducción / SIDs**| `lookupsids <SID>` | Traduce un SID de vuelta al nombre del usuario o grupo. |
| **Recursos** | `netshareenumall` | Lista todos los recursos compartidos (incluidos los ocultos `$`). |
| **Recursos** | `enumprinters` | Lista los controladores e impresoras del sistema. |
