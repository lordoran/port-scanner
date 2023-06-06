# SCANNING & FUZZING PROCEDURE
# WORDLISTS https://github.com/danielmiessler/SecLists
# 1.URL

## Initial Port Scanning:

I use Masscan to get an overview of open ports:

` masscan <website URL> -p1-65535 --rate <scan rate>`

For a detailed port scanning I'll feed the open ports into Nmap for more comprehensive scanning and service detection:

`nmap -p <open ports> -A <website URL>`

## Alternatively, I can use RustScan as a faster and more convenient replacement for Masscan and Nmap:

`rustscan -a <website URL>`


## Fuzzing Endpoints:
### FFUF or FIRBUSTER
Use ffuf or DirBuster to fuzz endpoints and discover hidden or vulnerable directories:

`ffuf -w <wordlist.txt> -u <URL>/FUZZ -mc all`

`gobuster dir -u <URL> -w <wordlist.txt> -x .php,.html`

### 2. BURPSUITE 
Launch Burp Suite: Start Burp Suite and ensure that your browser is configured to proxy through Burp.

Configure the Target: In Burp Suite, go to the "Target" tab and provide the URL of the application or endpoint you want to fuzz. You can also specify any necessary headers or cookies.

Open the Intruder Module: Go to the "Intruder" tab in Burp Suite.

Define the Payloads: In the "Intruder" tab, switch to the "Positions" sub-tab. Here, select the positions in the request that you want to fuzz, such as input fields, parameters, or headers.

Customize the Payloads: Move to the "Payloads" sub-tab. You can now define the payloads that will be sent during the fuzzing process. Burp Suite provides several payload types, such as lists, character sets, and payload generators.

Configure Fuzzing Options: In the "Options" sub-tab, you can customize various fuzzing options, such as the number of threads, delays between requests, and response handling.

Start the Fuzzing Attack: Once you have configured the payloads and options, switch to the "Attack" sub-tab and click on the "Start attack" button to initiate the fuzzing attack.

Analyze the Results: Burp Suite will start sending the specified payloads to the targeted positions in the request. Monitor the responses for any unexpected behavior, crashes, error messages, or other indications of potential vulnerabilities.

Refine and Iterate: Based on the results, you can refine your payloads, fuzzing options, and targeted positions to focus on potential areas of weakness and conduct further testing.


## Subdomain Enumeration:
Tools: Subfinder, Amass, Assetnote, Chaos, Aquatone, Sublist3r
### Subfinder:

Advantages:Fast and efficient subdomain enumeration.
Integration with multiple APIs for increased coverage.
Simple command-line interface for ease of use.

Disadvantages:Limited to subdomain enumeration and doesn't offer other reconnaissance features.
Relies on external APIs, which may have limitations or require API keys.
### Amass:

Advantages:Comprehensive subdomain enumeration, including recursive brute-forcing and scraping.
Integration with various data sources for wider coverage.
Active development and frequent updates.

Disadvantages:Can be resource-intensive and slower compared to other tools.
May generate a large number of false positives that require manual verification.
### Assetnote:

Advantages:
Focused on asset discovery, including subdomains, IP ranges, and other Internet-exposed assets.
Uses a combination of active and passive techniques for data collection.
Provides a web-based interface for easier management and collaboration.
Disadvantages:
Requires a subscription and is not available for free.
May have limited coverage or data sources compared to some other tools.
### Chaos:

Advantages:
Specifically designed for chaos engineering, focusing on DNS and other infrastructure testing.
Provides various DNS-related functionalities, including DNS resolution, zone transfers, and more.
Offers a simple command-line interface and is well-documented.
Disadvantages:
Primarily focused on DNS-related testing and may not cover other aspects of reconnaissance.
May have a steeper learning curve for users not familiar with DNS internals.
### Aquatone:

Advantages:
Useful for visual reconnaissance and capturing screenshots of discovered web assets.
Supports batch processing for efficiency.
Provides basic analysis and reporting features.
Disadvantages:
Limited to web assets and doesn't offer subdomain enumeration or other asset discovery capabilities.
May generate false negatives if the target assets are not accessible or configured to block automated scanning.

## Subdomain Enumeration:

Use Subfinder, Amass, Assetnote, Chaos, or Aquatone to enumerate subdomains:

`
subfinder -d <domain> -o <output.txt>`


`amass enum -d <domain> -o <output.txt>`


`assetnote -u <domain> -o <output.txt>`

`chaos -d <domain> -o <output.txt>`


`aquatone-discover -d <domain> -o <output.txt>`



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

`gobuster dir -u <URL> -w <wordlist.txt> -x .php,.html`

`dirsearch -u <URL> -w <wordlist.txt> -e .php,.html`

`gobuster dir -u <URL> -w <wordlist.txt> -x .php,.html`

# IP

