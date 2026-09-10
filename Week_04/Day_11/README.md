# Day 11 — Security Header and Web Configuration Review

## 1. Research Topic
Security Header and Web Configuration Review of an Authorized WebGoat Lab.
I selected Web Security and focused on understanding and reviewing HTTP security headers returned by the WebGoat application.


## 2. Background
HTTP headers are additional information sent between a browser and a web server.
Some headers are used for security. They can give the browser instructions about how it should handle web content.
Examples include Content-Security-Policy, X-Content-Type-Options, X-Frame-Options, Strict-Transport-Security, and Referrer-Policy.
Security headers are important because they can provide additional protection against attacks such as cross-site scripting, clickjacking, MIME-type sniffing, and insecure HTTP communication.
For this investigation, I used WebGoat locally as an intentionally vulnerable training application.


## 3. Research Question
What security-related HTTP response headers are returned by the WebGoat application, and what security controls do those headers provide?


## 4. Objective
The objective of this investigation was to:
- Run WebGoat in an authorized local environment.
- Observe normal HTTP communication with the application.
- Inspect HTTP response headers.
- Identify security-related headers.
- Understand what the headers are designed to protect against.
- Record observations and evidence without performing unauthorized testing.


## 5. Environment / Target
Target:
OWASP WebGoat running locally in a Docker container.
Environment:
- Operating System: Windows
- Docker Desktop
- WebGoat Docker image
- Browser: Google Chrome
- Chrome Developer Tools
- Command Prompt
- curl

The application was accessed through: `http://localhost:8080/WebGoat`
The testing was limited to the local WebGoat training environment.


## 6. Current Knowledge
Before starting the investigation, I understood that HTTP requests and responses contain headers.
I also understood that security headers are used to provide additional browser-side security controls.
I knew the basic purpose of several headers:
- Content-Security-Policy helps control allowed content and script sources.
- X-Content-Type-Options helps prevent MIME-type sniffing.
- X-Frame-Options controls framing of a webpage.
- Strict-Transport-Security helps enforce HTTPS.
- Referrer-Policy controls referrer information sent by the browser.

During the practical work, I wanted to understand how these headers actually appear in a real HTTP response.


## 7. Assumptions
The following were assumptions made before or during the investigation:
- WebGoat is an intentionally vulnerable application designed for security training.
- The local WebGoat instance is authorized for testing.
- The application is running only in my controlled lab environment.
- Security headers may differ between different application responses or endpoints.
- The absence of a security header does not automatically mean that a vulnerability exists.
- HSTS is mainly relevant when an application is served over HTTPS.

These assumptions were kept separate from confirmed observations.


## 8. Investigation Steps
### Step 1 — Verify Docker

I checked whether Docker was installed and running.

```cmd
docker --version
docker info
```
### Step 2 — Download the WebGoat image
```cmd 
docker pull webgoat/webgoat
```

This downloaded the WebGoat Docker image.

### Step 3 — Check the downloaded image
```cmd
docker images
```

This confirmed that the WebGoat image was available locally.

### Step 4 — Start the existing WebGoat container
```cmd
docker start webgoat
```

The existing WebGoat container was started instead of creating another container.

### Step 5 — Verify the running container
```cmd
docker ps
```

This confirmed that the WebGoat container was running and that port 8080 was mapped.

### Step 6 — Check HTTP behavior using curl
```cmd
curl -I http://localhost:8080/WebGoat
```

The response returned an HTTP 302 redirect.

I also used:

```cmd 
curl -I http://localhost:8080/WebGoat/
```

and observed the application's response and redirect behavior.

### Step 7 — Inspect browser traffic

I opened WebGoat in Chrome and used:
```text
Chrome Developer Tools → Network
```
I observed requests such as login and application page requests.

### Step 8 — Inspect response headers

I selected WebGoat requests and opened:
```text
Network → request → Headers → Response Headers
```
I reviewed the returned HTTP response headers.

### Step 9 — Review security-related headers

I looked for headers such as:

- Content-Security-Policy
- X-Content-Type-Options
- X-Frame-Options
- Strict-Transport-Security
- Referrer-Policy

### Step 10 — Compare observations

Different responses were reviewed because headers may not be identical for every endpoint.

One response contained a Content-Security-Policy header, while another selected response mainly contained general HTTP headers.

I recorded these as observations rather than immediately treating them as vulnerabilities.

## 9. Evidence Collected

The following evidence was collected during the investigation:
- Docker version and Docker environment information.
- WebGoat Docker image information.
- Docker container status and port mapping.
- curl HTTP response showing WebGoat responding locally.
- Chrome Network tab showing WebGoat requests.
- Response Headers from WebGoat requests.
- A response showing a Content-Security-Policy header.
- A selected response where the reviewed security headers were not present in the visible response-header list.

Sensitive information such as session identifiers or tokens should be removed or redacted before uploading screenshots to GitHub.

## 10. Expected Result

I expected to observe HTTP response headers from the WebGoat application and identify which security-related headers were present.

I also expected that some headers might be missing or configured differently depending on the response.

The purpose was to understand the application's security configuration rather than to exploit the application.

## 11. Limitations / Safety Boundaries

This investigation was performed only against a locally hosted WebGoat training environment.

I did not test real websites or systems without authorization.

The investigation was limited to:
- Localhost WebGoat traffic.
- Normal application requests.
- HTTP response-header inspection.
- Basic configuration analysis.

I did not perform:
- Unauthorized scanning.
- Credential attacks.
- Data extraction.
- Denial-of-service testing.
- Testing of real external websites.
- Disruptive exploitation.

Security-header absence was treated as an observation and not automatically classified as a vulnerability.

## 12. What I Learned
Through this investigation, I learned how a web application communicates with a browser using HTTP requests and responses.
Before the practical work, security headers were mostly theoretical to me. By using Chrome Developer Tools, I could actually see the headers returned by the application.
I learned that headers such as Content-Security-Policy can control how browsers handle scripts and other content.
I also learned that different responses can have different headers, so checking only one request may not give a complete picture of an application's configuration.
Most importantly, I learned that a security observation should be verified before calling it a vulnerability. Evidence, scope, and the actual security impact need to be considered before reaching a conclusion.
