# Day 12 — Web Reconnaissance & Attack Surface Mapping

## 1. Scope and Authorization

**Target:** WebGoat local application

**Authorization / Lab:** Authorized intentionally vulnerable local WebGoat lab

**Scope:** http://webgoat.local:8080/WebGoat

**Out of Scope:** All external systems, public websites, third-party IP addresses, and systems outside the local WebGoat lab.

**Recon Date:** 13 September 2026

**Objective:** Perform reconnaissance and create an attack-surface map without exploiting vulnerabilities.


## 2. Tools Used

- Nmap
- Burp Suite Community Edition
- Web browser
- Browser Developer Tools
- Manual application browsing

Some public/passive tools such as Subfinder, Amass, httpx, WhatWeb and gau were not applicable or were not installed for this local lab.


## 3. Passive Recon

The target is a local WebGoat application running on localhost.

Public-domain reconnaissance such as Certificate Transparency, search-engine discovery and public subdomain enumeration was not applicable because the target is a local authorized lab.

Confirmed local host:
- webgoat.local


## 4. DNS Recon

DNS/public DNS reconnaissance was not applicable to this localhost-based lab.

Observed host:
- webgoat.local
- IP: 127.0.0.1


## 5. Live Host Discovery

The WebGoat application was confirmed to be reachable at:

```text
http://webgoat.local:8080/WebGoat
```
Status: Accessible


## 6. Ports and Services

Nmap service detection identified:

| Port | State | Service | Technology |
|------|-------|---------|------------|
| 8080/tcp | Open | HTTP | Apache Tomcat |

The service is associated with the local WebGoat web application.


## 7. Technology Findings

Observed technology:

- Apache Tomcat
- HTTP
- WebGoat web application
- JSON responses
- MVC-style application routes

Technology identification is an observation and was not treated as proof of a vulnerability.


## 8. Burp Suite Observations

Burp Suite HTTP History was used while browsing the authorized WebGoat application.

Observed:

- GET and POST requests
- /WebGoat/login
- /WebGoat/register
- /WebGoat/start.mvc
- /WebGoat/service/lessonmenu.mvc
- /WebGoat/service/lessoninfo.mvc/
- /WebGoat/service/lessonoverview.mvc/
- /WebGoat/challenge/5
- /WebGoat/challenge/7
- /WebGoat/JWT/votings
- /WebGoat/JWT/votings/login
- /WebGoat/JWT/refresh/login
- /WebGoat/xxe/comments
- /WebGoat/csrf/review

Sensitive values such as passwords and session tokens were excluded from the submission.


## 9. Crawled / Observed Endpoints

Examples of observed application paths:

- /WebGoat/login
- /WebGoat/register
- /WebGoat/start.mvc
- /WebGoat/welcome.mvc
- /WebGoat/service/labels.mvc
- /WebGoat/service/lessonmenu.mvc
- /WebGoat/service/lessoninfo.mvc/
- /WebGoat/service/lessonoverview.mvc/
- /WebGoat/service/hint.mvc
- /WebGoat/challenge/5
- /WebGoat/challenge/7
- /WebGoat/xxe/comments
- /WebGoat/csrf/review


## 10. Historical URLs

Historical URL reconnaissance was not applicable because this exercise targeted a local WebGoat installation rather than a public domain.


## 11. JavaScript / API Findings

Observed JSON/client-side resources included:

- /WebGoat/lesson_js/questions_cia.json
- /WebGoat/lesson_js/questions_jwt.json
- /WebGoat/lesson_js/questions_sql_injection.json
- /WebGoat/lesson_js/questions_cross_site_scripting.json

Observed functional/API-style routes included:

- /WebGoat/JWT/votings
- /WebGoat/JWT/votings/login
- /WebGoat/JWT/refresh/login
- /WebGoat/xxe/comments
- /WebGoat/csrf/review

These were recorded as reconnaissance observations only.


## 12. Parameters

Observed parameter names included:

- username
- username_login
- password_login
- email
- token
- remember

Sensitive parameter values were not included in the submission.


## 13. Content Discovery

Content discovery was limited to the authorized WebGoat application and observed application paths.

No exploitation was performed.


## 14. Attack-Surface Map

The attack-surface map is provided separately as: attack-surface-map.png

It includes the local host, port/service, WebGoat application, authentication routes, application services, lessons/challenges, API-style routes, JSON resources and observed parameters.


## 15. Top 5 Areas to Prioritize

1. Authentication and login functionality
   - Important because authentication controls access to the application.

2. JWT-related endpoints
   - Important because token-based authentication is part of the application attack surface.

3. Application service endpoints
   - Important because multiple MVC/JSON service routes were observed.

4. Challenge and lesson functionality
   - Important because these represent different application functions and input-handling areas.

5. Request parameters and user-controlled inputs
   - Important because parameters such as username, email and other form inputs interact with application functionality.

These are priorities for future authorized testing, not confirmed vulnerabilities.


## 16. Confirmed Facts vs Assumptions

### Confirmed Facts

- WebGoat is running locally.
- webgoat.local resolves/operates through the local environment.
- 8080/tcp is open.
- Apache Tomcat was identified by Nmap.
- Burp HTTP History captured WebGoat requests.
- Multiple application endpoints and parameters were observed.

### Assumptions

- An observed endpoint is not automatically vulnerable.
- Technology identification does not prove a security weakness.
- Historical/public reconnaissance was not applicable to this local target.


## 17. What I Learned

I learned how to perform structured web reconnaissance and organize an application's attack surface.

I practiced identifying ports and services with Nmap, observing HTTP requests with Burp Suite, identifying endpoints and parameters, recognizing API/JSON resources, and organizing the findings into an attack-surface map.

The main reconnaissance workflow I learned was:
```text
Find → Verify → Organize → Understand → Prioritize → Test
```
