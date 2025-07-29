# Cybersecurity Home Lab

## Objective and purpose
Build a safe, isolated environment to practice cybersecurity skills particularly malware analysis and forensic investigation without risking harm to the host system or network.
Created a malware on kali linux (describe what basic malware it was and what it will do) and ran it on my windows vm. I then ran some command prompts on the infected windows vm machine from the Attacker machine (kali linux) and analzyed what my malware (Resume.pdf.exe) did on the Windows VM.

## Skills Learned
- Malware behavior analysis  
- Snapshot-based rollback and system restoration    
- Host-level forensics  

### Tools that were used
- Kali Linux (Attacker Machine)
- Splunk (SIEM)
- Virtual Box (Hypervisor)
- Windows VM (Test Machine)
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







4. Analyzing what the malware did (Splunk)



Parent Image Resume.pdf.exe spawned cmd.exe which then ran net user, net localgroup and ipconfig.
<img width="865" height="530" alt="Screenshot 6" src="https://github.com/user-attachments/assets/3474b1ca-baa3-4982-89e0-ccd8c57bb796" />




drag & drop screenshots here or use imgur and reference them using imgsrc

Every screenshot should have some text explaining what the screenshot is about.

Example below.

*Ref 1: Network Diagram*
