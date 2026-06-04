<h1 align="center">Gobuster Cheat Sheet</h1>

<p align="center">
  Fast reference guide for directory, file, DNS, and vhost enumeration during security assessments.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Kali_Linux-111827?style=for-the-badge&logo=kalilinux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/Linux-111827?style=for-the-badge&logo=linux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/Gobuster-Enumeration-111827?style=for-the-badge&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/OffSec-Recon-111827?style=for-the-badge&logoColor=FF003C">
  <img src="https://img.shields.io/badge/Type-CheatSheet-111827?style=for-the-badge&logoColor=00FFFF">
</p>

```
gobuster dir -u http://10.10.10.15 -w /usr/share/wordlists/dirb/common.txt
```

```
gobuster dir -u http://10.10.10.15 -w /usr/share/wordlists/dirb/common.txt -x php,html,txt
```

```
gobuster dir -u http://10.10.10.15 -w /usr/share/wordlists/dirb/common.txt -b 403,404
```

```
gobuster dir -u http://10.10.10.15 -w /usr/share/wordlists/dirb/common.txt -s 200,301
```

```
gobuster dir -u http://10.10.10.15 -w /usr/share/wordlists/dirb/common.txt -U admin -P password123
```

## Search subdomain
```
gobuster dns -d mi-objetivo.com -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt
```

```
gobuster dns -d mi-objetivo.com -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt -i
```

```
gobuster dns -d mi-objetivo.com -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt --quiet
```

## Virtualhosting
```
gobuster vhost -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt --url http://mi-objetivo.com
```

| Parámetro / Bandera | Descripción | Ejemplo de Uso |
| :--- | :--- | :--- |
| `-t, --threads` | Define el número de hilos concurrentes (Por defecto: 10). | `-t 50` |
| `-o, --output` | Guarda todos los resultados en un archivo de texto limpio. | `-o reporte.txt` |
| `-k, --no-tls-validation` | Salta la verificación de certificados SSL/TLS (entornos locales/CTF). | `-k` |
| `-v, --verbose` | Modo detallado (muestra incluso los intentos fallidos y errores). | `-v` |
| `--quiet` | Modo silencioso (solo imprime en pantalla los aciertos positivos). | `--quiet` |
| `--delay` | Tiempo de espera fijo entre peticiones para evadir detecciones. | `--delay 500ms` |
