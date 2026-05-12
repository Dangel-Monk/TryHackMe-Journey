
## Command Line

> Learn the command line and MS PowerShell in Windows by practising various essential commands. Then, discover the use of Bash in the Linux OS.

> Understanding command-line interfaces (CLI) is essential, as many security tools and tasks require their configuration and usage through them. CLIs are imperative for scripting and automation and can prove very helpful in carrying out penetration testing and incident analysis. This module will teach us how to use the command line and PowerShell in Windows and Bash in Linux.

----
<br>



## Windows Command Line

| Basic System Information |
| - |

> Before issuing commands, we should note that we can only issue the commands within the Windows Path. You can issue the command `set` to check your path from the command line. The terminal output below shows the path where MS Windows will execute commands, as indicated by the line starting with `Path=`

> Let’s use the ver command to determine the operating system (OS) version.

> We can run the `systeminfo` command to list various information about the system such as OS information, system details, processor and memory.

> First, you can pipe it through `more` if the output is too long. Then, you can view it page after page by pressing the space bar button. To demonstrate this, try running `driverquery` and compare it with running `driverquery | more`. In the latter, you can display the output page by page and you can exit it using `CTRL + C`

> `help` - Provides help information for a specific command
> `cls` - Clears the Command Prompt screen.
<br>

| Network Troubleshooting |
| - |

