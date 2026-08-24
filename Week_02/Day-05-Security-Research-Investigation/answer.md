# Day 05 — Security Research Investigation

## Topic
How DNS Works from a Security Perspective

## What Is It?
DNS stands for Domain Name System. It is like the phonebook of the internet. When we type a website name such as google.com, our computer needs to find the IP address of the server where that website is hosted. DNS helps convert the easy to remember domain name into an IP address.

## Why Is It Relevant to Cybersecurity?
DNS is an important part of internet communication, so attackers can also abuse it. If DNS is manipulated or compromised, a user may be redirected to a fake or malicious website even when they enter the correct domain name.
DNS security is important because it can help researchers understand how users are redirected to websites, how attackers can manipulate DNS requests, how malicious domains can be used in attacks, how DNS can be monitored to detect suspicious activity

## How It Works
When a user enters a domain name into a browser, a DNS lookup normally happens to find the IP address.
1. The user enters a domain name, such as google.com
2. The computer checks whether the DNS information is already stored in its cache.
3. It is not available, a DNS resolver is contacted.
4. The resolver finds the required DNS information.
5. The IP address is returned to the computer.
6. The browser uses that IP address to connect to the website.

## Security Risks/Concerns
### 1. DNS Spoofing
   An attacker may provide false DNS information so that a user is redirected to an incorrect or malicious IP address.
### 2. DNS Cache Poisoning
   False DNS information can be inserted into a DNS cache. This can cause users to be redirected to the wrong destination.
### 3. DNS Hijacking
   If an attacker gains control over DNS settings, they may redirect traffic to malicious websites.

## Interesting Observation
One interesting thing I learned is that DNS is not just about converting a website name into an IP address. Because DNS requests happen whenever devices communicate with internet services, DNS traffic can also provide useful security information. Security teams can look for unusual domain names, unexpected DNS requests, or repeated requests to suspicious domains.
DNS is useful for detecting suspicious activity.

## What I Would Investigate Next
1. How DNS cache poisoning attacks happen in real-world scenarios?
2. How can I capture and analyze DNS traffic?
3. How DNS Spoofing can be detected?
4. Which security tools are used to monitor DNS traffic for suspicious domains?

## References
1. Cloudflare - https://www.cloudflare.com/learning/dns/what-is-dns/
2. IBM - Domain Name System (DNS) - https://www.ibm.com/think/topics/dns
3. Center For Cybersecurity Policy and Law - https://www.centerforcybersecuritypolicy.org/insights-and-research/what-is-dns---a-dns-security-primer

## What I Learned
I learned from this research that DNS is an important part of how the internet works. It converts domain names into IP addresses and helps devices find the correct servers.
I also learned that DNS can have security risks such as spoofing, cache poisoning, hijacking, malicious domains, and DNS tunneling. The main thing I learned from this task is that DNS is not only a networking concept but also an important part of cybersecurity. Researching DNS helped me understand why security researchers monitor DNS activity and verify suspicious domains.
