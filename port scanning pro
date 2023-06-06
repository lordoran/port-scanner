#port scanning procedure#

Tools: Masscan, Nmap, RustScan, Nessus

## Initial Port Scanning:

I use Masscan to get an overview of open ports:
 masscan <website URL> -p1-65535 --rate <scan rate>

for a detailed port scanning I'll feed the open ports into Nmap for more comprehensive scanning and service detection:
nmap -p <open ports> -A <website URL>

#Alternatively, I can use RustScan as a faster and more convenient replacement for Masscan and Nmap:
rustscan -a <website URL>


Fuzzing Endpoints:
Use ffuf or DirBuster to fuzz endpoints and discover hidden or vulnerable directories:

ffuf -w <wordlist.txt> -u <URL>/FUZZ -mc all
gobuster dir -u <URL> -w <wordlist.txt> -x .php,.html

## Subdomain Enumeration:
Tools: Subfinder, Amass, Assetnote, Chaos, Aquatone, Sublist3r

Subdomain Enumeration:

Use Subfinder, Amass, Assetnote, Chaos, or Aquatone to enumerate subdomains:
php
Copy code
subfinder -d <domain> -o <output.txt>
amass enum -d <domain> -o <output.txt>
assetnote -u <domain> -o <output.txt>
chaos -d <domain> -o <output.txt>
aquatone-discover -d <domain> -o <output.txt>
TLD Enumeration:

Use dnstwist to enumerate TLD variations:

css
Copy code
dnstwist --registered <domain>
Use sublist3r to enumerate subdomains with TLD variations:

php
Copy code
sublist3r -d <domain> -t 100 -o <output.txt>
Parameter Fuzzing:
Tools: Burp Suite, OWASP ZAP, wfuzz, Intruder

Fuzzing Parameters:
Use Burp Suite or OWASP ZAP for manual parameter fuzzing.

Use wfuzz or Burp Suite's Intruder to perform additional parameter fuzzing:

php
Copy code
wfuzz -c -z file,<wordlist.txt> --hc 404 <URL>?FUZZ=test
File Discovery:
Tools: Gobuster, Dirsearch, DirBuster

File and Directory Discovery:
Use Gobuster, Dirsearch, or DirBuster to discover files and directories:
php
Copy code
gobuster dir -u <URL> -w <wordlist.txt> -x .php,.html
dirsearch -u <URL> -w <wordlist.txt> -e .php,.html
gobuster dir -u <URL> -w <wordlist.txt> -x .php,.html
By incorporating these additional tools and techniques into your procedure, you can conduct a more sophisticated and thorough assessment of the target website or network. Remember to always ensure you have proper
