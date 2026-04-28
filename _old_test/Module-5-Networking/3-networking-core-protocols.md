
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
<br>

\> NSLookUp
```
nslookup [arguments]        (Linux)

    [name]                The hostname or IP address you want to look up (the query target).
    [server]              Specifies the DNS server to use for the query, overriding your system's default.

    -type=[value]         Sets the DNS record type to query for (e.g., A, MX, NS). Default is A (IPv4 address).
    -class=[value]        Specifies the protocol class for the query (e.g., IN for Internet, CH for Chaos).
    -domain=[value]       Sets the default domain name for lookups.
    -port=[value]         Changes the default DNS server port from 53 to a specified value.

    -timeout=[value]      Sets the initial timeout for the query response in seconds.
    -retry=[value]        Specifies the number of times to retry the query if it fails.

    -version              Prints the version of nslook and immediately exits.
```

----
<br>



| Task 3 | = WHOIS = |
| - | - |

> You can register any available domain name for one or more years. You need to pay the annual fee, and you are required to provide accurate contact information(opens in new tab) as the registrant. This information is part of the data available via WHOIS records and is available publicly.
> 
> However, don’t worry if you want to register a domain without revealing your contact information publicly; you can use one of the privacy services that hide all your information from the WHOIS records.

+ *Hmm... I don't really know why this command is used? Maybe for reconnaissance, but who is obligated to register the pages? Because anyone could do it without having to provide information.*

> You can look up the WHOIS records of any registered domain name using one of the online services or via the command-line tool `whois`, available on Linux systems, among others. As expected, a WHOIS record provides information about the entity that registered a domain name, including name, phone number, email, and address.

+ *I also can't find a list of appealing options for the command...*

----
<br>


| Task 4 | = HTTP(S) Accessing the Web = |
| - | - |

> When you fire up your browser, you mainly use HTTP and HTTPS protocols. HTTP stands for Hypertext Transfer Protocol; the S in HTTPS stands for Secure. This protocol relies on TCP and defines how your web browser communicates with the web servers. HTTP and HTTPS commonly use TCP ports 80 and 443, respectively, and less commonly other ports such as 8080 and 8443.
>
> > \a) GET <br>
> > Retrieves data from a server, such as an HTML file or an image.
> >
> > \b) POST <br>
> > Allows us to submit new data to the server, such as submitting a form or uploading a file.
> > 
> > \c) PUT <br>
> > Is used to create a new resource on the server and to update and overwrite existing information.
> > 
> > \d) DELETE <br>
> > Is used to delete a specified file or resource on the server.

+ *Now for something interesting: get used to these magic words, as they'll be useful for anything related to HTTP. The only confusing ones are POST and PUT.*

> Using Wireshark, we can examine the exchange between the Firefox browser and the web server more closely. As you can tell, a lot of information is exchanged between the client and the server that does not get rendered to the user. Examples include the web server version and when the page was last modified.

+ *Since I'm not going to use material from the site (that's what the site is for), let's look at the general aspects. Every time we interact with a page, we make a request, right? And that's why the page responds with the result.*

        GET / HTTP/1.1
        Host: 10.10.41.192 (How you identify yourself)
        [...]
        "Hello, I want to see [GET] the main page [/], you can see that I am [Host]..."


        HTTP/1.1 200 OK
        Server: ngixn/1.18.0 (Ubuntu)
        [...]
        "Let me check... yes, everything seems fine [200 OK], here's what it contains..."

+ *So in order to solve the exercise we have to think about what they are asking us to do (this is a good time to start rationalizing...)*
  
    \a) We want to access a website through the terminal. <br>
    \b) We want to see if we can get a specific address.
<br>

    \1) We opened the terminal, and started with `telnet`... 
  
        # telnet [machine_ip] [port]

            [machine_ip]      Here you enter the IP address of your test machine, it can be [10.64.131.12]?
            [port]            The common port number of HTTP, like [80]...


  + *Now that we're inside, We will begin by creating our form line by line, starting with our request type and our identification (Remember to press <ENTER> after each line, and twice to finish...)*
<br>

    \2) We want to obtain a specific page with 'GET'...

        [...]
        # GET /[address] HTTP/1.1
        # Host: [machine name] 

            [address]           The page address, in this case the [flag.html] addres
            [machine name]      Since your machine is set up this way, you can put whatever you want on it, like [hand_over_the_flag].


----
<br>



| Task 5 | = FTP Transfering Files = |
| - | - |

> Unlike HTTP, which is designed to retrieve web pages, File Transfer Protocol (FTP) is designed to transfer files. As a result, FTP is very efficient for file transfer, and when all conditions are equal, it can achieve higher speeds than HTTP. FTP server listens on TCP port `21` by default; data transfer is conducted via another connection from the client to the server.
>
> > \a) USER <br>
> > Used to input the username
> >
> > \b) PASS <br>
> > Used to enter the password
> > 
> > \c) RETR <br>
> > Used to download a file from the FTP server to the client. (Retrive)
> > 
> > \d) STOR <br>
> > Used to upload a file from the client to the FTP server. (Store)
<br>

> FTP
```
telnet [commands]        (Linux)

    [ip_address]               The IP address of the machine. 
    [port]                     Specify if the port is not the common one.

    ls                         Displays the contents of the directory on the screen.
    dir                        List the directories on the remote server.

    cd [directory]             Change the directory of the remote machine.
    cdup                       To move up one level in the directory (like cd ..)

    lcd                        Change the local directory of your machine.

    get [filename]             Download a single file.
    mget [filenames]           Allows you to download multiple files (mget [file] [*.txt] [etc...])

    put [local file]           Choose a single file to upload.
    mput [local files]         Choose multiple files to upload.

    delete [file]              .
    mdelete [files]            .

    rename [old name] [new]    .

    help                       Perhaps you're interested in learning more FTP commands.
```

+ *For various reasons, we can use other types of services to connect to the machines; we just need to consider their structure. I could copy the example to text, but we still need the flag...*

    \a) We want to access FTP through the terminal. <br>
    \b) We want to get the flag.
<br>

    \1) Let's start the terminal as usual and use `ftp`...

        # ftp [machine_ip]

            [machine_ip]        Since we're still using the same machine [10.66.168.66]


        [...]
        # Name (10.66.168.66:root): [username]

             [username]         Could we try logging in with an account? But let's try entering as [anonymous]


        [...]
        # Password: [passwd]

              [passwd]          Since Anonymous doesn't have an account, we just press <ENTER>
<br>

    \2) Congratulations! You're in. Now that you're connected, we can use different commands to navigate this machine.

        # ftp> ls
        [...]

    \a) There appears to be more than one text, but we are only interested in one; if we wanted, we could download them all.

        # ftp> get [filename]

               [filename]        The [flag.txt] of course!


        # ftp> exit

+ *If you did nothing more than log in and log out, simply listing your current directory should show [flag.txt]*

