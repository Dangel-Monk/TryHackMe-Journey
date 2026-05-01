
## Start Your Cyber Security Journey

> Explore offensive and defensive cyber security via interactive exercises and acquire the essential search skills to find information.

> This module introduces the reader to offensive cyber security through an interactive exercise where users can practice hacking an insecure web application in a legal and safe environment. Then, it presents defensive security via an interactive exercise to protect against an attack. Finally, it equips the reader with the fundamental search skills to find what they need as they start their journey in cyber security.

----
<br>



## Offensive Security Intro

> "To outsmart a hacker, you need to think like one."

> This is the core of "Offensive Security." It involves breaking into computer systems, exploiting software bugs, and finding loopholes in applications to gain unauthorized access. The goal is to understand hacker tactics and enhance our system defences.

> We will use a command-line application called "Gobuster(opens in new tab)" to brute-force FakeBank's website to find hidden directories and pages. Gobuster will take a list of potential page or directory names and try accessing a website with each of them; if the page exists, it tells you.

> Most companies have an admin portal page, giving their staff access to basic admin controls for day-to-day operations. For a bank, an employee might need to transfer money to and from client accounts. Due to human error or negligence, there may be instances when these pages are not made private, allowing attackers to find hidden pages that show or give access to admin controls or sensitive data.

```bash
# We have a page we would like to investigate... 
web_page="http://fakebank.thm";

# We just need to know the location of the text with the most common folder names... 
wordlist="/home/ubuntu/Desktop/wordlist.txt";

# And we run the script with the option `dir` to search directories primarily...
gobuster -u $web_page -w $wordlist dir;

# [...]
# Bingo, we found a couple of folders containing the page apart from the main one...
interesting_page="/bank-transfer";
```

+ *This seems like a very simple scenario; we just put in a couple of commands with different options, filled in the blanks, and voila, it gave us the answer... right? You're not paying attention...*

1. *We examined a website and noticed the poor quality of the site... isn't it too simple?*
2. *A webpage isn't so different from a folder with several files / folders, and we use a tool to discover them.*
3. *We write down the data that interests us somewhere, not only to remember it but also to make it easier to reuse in the future.*

+ *Like thousands of situations you'll encounter along the way, You must be able to formulate your own conclusions and create the habit of thinking about the big picture of the situation.*

----
<br>



## Defensive Security Intro

> In the previous lesson, we learned about offensive security, which aims to identify and exploit system vulnerabilities to enhance security measures. This includes exploiting software bugs, leveraging insecure setups, and taking advantage of unenforced access control policies, among other strategies. Red teams and penetration testers specialize in these offensive techniques.

> Some of the tasks that are related to defensive security include:
>
>> 1. User cyber security awareness: Training users about cyber security helps protect against attacks targeting their systems.
>> 2. Documenting and managing assets: We need to know the systems and devices we must manage and protect adequately.
>> 3. Updating and patching systems: Ensuring that computers, servers, and network devices are correctly updated and patched against any known vulnerability (weakness).
>> 4. Setting up preventative security devices: firewall and intrusion prevention systems (IPS) are critical components of preventative security. Firewalls control what network traffic can go inside and what can leave the system or network. IPS blocks any network traffic that matches present rules and attack signatures.
>> 5. Setting up logging and monitoring devices: Proper network logging and monitoring are essential for detecting malicious activities and intrusions. If a new unauthorized device appears on our network, we should be able to detect it.

+ *What's the main takeaway from this point? Simply put, a person capable of attacking must know they are attacking, and vice versa. This is the best point for changing your mindset, your top priority is understanding the systems and how they work... how they can be abused and protected.*
<br>

| Security Operations Center (SOC) |
| - |

> A Security Operations Center (SOC) is a team of cyber security professionals that monitors the network and its systems to detect malicious cyber security events.
<br>

| Threat Intelligence |
| - |

> In this context, intelligence refers to information you gather about actual and potential enemies. A threat is any action that can disrupt or adversely affect a system. Threat intelligence collects information to help the company better prepare against potential adversaries. The purpose would be to achieve a threat-informed defence. Different companies have different adversaries. Some adversaries might seek to steal customer data from a mobile operator; however, other adversaries are interested in halting the production in a petroleum refinery. Example adversaries include a nation-state cyber army working for political reasons and a ransomware group acting for financial purposes. Based on the company (target), we can expect adversaries.

> Intelligence needs data. Data has to be collected, processed, and analyzed. Data is collected from local sources such as network logs and public sources such as forums. Data processing arranges it into a format suitable for analysis. The analysis phase seeks to find more information about the attackers and their motives; moreover, it aims to create a list of recommendations and actionable steps.
<br>

| Digital Forensics and Incident Response (DFIR) |
| - |

> Forensics is the application of science to investigate crimes and establish facts. With the use and spread of digital systems, such as computers and smartphones, a new branch of forensics was born to investigate related crimes: computer forensics, which later evolved into digital forensics.

> In defensive security, the focus of digital forensics shifts to analyzing evidence of an attack and its perpetrators and other areas such as intellectual property theft, cyber espionage, and possession of unauthorized content.
>
>> 1. File System: Analyzing a digital forensics image (low-level copy) of a system’s storage reveals much information, such as installed programs, created files, partially overwritten files, and deleted files.
>> 2. System memory: If the attacker runs their malicious program in memory without saving it to the disk, taking a forensic image (low-level copy) of the system memory is the best way to analyze its contents and learn about the attack.
>> 3. System logs: Each client and server computer maintains different log files about what is happening. Log files provide plenty of information about what happened on a system. Even if the attacker tries to clear their traces, some traces will remain.
>> 4. Network logs: Logs of the network packets that have traversed a network would help answer more questions about whether an attack is occurring and what it entails.


