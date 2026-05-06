
## Linux Fundamentals Part

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

+ *As a bonus, you'll thank me later, but also learn some terminal shortcuts! They're not that different from what you already use, and they're related to text editors...*


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


``` bash
# I usually prefer to open text files with an editor, but in some cases `cat` works.
# Let's say we want to make quick annotations to a text using echo.

pretty_please="Hyperhypexia is a harmless treatise"
porroe="I can't help them, they no longer exist."

echo "$pretty_please" > todo.txt;        # Adds the text to the text file. 
echo "$porroe" >> todo.txt;              # Add to the end of the text. 
ls -l;


# And then with the help of `cat` we can show it at that moment.

cat todo.txt;
```
<br>

| Searching for Files | 
| - |

> Although it doesn't seem like it so far, one of the redeeming features of Linux is truly how efficient you can be with it. With that said, you can only be as efficient as you are familiar with it of course. As you interact with OSs such as Ubuntu over time, essential commands like those we've already covered will start to become muscle-memory.

> The find command is fantastic in the sense that it can be used both very simply or rather complex depending upon what it is you want to do exactly. However, let's stick to the fundamentals first.


```bash
# Let's consider a situation where we created thousands of folders throughout the system...

cd ~/Desktop; mkdir Imagine-All The-Different Problems-Right;
echo "This is a test" >> ./The-Different/bango.txt; ls -l *;


# Now, we have a couple of folders and in one of them there is some text...

wheres_text=$(find . -name "*.txt")

echo "Theres a text at: "$wheres_text"";
```
<br>

| Using Grep | 
| - |

> Using a command like cat isn't going to cut it too well here. Let's say for example if we wanted to search this log file to see the things that a certain user/IP address visited? Looking through 244 entries isn't all that efficient considering we want to find a specific value.

> We can use grep to search the entire contents of this file for any entries of the value that we are searching for. Going with the example of a web server's access log, we want to see everything that the IP address "81.143.211.90" has visited (note that this is fictional)

```bash
# After obtaining a network scan, or looking at the logs, you become interested in an IP address...

logs_container="$HOME/Desktop"
sus_ip="164.60.83.21"
log_file="$logs_container/access-log.txt"
out_file="$logs_container/investigate.txt"

grep -wn "$sus_ip" "$log_file" > "$out_file";
cat "$out_file";


# What if there are multiple files with access points, but in different folders?

grep -R -w "$sus_ip" "$logs_container";
```
<br>

| Shell Operators | 
| - |

> Operator "`&`"
>> This operator allows us to execute commands in the background. For example, let's say we want to copy a large file. This will obviously take quite a long time and will leave us unable to do anything else until the file successfully copies.

> Operator "`&&`"
>> This shell operator is a bit misleading in the sense of how familiar is to its partner "&". Unlike the "&" operator, we can use "&&" to make a list of commands to run for example `command1 && command2`. However, it's worth noting that `command2` will only run if `command1` was successful.

> Operator "`>`"
>> This operator is what's known as an output redirector. What this essentially means is that we take the output from a command we run and send that output to somewhere else.

> Operator "`>>`"
>> The `>>` operator allows to append the output to the bottom of the file — rather than replacing the contents of the file.

----
<br>



## Linux Fundamentals Part 2

| Access using SSH | 
| - |

> Secure Shell or SSH simply is a protocol between devices in an encrypted form. Using cryptography, any input we send in a human-readable format is encrypted for travelling over a network -- where it is then unencrypted once it reaches the remote machine.

```bash
# There is an exercise on the page where you can connect to a machine. 

user_name='tryhackme'
exercise_machine='191.102.248.140'
password_if="" # note your password here if needed

'yes' | ssh "$user_name@$exercise_machine";
```
<br>

| Access using SSH | 
| - |

> A majority of commands allow for arguments to be provided. These arguments are identified by a hyphen and a certain keyword known as flags or switches.

> Commands that accept these will also have a --help option. This option will list the possible options that the command accepts, provide a brief description and example of how to use it.

```bash
# As you will realize, the manual will also be something you use constantly for your learning.

ls -l;        # Displays the contents of the folder in a list.
ls --help;    # Displays the command manual `ls`


# Some useful shortcuts that can help you not lose your mind...

<q>    Quit the manual.
<f>    Turn forward half a page.
<b>    Go back half a page.
<d>    Turn forward one page.
<u>    Go back one entire page.


# Either way, you can find help online or use help commands in the terminal...

help_command='ls'

man [man];
man [-h | --help];
man [man]; <h>        It offers a more extensive list of shortcuts for getting around.
```
<br>

| Filesystem Interaction Continued | 
| - |

> In this task, we're going to learn some more commands for interacting with the filesystem to allow us to:
>
>> - Create files and folders
>> - Move files and folders
>> - Delete files and folders

```bash
# It wouldn't make much sense to learn these commands without making sense of them...
# Therefore, we will focus more on knowing, what is it that we want to do?

# 1. Create 3 folders on the desktop: personal notes, logs, and whitelist.
# 2. Create several empty files in each folder but with corresponding names.
# 3. In your personal notes, create a file with your goals and a proverb.
# 4. In the logs, create a list with 5 randomly generated IPs.
# 5. Copy the text to the whitelist folder, and rename it.


# This is just one way to do it, try different ways...

cd ~/Desktop;
mkdir -p Small-Project/Personal-Notes Small-Project/Logs-Reg Small-Project/White-List;
cd Small-Project;

# Create mathc{a..e}na.txt in each of the three directories
touch {Personal-Notes,Logs-Reg,White-List}/mathc{a..e}na.txt;

# Append a quote to Personal-Notes/text-quill.txt
quoting="The way to get started is to quit talking and begin doing. -Walt Disney"
echo "$quoting" >> Personal-Notes/text-quill.txt;

# Proper IP array
ip_list=("238.137.208.223" "70.131.83.191" "91.40.214.1" "33.96.32.138" "38.15.28.75")

for me_ip in "${ip_list[@]}"; do
    echo "$me_ip" >> Logs-Reg/ip-record.txt;
done;

# Copy the log to the White-List directory and rename
cp Logs-Reg/ip-record.txt White-List/ip-record.txt;
mv White-List/ip-record.txt White-List/allow-list.txt;


# Cool! Everything should be in order. You can delete it like this (Always be careful with `rm`, please! or use -i / -I as a safenet):
rm -r ~/Desktop/Small-Project;
```
<br>

| Permissions 101 |
| - |

> As you would have already found out by now, certain users cannot access certain files or folders. We've previously explored some commands that can be used to determine what access we have and where it leads us.
> 
> Although intimidating, these three columns are very important in determining certain characteristics of a file or folder and whether or not we have access to it. A file or folder can have a couple of characteristics that determine both what actions are allowed and what user or group has the ability to perform the given action.

+ *If it wasn't very clear, you can look at more resources on the subject.*

+ *[Marc Nuri Blog / File Permissions](blog.marcnuri.com/linux-file-permissions-complete-guide)*
+ *[Geeks for Geeks / File Permissions](www.geeksforgeeks.org/linux-unix/set-file-permissions-linux/)*

> The great thing about Linux is that permissions can be so granular, that whilst a user technically owns a file, if the permissions have been set, then a group of users can also have either the same or a different set of permissions to the exact same file without affecting the file owner itself.
> 
> Let's put this into a real-world context; the system user that runs a web server must have permissions to read and write files for an effective web application. However, companies such as web hosting companies will have to want to allow their customers to upload their own files for their website without being the webserver system user -- compromising the security of every other customer. 




