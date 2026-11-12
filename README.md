# Website Reconnaissance Tools in Kali Linux

A beginner-friendly guide to using WHOIS, WhatWeb, `nslookup`, `curl`, and WAFW00F for **authorized website reconnaissance**.

> **Permission and safety:** Run these checks only against domains and systems that you own or have explicit permission to assess. The example domain `networkwalks.com` is taken from the supplied terminal screenshots; replace it with an authorized target.

## WHOIS

**1. What is WHOIS?**

WHOIS is used to retrieve public domain-registration information, such as the registrar, registration and update dates, expiry date, name servers, and domain status.

![WHOIS command output](images/01-whois-output.png)

**2. Open the terminal.**

Start a terminal in your Kali Linux machine.

**3. Enter the WHOIS command and domain name.**

```bash
whois networkwalks.com
```

**4. Read the result.**

The terminal displays the available registration information for the domain. The exact fields depend on the registry and registrar.

![WhatWeb terminal screenshot supplied with the request](images/02-whatweb-output.png)

## WhatWeb

**5. What is WhatWeb?**

WhatWeb helps identify technologies used by a website. Depending on what the site exposes, it may detect the web server, CMS, JavaScript libraries, frameworks, and version information. It does not necessarily identify every component.

**6. Run WhatWeb in Kali Linux.**

```bash
whatweb https://networkwalks.com
```

Review the output for detected technologies and version strings. Treat these as indicators, not a guarantee that every component or version has been identified.

## DNS lookup with nslookup

**7. What is nslookup?**

`nslookup` queries DNS to find records associated with a domain. A common use is resolving a domain name to its IP address.

**8. Enter the domain name.**

```bash
nslookup networkwalks.com
```

Look for the returned address in the answer section. A domain can resolve to more than one IP address, and results can vary by DNS resolver and location.

## curl — inspect HTTP headers

<!-- SCREENSHOT 3: Place the third screenshot immediately before step 9. -->

**Screenshot 3:** Not supplied yet. When available, save it as `images/03-curl-headers.png` and replace this note with:
`![curl HTTP headers output](images/03-curl-headers.png)`

**9. What can HTTP headers reveal?**

HTTP response headers can reveal information such as the web server, caching behavior, redirects, and security-related header settings. They may expose implementation details, so review them as part of an authorized security assessment.

**10. Run curl with the -I option.**

```bash
curl -I https://networkwalks.com
```

The `-I` option requests the response headers without downloading the full page body.

## WAFW00F

**11. Check whether a website may use a web application firewall.**

WAFW00F checks whether a website appears to be protected by a web application firewall (WAF), and may identify the WAF product.

Run:

```bash
wafw00f https://networkwalks.com
```

Read the result carefully. A detection is an indication based on the tool's checks; a result that does not identify a WAF does not prove that no protection exists.

<!-- SCREENSHOT 4: Place the fourth screenshot immediately after step 11. -->

**Screenshot 4:** Not supplied yet. When available, save it as `images/04-wafw00f-output.png` and replace this note with:
`![WAFW00F output](images/04-wafw00f-output.png)`

## Quick command reference

| Tool | Command | Main purpose |
|---|---|---|
| WHOIS | `whois networkwalks.com` | Domain registration details |
| WhatWeb | `whatweb https://networkwalks.com` | Detect website technologies |
| nslookup | `nslookup networkwalks.com` | Query DNS records |
| curl | `curl -I https://networkwalks.com` | View HTTP response headers |
| WAFW00F | `wafw00f https://networkwalks.com` | Check for signs of a WAF |

## Notes

- Install a missing tool with Kali's package manager if it is not already available; check the package name and documentation for your Kali release.
- Tool output can change over time because websites, DNS records, and hosting configurations change.
- Do not treat detected versions or missing detections as proof of a vulnerability or absence of security controls.

## Repository contents

```text
kali-web-recon-tools/
├── README.md
├── .gitignore
└── images/
    ├── 01-whois-output.png
    └── 02-whatweb-output.png
```

The repository includes the two screenshots attached with the request. Screenshot 3 (curl) and screenshot 4 (WAFW00F) are marked as placeholders because those images were not attached.
