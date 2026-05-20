<h1 align="center">Nmap Cheat Sheet</h1>

<p align="center">
  Fast reference guide for enumeration, scanning and offensive security workflows.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Kali_Linux-111827?style=for-the-badge&logo=kalilinux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/Linux-111827?style=for-the-badge&logo=linux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/Nmap-Recon-111827?style=for-the-badge&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/OffSec-Pentesting-111827?style=for-the-badge&logoColor=FF003C">
  <img src="https://img.shields.io/badge/Type-CheatSheet-111827?style=for-the-badge&logoColor=00FFFF">
</p>

## Deteccion Open Ports TCP and UDP

````markdown
nmap 10.10.19.120 -p- --open -n -Pn -oN AllPorts
```` 

````markdown
nmap 10.10.19.120 -p- --open -n -Pn -T5 -oN AllPorts
````
| Template | Nombre     | Velocidad  | Uso               |
| -------- | ---------- | ---------- | ----------------- |
| `-T0`    | Paranoid   | Muy lento  | IDS evasion       |
| `-T1`    | Sneaky     | Muy lento  | Stealth           |
| `-T2`    | Polite     | Lento      | Redes sensibles   |
| `-T3`    | Normal     | Default    | Balanceado        |
| `-T4`    | Aggressive | Rápido     | HTB / CTF / Labs  |
| `-T5`    | Insane     | Muy rápido | Redes MUY rápidas |


````markdown
nmap 10.10.19.120 -p- --open -n -Pn --min-rate 5000 -oN AllPorts
````

````markdown
nmap 10.10.19.120 -sU -p- --min-rate 5000 -oN AllPorts
````

````markdown
nmap 10.10.19.120 -sU -p- -oN AllPorts
````
## Recon services

````markdown
nmap 10.10.19.120 -p 80,22,8080,3075,4242,3000,21,1038 -sCV -oG Machine01.txt
````
> -sC default script and -sV detec version services

````markdown
nmap 10.10.19.120 -p 80,22,8080,3075,4242,3000,21,1038 -sCV -T4 -oG Machine01.txt
````

````markdown
nmap 10.10.19.120 -p 80,22,8080,3075,4242,3000,21,1038 -sCV --min-rate 5000 -oG Machine01.txt
````

## Dicovery Services

````markdown
nmap --script 'smb-*' -p445 target
````

````markdown
nmap --script 'smb2-*' -p445 target
````

```markdown
nmap --script 'ssl-*' -p443 target
```

````markdown
nmap --script 'ftp-*' -p21 target
````

````markdown
nmap --script 'dns-*' -p53 target
````

````markdown
nmap --script 'snmp-*' -sU -p161 target
````

```markdown
nmap --script 'ssh-*' -p22 target
```

```markdown
nmap --script 'mysql-*' -p3306 target
```

```markdown
nmap --script 'ms-sql-*' -p1433,1434 target
```

```markdown
nmap --script 'imap-*' -p143,993 target
```

```markdown
nmap --script 'pop3-*' -p110,995 target
```

```markdown
nmap --script 'smtp-*' -p25 target
```

## Silent scanning

````markdown
nmap -sS target
````

````markdown
nmap -sS -Pn -n -T1 target
````

````markdown
nmap -sS -Pn -n -p- -T1 target
````

````markdown
nmap -sS --scan-delay 5s target
````

````markdown
nmap -sS -T0 --scan-delay 10s target
````

> ## Null Scan
````markdown
nmap -sN target
````
````markdown
nmap -sN -T1 --scan-delay 5s target
````
````markdown
nmap -sN -f target
````

> ## Fin Scan
````markdown
nmap -sF target
````
````markdown
nmap -sF -T1 --scan-delay 5s target
````
````markdown
nmap -sF -f target
````

> ## Xmas Scan
````markdown
nmap -sX target
````
````markdown
nmap -sX -T1 --scan-delay 5s target
````
````markdown
nmap -sX -f target
````

## Local Network

| Técnica               | Comando                                     | Qué modifica              | Nivel OSI  |
| --------------------- | ------------------------------------------- | ------------------------- | ---------- |
| Decoys                | `nmap -D RND:5 target`                      | Añade IPs falsas          | Capa 3     |
| Decoys personalizados | `nmap -D 1.1.1.1,8.8.8.8,ME target`         | Mezcla IP real con falsas | Capa 3     |
| Source IP spoofing*   | `nmap -S IP target`                         | Falsifica IP origen       | Capa 3     |
| Seleccionar interfaz  | `nmap -e tun0 target`                       | Interfaz origen           | Capa 2/3   |
| Source Port spoof     | `nmap -g 53 target`                         | Puerto TCP/UDP origen     | Capa 4     |
| Source Port largo     | `nmap --source-port 53 target`              | Igual que `-g`            | Capa 4     |
| MAC aleatoria         | `nmap --spoof-mac 0 target`                 | MAC origen random         | Capa 2     |
| MAC Cisco             | `nmap --spoof-mac Cisco target`             | Vendor MAC falso          | Capa 2     |
| MAC personalizada     | `nmap --spoof-mac 00:11:22:33:44:55 target` | MAC específica            | Capa 2     |
| Randomize hosts       | `nmap --randomize-hosts target`             | Orden aleatorio escaneo   | Lógica     |

## Evasion de Firewall
| Técnica                | Comando              | Explicación                                                                                                                                     |
| ---------------------- | -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| Fragmentación básica   | `nmap -f target`     | Divide los paquetes IP en fragmentos pequeños para intentar evadir firewalls/IDS simples que no reensamblan correctamente los paquetes.         |
| Fragmentación agresiva | `nmap -ff target`    | Usa fragmentación más pequeña/agresiva que `-f`, generando más fragmentos TCP/IP y aumentando las posibilidades de evasión en filtros antiguos. |
| SYN + fragmentación    | `nmap -sS -f target` | Combina SYN Stealth Scan con fragmentación. Envía paquetes SYN fragmentados para dificultar la inspección del firewall.                         |
| Xmas + fragmentación   | `nmap -sX -f target` | Realiza un Xmas Scan usando paquetes fragmentados. Busca evadir IDS/firewalls antiguos usando flags TCP anómalas + fragmentación.               |
| FIN + fragmentación    | `nmap -sF -f target` | Ejecuta un FIN Scan con paquetes fragmentados para intentar evitar detección por filtros TCP simples.                                           |

