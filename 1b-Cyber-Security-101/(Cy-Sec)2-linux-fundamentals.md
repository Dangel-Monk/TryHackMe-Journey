
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

+ *[freeCodeCamp / Linux Handbook](https://www.freecodecamp.org/news/the-linux-commands-handbook/)*
+ *[Geeks for Geeks / Linux Tutorial](https://www.geeksforgeeks.org/linux-unix/linux-tutorial/)*

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

+ *[Linux Foundation / Linux File-System](https://www.linuxfoundation.org/blog/blog/classic-sysadmin-the-linux-filesystem-explained)*
+ *[Geeks for Geeks / Linux Directory Structure](https://www.geeksforgeeks.org/linux-unix/linux-directory-structure/)*
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

+ *[Marc Nuri Blog / File Permissions](https://blog.marcnuri.com/linux-file-permissions-complete-guide)*
+ *[Geeks for Geeks / File Permissions](https://www.geeksforgeeks.org/linux-unix/set-file-permissions-linux/)*

> The great thing about Linux is that permissions can be so granular, that whilst a user technically owns a file, if the permissions have been set, then a group of users can also have either the same or a different set of permissions to the exact same file without affecting the file owner itself.
> 
> Let's put this into a real-world context; the system user that runs a web server must have permissions to read and write files for an effective web application. However, companies such as web hosting companies will have to want to allow their customers to upload their own files for their website without being the webserver system user -- compromising the security of every other customer. 

+ *I won't lie, while knowing file permissions isn't the complicated part, it's more about the users themselves: how to create them, modify them, switch between them, create groups, manage them, etc. It's something I'm still learning.*

+ *But something I do want to emphasize is permissions... Your research, operations, or even your own systems depend on having permissions correctly defined.  You'll notice that while there are actions a user can't perform, there are other ways they can. It won't make much sense right now, but stay alert for this type of details.*

----
<br>



## Linux Fundamentals Part 3

| Terminal Text Editors |
| - |

> Throughout the series so far, we have only stored text in files using a combination of the `echo` command and the pipe operators (`>` and `>>`). This isn't an efficient way to handle data when you're working with files with multiple lines and the sorts!
<br>

> \> Nano
> 
> It is easy to get started with Nano! To create or edit a file using nano, we simply use `nano filename` -- replacing "filename" with the name of the file you wish to edit.
>
> Nano has a few features that are easy to remember & covers the most general things you would want out of a text editor, including:
> 
>> 1. Searching for text
>> 2. Copying and Pasting
>> 3. Jumping to a line number
>> 4. Finding out what line number you are on
<br>

> \> Vim
> 
> VIM is a much more advanced text editor. Whilst you're not expected to know all advanced features, it's helpful to mention it for powering up your Linux skills.
<br>

| General / Useful Utilities |
| - |

> \> Downloading Files (Wget)
> 
> A pretty fundamental feature of computing is the ability to transfer files. For example, you may want to download a program, a script, or even a picture. Thankfully for us, there are multiple ways in which we can retrieve these files.

>  We're going to cover the use of wget .  This command allows us to download files from the web via HTTP -- as if you were accessing the file in your browser. We simply need to provide the address of the resource that we wish to download. For example, if I wanted to download a file named "myfile.txt" onto my machine, assuming I knew the web address it -- it would look something like this:

```bash
wget https://assets.tryhackme.com/additional/linux-fundamentals/part3/myfile.txt;
```
<br>

> \> Transferring Files From Your Host - SCP (SSH)
> 
> Secure copy, or SCP, is just that -- a means of securely copying files. Unlike the regular cp command, this command allows you to transfer files between two computers using the SSH protocol to provide both authentication and encryption.

> Working on a model of SOURCE and DESTINATION, SCP allows you to:
> 
>> - Copy files & directories from your current system to a remote system
>> - Copy files & directories from a remote system to your current system
<br>

```bash
# This works like a two-way route, where you specify whether you want to send or receive.
# Let's send the text by `scp` using the SOURCE and DESTINATION format:

ip_address_remote='192.168.1.30'
user_remote_system='ubuntu'
local_file='important.txt'
store_file_as='transferred.txt'

scp "$local_file" "$user_remote_system@$ip_address_remote":"~/Downloads/$store_file_as"


# In another sense, what happens if we now want to save it?

remote_local_file='documents.txt'
save_file_as='notes.txt'

scp "$user_remote_system@$ip_address_remote":"~/Downloads/$remote_local_file" "$save_file_as";


# It's like you normally connect to a machine via SSH; you just add the parameters to send / receive

ssh [Your things...] + "$user_remote_system@ip_address_remote" OR [Your things...];
```
<br>

> \> Serving Files From Your Host - WEB
>
> Ubuntu machines come pre-packaged with python3. Python helpfully provides a lightweight and easy-to-use module called "HTTPServer". This module turns your computer into a quick and easy web server that you can use to serve your own files, where they can then be downloaded by another computing using commands such as `curl` and `wget`.

> Python3's "HTTPServer" will serve the files in the directory where you run the command, but this can be changed by providing options that can be found within the manual pages. Simply, all we need to do is run `python3 -m  http.server` in the terminal to start the module!
<br>

```bash
# Let's experiment a bit with creating the service...

public_folder='~/Documents/Webserver-Files'
machine_ip='192.168.6.92'

# First, we need to be in the folder we want to share; this is important for several tools.

cd "$public_folder"; python3 -m http.server;


# It wasn't that difficult, you just have to leave that terminal open (since it's now a server).
# <ctrl> + <c>        if you want to stop it...

# Now we can connect to our computer with a link and download the content.

wget "http://$machine_ip:8000/secret_sauce.txt";


# Which makes you wonder, you're accessing a hard drive path with the added http... hmmm...
```
<br>

| Processes 101 |
| - |

> Processes are the programs that are running on your machine. They are managed by the kernel, where each process will have an ID associated with it, also known as its PID. The PID increments for the order In which the process starts. I.e. the 60th process will have a PID of 60.
<br>

> \> Viewing Processes
>
> We can use the friendly `ps` command to provide a list of the running processes as our user's session and some additional information such as its status code, the session that is running it, how much usage time of the CPU it is using, and the name of the actual program or command that is being executed

> To see the processes run by other users and those that don't run from a session (i.e. system processes), we need to provide aux to the ps command like so: `ps aux`
>
> Another very useful command is the `top` command; top gives you real-time statistics about the processes running on your system instead of a one-time view. These statistics will refresh every 10 seconds, but will also refresh when you use the arrow keys to browse the various rows.
<br>

> \> Managing Processes
>
> You can send signals that terminate processes; there are a variety of types of signals that correlate to exactly how "cleanly" the process is dealt with by the kernel. To kill a command, we can use the appropriately named `kill` command and the associated PID that we wish to kill.

> Below are some of the signals that we can send to a process when it is killed:
>
>> - SIGTERM - Kill the process, but allow it to do some cleanup tasks beforehand.
>> - SIGKILL - Kill the process - doesn't do any cleanup after the fact.
>> - SIGSTOP - Stop/suspend a process.
<br>

> \> How do Processes Start?
>
> Let's start off by talking about namespaces. The Operating System (OS) uses namespaces to ultimately split up the resources available on the computer to (such as CPU, RAM and priority) processes. Think of it as splitting your computer up into slices -- similar to a cake. Processes within that slice will have access to a certain amount of computing power, however, it will be a small portion of what is actually available to every process overall.

> Namespaces are great for security as it is a way of isolating processes from another -- only those that are in the same namespace will be able to see each other.
<br>

> \> Getting Processes/Services to Start on Boot
>
> Some applications can be started on the boot of the system that we own. For example, web servers, database servers or file transfer servers. This software is often critical and is often told to start during the boot-up of the system by administrators.

> Enter the use of `systemctl` -- this command allows us to interact with the systemd process/daemon. Continuing on with our example, systemctl is an easy to use command that takes the following formatting: `systemctl [option] [service]`

> We can do five options with `systemctl`:
>
>> - Start
>> - Stop
>> - Enable
>> - Disable
>> - Status
<br>

> \> An Introduction to Backgrounding and Foregrounding in Linux
>
> Processes can run in two states: In the background and in the foreground. For example, commands that you run in your terminal such as `echo` or things of that sort will run in the foreground of your terminal as it is the only command provided that hasn't been told to run in the background. "Echo" is a great example as the output of echo will return to you in the foreground, but wouldn't in the background
<br>

```bash
# Running this command prints the message to the screen...
echo "Hi THM";

# But what if we did it in the background? Nothing, silence... 
echo "Hi THM" &;
```
<br>

> This is great for commands such as copying files because it means that we can run the command in the background and continue on with whatever further commands we wish to execute (without having to wait for the file copy to finish first)
>
> We can do the exact same when executing things like scripts -- rather than relying on the & operator, we can use [Ctrl + Z] on our keyboard to background a process. It is also an effective way of "pausing" the execution of a script or command.

+ *Now, this might just be me, but if I understand correctly, there are certain commands that depend on being in the foreground (like `echo`), but other more practical operations like copying, moving, etc., have no problem running in the background.*

+ *So part of the usefulness of using [Ctrl + Z] is that it not only helps us send certain commands to the background (or using `&`) but when they are scripts that print to the screen, by sending them to the background "paused" them*

> With our process backgrounded using either [Ctrl + Z] or the `&` operator, we can use `fg` to bring this back to focus like below, where we can see the `fg` command is being used to bring the background process back into use on the terminal, where the output of the script is now returned to us.
<br>

| Maintaining your System: Automation |
| - |

> Users may want to schedule a certain action or task to take place after the system has booted. Take, for example, running commands, backing up files, or launching your favourite programs on, such as Spotify or Google Chrome.

> We're going to be talking about the cron process, but more specifically, how we can interact with it via the use of crontabs . Crontab is one of the processes that is started during boot, which is responsible for facilitating and managing cron jobs.
>
>> - MIN
>> What minute to execute at.
>>
>> - HOUR
>> What hour to execute at.
>>
>> - DAY
>> What day of the month to execute at.
>>
>> - MONTH
>> What month of the year to execute at.
>>
>> - DAY WEEK
>> What day of the week to execute at.
>>
>> - CMD
>> The actual command that will be executed.
<br>

```bash
# [number?] [MIN] [HOUR] [DAY] [MONTH] [DAY WEEK] [CMD]

# Example, create a backup of "Documents" in "var/backups"

0 */12 * * * cp -R /home/cmnatic/Documents /var/backups/;
```
<br>

+ *There are a couple of pages which will greatly help in understanding how they work*

+ *[Crontab Generator](https://crontab-generator.org/)*
+ *[Cronitor](https://crontab.guru/)*
<br>

| Maintaining your System: Automation |
| - |

> When developers wish to submit software to the community, they will submit it to an  "apt" repository. If approved, their programs and tools will be released into the wild. Two of the most redeeming features of Linux shine to light here: User accessibility and the merit of open source tools.

> Whilst Operating System vendors will maintain their own repositories, you can also add community repositories to your list! This allows you to extend the capabilities of your OS. Additional repositories can be added by using the `add-apt-repository` command or by listing another provider! For example, some vendors will have a repository that is closer to their geographical location.

+ *[.....] This is still beyond my radar :P*

> - Managing Your Repositories (Adding and Removing)
>
> Normally we use the apt command to install software onto our Ubuntu system. The apt command is a part of the package management software also named apt. Apt contains a whole suite of tools that allows us to manage the packages and sources of our software, and to install or remove software at the same time.

> Whilst you can install software through the use of package installers such as `dpkg`, the benefits of apt means that whenever we update our system -- the repository that contains the pieces of software that we add also gets checked for updates.
<br>

```bash
# There are a couple of steps in the page, so take the process more into consideration...
# 1. Let's download the GPG key and use apt-key to trust it.

wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -

# 2. Now that we have added this key to our trusted list, we can now add Sublime Text 3's repository to our apt sources list. A good practice is to have a separate file for every different community/3rd party repository that we add.

# 2.1 Let's create a file named sublime-text.list in /etc/apt/sources.list.d and enter the repository information like so:

cd /etc/apt/sources.list.d; touch sublime-text.list;

# 2.2 And now use Nano or a text editor of your choice to add & save the Sublime Text 3 repository into this newly created file:

echo "deb https://download.sublimetext.com/ apt/stable/" > sublime-text.list;

# 2.3 After we have added this entry, we need to update apt to recognise this new entry -- this is done using the `apt update` command

# 2.4 Once successfully updated, we can now proceed to install the software that we have trusted and added to apt using `apt install sublime-text`
```
<br>

> Removing packages is as easy as reversing. This process is done by using the `add-apt-repository --remove ppa:PPA_Name/ppa` command or by manually deleting the file that we previously added to. Once removed, we can just use `apt remove [software-name-here]` i.e. `apt remove sublime-text`
<br>

| Maintaining your System: Logs |
| - |

> Located in the /var/log directory, these files and folders contain logging information for applications and services running on your system. The Operating System  (OS) has become pretty good at automatically managing these logs in a process that is known as "rotating".

> These services and logs are a great way in monitoring the health of your system and protecting it. Not only that, but the logs for services such as a web server contain information about every single request - allowing developers or administrators to diagnose performance issues or investigate an intruder's activity.



