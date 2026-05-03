
## Linux Fundamentals

> Many servers and security tools use Linux. Learn how to use the Linux operating system, a critical skill in cyber security.

> Linux is one of the major operating systems and is heavily used in organisations all around the world. Learning how to use Linux is a core competency and will help you in your hacking journey not to just use Linux-based security tools, but how to use and exploit the operating system. This module will focus on getting you comfortable using Linux.

----
<br>



## Linux Fundamentals Part 1

| Where is Linux Used? | 
| - |

> It's fair to say that Linux is a lot more intimidating to approach than Operating System's (OSs) such as Windows. Both variants have their own advantages and disadvantages. For example, Linux is considerably much more lightweight and you'd be surprised to know that there's a good chance you've used Linux in some form or another every day!
<br>

| Flavours of Linux |
| - |

> The name "Linux" is actually an umbrella term for multiple OS's that are based on UNIX (another operating system). Thanks to Linux being open-source, variants of Linux come in all shapes and sizes - suited best for what the system is being used for.

> As we previously discussed, a large selling point of using OSs such as Ubuntu is how lightweight they can be. This, of course, doesn't come without its disadvantages, where for example, often there is no GUI (Graphical User Interface) or what is also known as a desktop environment that we can use to interact with the machine (unless it has been installed). A large part of interacting with these systems is using the "Terminal".

+ *Personally, I don't see much point in writing down thousands of commands that you'll forget if you only use this module. Instead, I propose the following: In every possible lesson, step outside your comfort zone and integrate commands...*

+ *[freeCodeCamp / Linux Handbook](www.freecodecamp.org/news/the-linux-commands-handbook/)*
+ *[Geeks for Geeks / Linux Tutorial](www.geeksforgeeks.org/linux-unix/linux-tutorial/)*

+ *As a bonus, you'll thank me later, but also learn some terminal shortcuts! They're not that different from what you already use, and they're related to text editors... *


```bash
# So, if you've followed the steps on the page and you're inside the machine, it's all yours!

message="Hello!"
echo $message "my friend!";      # `echo` prints to the terminal


# and to find out who we are, what username we are logged in with...

current_user=$(whoami)
echo "Welcome back! $current_user, lets do our best today.";
```
<br>

| Interacting With the Filesystem |
| - |

> As I previously stated, being able to navigate the machine that you are logged into without relying on a desktop environment is pretty important. After all, what's the point of logging in if we can't go anywhere?

```bash
# Every time we start a terminal, it would be good to know where we are.

echo "Your starting point is: [$(pwd)]"; ls -l;


# Now, it's something simple, something uncomplicated, but we should be able to navigate the system, right?

echo "We're in this directory, right? > $(pwd), and contains this:"; ls -l;


# But if we wanted, we could go back one level (or go to the parent folder) with `..`

cd ..;
echo "We're now at the top > $(pwd)"; ls -l;

# Or enter a folder by typing its name (You can type the beginning and complete it with <Tab>)

cd ~/Desktop/;      # If you enter `~`, you'll be accessing your personal folder directly.
```

+ *There are many folders that are very different from those in Windows, so you can also learn more about each one...*

+ *[Linux Foundation / Linux File-System](www.linuxfoundation.org/blog/blog/classic-sysadmin-the-linux-filesystem-explained)*
+ *[Geeks for Geeks / Linux Directory Structure](www.geeksforgeeks.org/linux-unix/linux-directory-structure/)*
<br>

| Outputting the Contents of a File (cat) |
| - |

> Whilst knowing about the existence of files is great — it's not all that useful unless we're able to view the contents of them.
> "Cat" is short for concatenating & is a fantastic way for us to output the contents of files (not just text files!).

```bash
# I usually prefer to open text files with an editor, but in some cases `cat` works.
# Let's say we want to make quick annotations to a text using echo.

pretty_please="Hyperhypexia is a harmless treatise"
porroe="I can't help them, they no longer exist."

echo $pretty_please > todo.txt;
echo $porroe >> todo.txt;
ls -l;

# And then with the help of `cat` we can show it at that moment.

cat todo.txt
```

