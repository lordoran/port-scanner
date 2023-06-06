# SCANNING & FUZZING PROCEDURE
# WORDLISTS https://github.com/danielmiessler/SecLists

## Initial Port Scanning:

I use Masscan to get an overview of open ports:

` masscan <website URL> -p1-65535 --rate <scan rate>`

For a detailed port scanning I'll feed the open ports into Nmap for more comprehensive scanning and service detection:

`nmap -p <open ports> -A <website URL>`

## Alternatively, I can use RustScan as a faster and more convenient replacement for Masscan and Nmap:
`rustscan -a <website URL>`


## Fuzzing Endpoints:
Use ffuf or DirBuster to fuzz endpoints and discover hidden or vulnerable directories:

`ffuf -w <wordlist.txt> -u <URL>/FUZZ -mc all
gobuster dir -u <URL> -w <wordlist.txt> -x .php,.html`


## Subdomain Enumeration:
Tools: Subfinder, Amass, Assetnote, Chaos, Aquatone, Sublist3r

Subdomain Enumeration:

Use Subfinder, Amass, Assetnote, Chaos, or Aquatone to enumerate subdomains:
`subfinder -d <domain> -o <output.txt>
amass enum -d <domain> -o <output.txt>
assetnote -u <domain> -o <output.txt>
chaos -d <domain> -o <output.txt>
aquatone-discover -d <domain> -o <output.txt>`

TLD Enumeration:
Use dnstwist to enumerate TLD variations:
`dnstwist --registered <domain>`
 
Use sublist3r to enumerate subdomains with TLD variations:
`sublist3r -d <domain> -t 100 -o <output.txt>`

## Fuzzing Parameters:
Use Burp Suite or OWASP ZAP for manual parameter fuzzing
`wfuzz -c -z file,<wordlist.txt> --hc 404 <URL>?FUZZ=test`
 
## File and Directory Discovery:
Gobuster, Dirsearch, or DirBuster to discover files and directories:
`gobuster dir -u <URL> -w <wordlist.txt> -x .php,.html
dirsearch -u <URL> -w <wordlist.txt> -e .php,.html
gobuster dir -u <URL> -w <wordlist.txt> -x .php,.html`

