<h1 align="center">Hashcat Cheat Sheet</h1>

<p align="center">
  Fast reference guide for GPU-accelerated password cracking, rule deployment, and hash recovery.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Kali_Linux-111827?style=for-the-badge&logo=kalilinux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/Linux-111827?style=for-the-badge&logo=linux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/Hashcat-Cracking-111827?style=for-the-badge&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/OffSec-GPU_Cracking-111827?style=for-the-badge&logoColor=FF003C">
  <img src="https://img.shields.io/badge/Type-CheatSheet-111827?style=for-the-badge&logoColor=00FFFF">
</p>

- Previamente siempre debemos identificar el tipo de Hash.

````
  hashid -m '$1$FNr44XZC$wQxY6HHLrgrGX0e1195k.1'
````

```
Analyzing '$1$FNr44XZC$wQxY6HHLrgrGX0e1195k.1'
[+] MD5 Crypt [Hashcat Mode: 500]
[+] Cisco-IOS(MD5) [Hashcat Mode: 500]
[+] FreeBSD MD5 [Hashcat Mode: 500]
```

## Diccionary Attack - Lista de todas la numeraciones -m [aqui](https://hashcat.net/wiki/doku.php?id=example_hashes)
- Cracking Hash MD5
````
hashcat -a 0 -m 0 81dc9bdb52d04dc20036dbd8313ed055 /usr/share/wordlists/rockyou.txt
````

- Cracking Hash NetNTLMv2
```
hashcat -a 0 -m 5600 netntlm2_hash.txt /usr/share/wordlists/rockyou.txt
```

- Cracking Hash Tickets TGS de Kerberos
```
hashcat -a 0 -m 13100 krb_tgs.txt /usr/share/wordlists/rockyou.txt
```

## Based Rule
> Cogera cada una de las palabras de un diccionario y en base a las reglas lo altera.
```
hashcat -a 0 -m 0 1b0556a75770563578569ae21392630c /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/best66.rule 
```
```
hashcat -a 0 -m 0 1b0556a75770563578569ae21392630c /usr/share/wordlists/rockyou.txt -r /usr/share/hashcat/rules/combinator.rule
```
Mas reglas aqui 
```
ls -l /usr/share/hashcat/rules
```
