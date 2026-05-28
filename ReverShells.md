<h1 align="center">Reverse Shells Cheat Sheet</h1>

<p align="center">
  Fast reference guide for instant reverse shells, multi-language payloads, listeners, and TTY upgrading workflows.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Kali_Linux-111827?style=for-the-badge&logo=kalilinux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/Linux-111827?style=for-the-badge&logo=linux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/Shells-Access-111827?style=for-the-badge&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/OffSec-Exploitation-111827?style=for-the-badge&logoColor=FF003C">
  <img src="https://img.shields.io/badge/Type-CheatSheet-111827?style=for-the-badge&logoColor=00FFFF">
</p>

---

## 🎣 Catching Listeners

Before executing any payload, establish a listener on your local machine.

### Netcat (Standard)
```bash
nc -lvnp <PORT>
