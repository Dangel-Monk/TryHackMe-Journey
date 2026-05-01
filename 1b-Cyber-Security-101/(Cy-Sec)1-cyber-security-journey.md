
## Start Your Cyber Security Journey

> Explore offensive and defensive cyber security via interactive exercises and acquire the essential search skills to find information.

> This module introduces the reader to offensive cyber security through an interactive exercise where users can practice hacking an insecure web application in a legal and safe environment. Then, it presents defensive security via an interactive exercise to protect against an attack. Finally, it equips the reader with the fundamental search skills to find what they need as they start their journey in cyber security.

## Offensive Security Intro

> "To outsmart a hacker, you need to think like one."

> This is the core of "Offensive Security." It involves breaking into computer systems, exploiting software bugs, and finding loopholes in applications to gain unauthorized access. The goal is to understand hacker tactics and enhance our system defences.

> We will use a command-line application called "Gobuster(opens in new tab)" to brute-force FakeBank's website to find hidden directories and pages. Gobuster will take a list of potential page or directory names and try accessing a website with each of them; if the page exists, it tells you.

> Most companies have an admin portal page, giving their staff access to basic admin controls for day-to-day operations. For a bank, an employee might need to transfer money to and from client accounts. Due to human error or negligence, there may be instances when these pages are not made private, allowing attackers to find hidden pages that show or give access to admin controls or sensitive data.

```bash
# We have a page we would like to investigate... 
user="http://fakebank.thm"

# We just need to know the location of the text with the most common folder names... 
wordlist="/home/ubuntu/Desktop/wordlist.txt"

# And we run the script with the option `dir` to search directories primarily...
gobuster -u $user -w $wordlist dir

# [...]
# Bingo, we found a couple of folders containing the page apart from the main one...
interesting_page="/bank-transfer"
```

+ *This seems like a very simple scenario; we just put in a couple of commands with different options, filled in the blanks, and voila, it gave us the answer... right? You're not paying attention...*

1. *We examined a website and noticed the poor quality of the site... isn't it too simple?*
2. *A webpage isn't so different from a folder with several files / folders, and we use a tool to discover them.*
3. *We write down the data that interests us somewhere, not only to remember it but also to make it easier to reuse in the future.*

+ *Like thousands of situations you'll encounter along the way, You must be able to formulate your own conclusions and create the habit of thinking about the big picture of the situation.*
