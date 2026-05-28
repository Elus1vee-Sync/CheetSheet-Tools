<h1 align="center">Metasploit Framework Cheat Sheet</h1>

<p align="center">
  Fast reference guide for exploit execution, auxiliary scanning, payload deployment, and session post-exploitation.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Kali_Linux-111827?style=for-the-badge&logo=kalilinux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/Linux-111827?style=for-the-badge&logo=linux&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/Metasploit-Exploitation-111827?style=for-the-badge&logoColor=00BFFF">
  <img src="https://img.shields.io/badge/Rapid7-Framework-111827?style=for-the-badge&logoColor=FF003C">
  <img src="https://img.shields.io/badge/Type-CheatSheet-111827?style=for-the-badge&logoColor=00FFFF">
</p>

## Status services
| Command | Description |
| :--- | :--- |
| `msfconsole` | Launch the Metasploit Framework console. |
| `msfconsole -q` | Launch quietly (suppress the banner and startup logs). |
| `msfdb init` | Initialize the Metasploit PostgreSQL database. |
| `db_status` | Check the current database connection status. |
| `workspace -a <name>` | Create a new isolated project workspace. |

## Movent interface
| Command | Description |
| :--- | :--- |
| `search <exploit/cve/name>` | Search for modules, exploits, or scanners. |
| `use <path/to/module>` | Select and load a specific module. |
| `info` | Show details, targets, references, and options for the loaded module. |
| `show options` | Display the required and optional parameters for the module. |
| `set <VARIABLE> <value>` | Define a module variable (e.g., `set RHOSTS 10.10.10.5`). |
| `setg <VARIABLE> <value>` | Define a variable globally across all modules in the session. |
| `unset <VARIABLE>` | Clear a specific variable value. |
| `exploit` or `run` | Execute the loaded module. |
| `back` | Exit the current module context and return to global prompt. |
