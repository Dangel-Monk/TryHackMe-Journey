
| Task 1 | = Introduction = |
| - | - |

> By the tiiimeee youuu finish thiiis rooom... yooouuu will have learned about the following protocols...
>
> > \a) WHOIS <br>
> > \b) DNS <br>
> > \c) HTTP and FTP <br>
> > \d) SMTP, POP3 and IMAP

+ *Ok, the first time I was really lost and didn't understand anything about what was happening with networks, but now that I'm reviewing it a second time it makes more sense (the value of writing...)*

----
<br>



| Task 2 | = DNS Remembering Addresses = |
| - | - |

> Do you remember the IP addresses of your favourite websites? Unless it is a private IP address of a local device, no one needs to worry about memorizing IP addresses. This is in part due to the Domain Name System (DNS), which is responsible for properly mapping a domain name to an IP address.

+ *In this sense, the existence of a DNS is like having an alias or nickname for the IP address of websites; in this sense, it's easier to remember by name...*

> DNS operates at the Application Layer, i.e., Layer 7 of the ISO OSI model. DNS traffic uses UDP port 53 by default and TCP port 53 as a default fallback.
>
> > \a) A Record <br>
> > The A (Address) record maps a hostname to one or more IPv4 addresses. For example, you can set `example.com` to resolve to `172.17.2.172`.
> >
> > \b) AAAA Record <br>
> > The AAAA record is similar to the A Record, but it is for IPv6. Remember that it is AAAA (quad-A), as AA and AAA would refer to a battery size; furthermore, AAA refers to Authentication, Authorization, and Accounting; neither falls under DNS.
> >
> > \c) CNAME Record <br>
> > The CNAME (Canonical Name) record maps a domain name to another domain name. For example, `www.example.com` can be mapped to `example.com` or even to `example.org`.
> >
> > \d) MX Record <br>
> > The MX (Mail Exchange) record specifies the mail server responsible for handling emails for a domain.

> If you want to look up the IP address of a domain from the command line, you can use a tool such as `nslookup`.
<br>

\> NSLookUp
```
nslookup         (Linux)



```
