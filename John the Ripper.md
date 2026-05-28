<h1 align="center">John the Ripper Cheat Sheet</h1>

<p align="center">
  Fast reference guide for password cracking, hash identification, and offline brute-force workflows.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Kali_Linux-111827?style=for-the-badge&logo=kalilinux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/Linux-111827?style=for-the-badge&logo=linux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/John-Cracking-111827?style=for-the-badge&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/OffSec-Passwords-111827?style=for-the-badge&logoColor=FF003C">
  <img src="https://img.shields.io/badge/Type-CheatSheet-111827?style=for-the-badge&logoColor=00FFFF">
</p>

## Singel Mode
> En base a esta informacion: r0lf:$6$ues25dIanlctrWxg$nZHVz2z4kCy1760Ee28M1xtHdGoy0C2cYzZ8l2sVa1kIa8K9gAcdBP.GI6ng/qA4oaMrgElZ1Cb9OeXO4Fvy3/:0:0:Rolf Sebastian:/home/r0lf:/bin/bash

````
john --single passwd
````
```
❯ john --single passwd
Using default input encoding: UTF-8
Loaded 1 password hash (sha512crypt, crypt(3) $6$ [SHA512 128/128 SSE2 2x])
Cost 1 (iteration count) is 5000 for all loaded hashes
Will run 6 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
NAITSABES        (r0lf)     
1g 0:00:00:00 DONE (2026-05-28 21:22) 6.250g/s 2700p/s 2700c/s 2700C/s FL0RR..rSebastiannaitsabeSr
Use the "--show" option to display all of the cracked passwords reliably
Session completed. 
```
## Wordlist Mode
```
john --wordlist=/usr/share/wordlists/rockyou.txt hashes.txt
```

## Incremental mode
> Es un potente método de descifrado de contraseñas por fuerza bruta que genera contraseñas candidatas basándose en un modelo estadístico [Cadenas Markov](https://en.wikipedia.org/wiki/Markov_chain). 

```
john --incremental hash.txt
```
## Unidentified hash
