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
nmap 10.10.19.120 -sU -p- --min-rate 5000 -oG AllPorts
````

````markdown
nmap 10.10.19.120 -sU -p- -oG AllPorts
````
## Discovery services
