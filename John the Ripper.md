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
> Hay en ocasiones que no es capaz de indetificar el tipo de Hash , entonces tenemos que probar 1 a 1 e indicarselos manualmente.
 hashid -j 193069ceb0461e1d40d216e32c79c704

```
> Analyzing '193069ceb0461e1d40d216e32c79c704'
[+] MD2 [JtR Format: md2]
[+] MD5 [JtR Format: raw-md5]
[+] MD4 [JtR Format: raw-md4]
[+] Double MD5 
[+] LM [JtR Format: lm]
[+] RIPEMD-128 [JtR Format: ripemd-128]
[+] Haval-128 [JtR Format: haval-128-4]
```
### Table formats
```
john --format=zip --wordlist=/usr/share/wordlists/rockyou.txt hash_zip.txt
```
| Hash Format | Example Command | Description |
| :--- | :--- | :--- |
| **`zip`** | `john --format=zip hashes.txt` | ZIP (WinZip) password hashes |
| **`afs`** | `john --format=afs hashes.txt` | AFS (Andrew File System) password hashes |
| **`bfegg`** | `john --format=bfegg hashes.txt` | bfegg hashes used in Eggdrop IRC bots |
| **`bf`** | `john --format=bf hashes.txt` | Blowfish-based crypt(3) hashes |
| **`bsdi`** | `john --format=bsdi hashes.txt` | BSDi crypt(3) hashes |
| **`crypt(3)`** | `john --format=crypt hashes.txt` | Traditional Unix crypt(3) hashes |
| **`des`** | `john --format=des hashes.txt` | Traditional DES-based crypt(3) hashes |
| **`dmd5`** | `john --format=dmd5 hashes.txt` | DMD5 (Dragonfly BSD MD5) password hashes |
| **`dominosec`** | `john --format=dominosec hashes.txt` | IBM Lotus Domino 6/7 password hashes |
| **`episerver`** | `john --format=episerver hashes.txt` | EPiServer SID (Security Identifier) password hashes |
| **`hdaas`** | `john --format=hdaa hashes.txt` | hdaa password hashes used in Openwall GNU/Linux |
| **`hmac-md5`** | `john --format=hmac-md5 hashes.txt` | hmac-md5 password hashes |
| **`hmailserver`** | `john --format=hmailserver hashes.txt` | hmailserver password hashes |
| **`ipb2`** | `john --format=ipb2 hashes.txt` | Invision Power Board 2 password hashes |
| **`krb4`** | `john --format=krb4 hashes.txt` | Kerberos 4 password hashes |
| **`krb5`** | `john --format=krb5 hashes.txt` | Kerberos 5 password hashes |
| **`LM`** | `john --format=LM hashes.txt` | LM (Lan Manager) password hashes |
| **`lotus5`** | `john --format=lotus5 hashes.txt` | Lotus Notes/Domino 5 password hashes |
| **`mscash`** | `john --format=mscash hashes.txt` | MS Cache password hashes |
| **`mscash2`** | `john --format=mscash2 hashes.txt` | MS Cache v2 password hashes |
| **`mschapv2`** | `john --format=mschapv2 hashes.txt` | MS CHAP v2 password hashes |
| **`mskrb5`** | `john --format=mskrb5 hashes.txt` | MS Kerberos 5 password hashes |
| **`mssql05`** | `john --format=mssql05 hashes.txt` | MS SQL 2005 password hashes |
| **`mssql`** | `john --format=mssql hashes.txt` | MS SQL password hashes |
| **`mysql-fast`** | `john --format=mysql-fast hashes.txt` | MySQL fast password hashes |
| **`mysql`** | `john --format=mysql hashes.txt` | MySQL password hashes |
| **`mysql-sha1`** | `john --format=mysql-sha1 hashes.txt` | MySQL SHA1 password hashes |
| **`NETLM`** | `john --format=netlm hashes.txt` | NETLM (NT LAN Manager) password hashes |
| **`NETLMv2`** | `john --format=netlmv2 hashes.txt` | NETLMv2 (NT LAN Manager version 2) password hashes |
| **`NETNTLM`** | `john --format=netntlm hashes.txt` | NETNTLM (NT LAN Manager) password hashes |
| **`NETNTLMv2`** | `john --format=netntlmv2 hashes.txt` | NETNTLMv2 (NT LAN Manager version 2) password hashes |
| **`NEThalfLM`** | `john --format=nethalflm hashes.txt` | NEThalfLM (NT LAN Manager) password hashes |
| **`md5ns`** | `john --format=md5ns hashes.txt` | md5ns (MD5 namespace) password hashes |
| **`nsldap`** | `john --format=nsldap hashes.txt` | nsldap (OpenLDAP SHA) password hashes |
| **`ssha`** | `john --format=ssha hashes.txt` | ssha (Salted SHA) password hashes |
| **`NT`** | `john --format=nt hashes.txt` | NT (Windows NT) password hashes |
| **`openssha`** | `john --format=openssha hashes.txt` | OPENSSH private key password hashes |
| **`oracle11`** | `john --format=oracle11 hashes.txt` | Oracle 11 password hashes |
| **`oracle`** | `john --format=oracle hashes.txt` | Oracle password hashes |
| **`pdf`** | `john --format=pdf hashes.txt` | PDF (Portable Document Format) password hashes |
| **`phpass-md5`** | `john --format=phpass-md5 hashes.txt` | PHPass-MD5 (Portable PHP password hashing framework) password hashes |
| **`phps`** | `john --format=phps hashes.txt` | PHPS password hashes |
| **`pix-md5`** | `john --format=pix-md5 hashes.txt` | Cisco PIX MD5 password hashes |
| **`po`** | `john --format=po hashes.txt` | Po (Sybase SQL Anywhere) password hashes |
| **`rar`** | `john --format=rar hashes.txt` | RAR (WinRAR) password hashes |
| **`raw-md4`** | `john --format=raw-md4 hashes.txt` | Raw MD4 password hashes |
| **`raw-md5`** | `john --format=raw-md5 hashes.txt` | Raw MD5 password hashes |
| **`raw-md5-unicode`** | `john --format=raw-md5-unicode hashes.txt` | Raw MD5 Unicode password hashes |
| **`raw-sha1`** | `john --format=raw-sha1 hashes.txt` | Raw SHA1 password hashes |
| **`raw-sha224`** | `john --format=raw-sha224 hashes.txt` | Raw SHA224 password hashes |
| **`raw-sha256`** | `john --format=raw-sha256 hashes.txt` | Raw SHA256 password hashes |
| **`raw-sha384`** | `john --format=raw-sha384 hashes.txt` | Raw SHA384 password hashes |
| **`raw-sha512`** | `john --format=raw-sha512 hashes.txt` | Raw SHA512 password hashes |
| **`salted-sha`** | `john --format=salted-sha hashes.txt` | Salted SHA password hashes |
| **`sapb`** | `john --format=sapb hashes.txt` | SAP CODVN B (BCODE) password hashes |
| **`sapg`** | `john --format=sapg hashes.txt` | SAP CODVN G (PASSCODE) password hashes |
| **`sha1-gen`** | `john --format=sha1-gen hashes.txt` | Generic SHA1 password hashes |
| **`skey`** | `john --format=skey hashes.txt` | S/Key (One-time password) hashes |
| **`ssh`** | `john --format=ssh hashes.txt` | SSH (Secure Shell) password hashes |
| **`sybasease`** | `john --format=sybasease hashes.txt` | Sybase ASE password hashes |
| **`xsha`** | `john --format=xsha hashes.txt` | xsha (Extended SHA) password hashes |

