<h1 align="center">Chisel Cheat Sheet</h1>

<p align="center">
  Fast reference guide for network pivoting, port forwarding, and reverse SOCKS tunnels encapsulation over HTTP.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Kali_Linux-111827?style=for-the-badge&logo=kalilinux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/Linux-111827?style=for-the-badge&logo=linux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/Chisel-Pivoting-111827?style=for-the-badge&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/OffSec-Networks-111827?style=for-the-badge&logoColor=FF003C">
  <img src="https://img.shields.io/badge/Type-CheatSheet-111827?style=for-the-badge&logoColor=00FFFF">
</p>

## Chisel es un único archivo ejecutable que funciona en dos modos:

  > Server (El que recibe): Se ejecuta en la máquina que va a escuchar las conexiones.
<br>

  > Client (El que inicia): Se ejecuta en la máquina que se conecta al servidor y define qué puertos quiere tunelizar.

```
chisel server --port 8000 --reverse
```
<a>o</a>
```
chisel server --port 8000 --reverse --tls-key clave.key --tls-cert certificado.crt
```
## Local Port Forwarding
```
chisel client 10.10.10.5:8000 8001:192.168.1.50:3306
```
> Recuerda 10.10.10.5 es la maquina objetivo. Resultado: Ahora, si vas al puerto 8001 de tu propia máquina (localhost:8001), estarás hablando directamente con el puerto 3306 de la máquina interna oculta.

## Remote Port Forwarding
