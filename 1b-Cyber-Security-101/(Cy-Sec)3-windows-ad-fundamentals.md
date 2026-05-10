
## Windows and AD Fundamentals

> Get hands-on access to Windows and it's security controls. These basics will help you in identifying, exploiting and defending Windows.
>
> Keep existing description: Windows is the most popular operating system, used by individuals and corporate environments worldwide. This module will help you become comfortable using essential Windows features (in a safe environment), including user account permissions, resource management and monitoring, registry access, and security controls. It will also introduce you to Active Directory (AD) basics.

----
<br>



## Windows Fundamentals 1

| The File System |
| - |

> The file system used in modern versions of  Windows  is the New Technology File System or simply  NTFS.
> Before NTFS, there was  FAT16/FAT32 (File Allocation Table) and HPFS (High Performance File System).

> NTFS is known as a journaling file system. In case of a failure, the file system can automatically repair the folders / files on disk using information stored in a log file. This function is not possible with FAT.
<br>

> NTFS addresses many of the limitations of the previous file systems; such as:
>
>> - Supports files larger than 4GB.
>> - Set specific permissions on folders and files.
>> - Folder and file compression.
>> - Encryption (Encryption File System or EFS)
<br>

> On NTFS volumes, you can set permissions that grant or deny access to files and folders.
>
>> - Full control
>> - Modify
>> - Read & Execute
>> - List folder contents
>> - Read
>> - Write
<br>

+ *I couldn't say how much these pages will help in understanding how the file system works*

- [Kingston / Understanding File System](https://www.kingston.com/en/blog/personal-storage/understanding-file-systems)
- [Geeks for Geeks / File System](https://www.geeksforgeeks.org/ethical-hacking/windows-file-system-structure/)
<br>

> How can you view the permissions for a file or folder?
>
> 1. Right-click the file or folder you want to check for permissions.
> 2. From the context menu, select `Properties`.
> 3. Within Properties, click on the `Security` tab.
> 4. In the `Group or user names` list, select the user, computer, or group whose permissions you want to view.

> Another feature of NTFS is Alternate Data Streams (ADS), is a file attribute specific to Windows  NTFS (New Technology File System).

> Every file has at least one data stream ($DATA), and ADS allows files to contain more than one stream of data. Natively Window Explorer doesn't display ADS to the user. There are 3rd party executables that can be used to view this data, PowerShell also gives you the ability to view ADS for files.

> From a security perspective, malware writers have used ADS to hide data.
> Not all its uses are malicious. For example, when you download a file from the Internet, there are identifiers written to ADS to identify that the file was downloaded from the Internet.

+ *I didn't know that Windows also handled values for saving specific data... So, while using the equipment, can we create dynamic scripts?*
<br>

| The Windows / System32 Folders |
| - |

> The Windows folder (`C:\Windows`) is traditionally known as the folder which contains the Windows operating system. The folder doesn't have to reside in the C drive necessarily. It can reside in any other drive and technically can reside in a different folder.

> This is where environment variables, more specifically system environment variables, come into play.  Even though not discussed yet, the system  environment variable for the Windows directory is `%windir%`.
>
> Per Microsoft, "Environment variables store information about the operating system environment. This information includes details such as the operating system path, the number of processors used by the operating system, and the location of temporary folders".

+ *This should greatly simplify navigating or moving around the computer. What I really like is that you not only have a graphical view of all the folder contents, but also the top bar can be modified.*

> The System32 folder holds the important files that are critical for the operating system. You should proceed with extreme caution when interacting with this folder. Accidentally deleting any files or folders within System32 can render the Windows OS inoperational.
<br>

| User Accounts, Profiles and Permissions |
| - |

> User accounts can be one of two types on a typical local Windows system: Administrator & Standard User. The user account type will determine what actions the user can perform on that specific Windows system. 
>
>> - An Administrator can make changes to the system: add users, delete users, modify groups, modify settings on the system, etc. 
>> - A Standard User can only make changes to folders/files attributed to the user & can't perform system-level changes, such as install programs.

> There are several ways to determine which user accounts exist on the system. One way is to click the `Start Menu` and type `Other User`. A shortcut to `System Settings` > `Other users` should appear. 
>
> When a user account is created, a profile is created for the user. The location for each user profile folder will fall under is `C:\Users`.

> Another way to access this information, and then some, is using Local User and Group Management. Right-click on the Start Menu and click Run. Type `lusrmgr.msc`.

+ *Part of having an overview is knowing what types of users are in the system and how they are configured. What type of permissions do they have, what access do they have, and what groups do they belong to...*
<br>

| User Account Control |
| - |

> The large majority of home users are logged into their Windows systems as local administrators. Remember from the previous task that any user with administrator as the account type can make changes to the system.

> A user doesn't need to run with high (elevated) privileges on the system to run tasks that don't require such privileges, such as surfing the Internet, working on a Word document, etc. This elevated privilege increases the risk of system compromise because it makes it easier for malware to infect the system. Consequently, since the user account can make changes to the system, the malware would run in the context of the logged-in user.

> To protect the local user with such privileges, Microsoft introduced User Account Control (UAC). This concept was first introduced with the short-lived Windows Vista (opens in new tab) and continued with versions of Windows that followed.
>
> How does UAC work? When a user with an account type of administrator logs into a system, the current session doesn't run with elevated permissions. When an operation requiring higher-level privileges needs to execute, the user will be prompted to confirm if they permit the operation to run.

+ *Many of these verification systems are useful for reinforcing decision-making, to ensure that certain actions are indeed being taken. And while they are not perfect, You should take precautions and develop good habits.*
<br>

| Task Manager |
| - |

> The Task Manager provides information about the applications and processes currently running on the system. Other information is also available, such as how much CPU and RAM are being utilized, which falls under Performance.

+ *[How-To Geek / Windows Task Manager](https://www.howtogeek.com/405806/windows-task-manager-the-complete-guide/)*

----
<br>



## Windows Fundamentals 2

| System Configuration and Advance System Settings |
| - |

> The System Configuration utility (`MSConfig`) is for advanced troubleshooting, and its main purpose is to help diagnose startup issues.
<br>

> The utility has five tabs across the top. Below are the names for each tab. We will briefly cover each tab in this task.
>
>> - General (We can select what devices and services for Windows to load upon boot)
>> - Boot (We can define various boot options for the Operating System)
>> - Services (Lists all services configured for the system regardless of their state)
>> - Startup (Manages programs that launch automatically at login)
>> - Tools (Provides a centralized list of diagnostic and system management utilities)

> As you can see, Microsoft advises using Task Manager (`taskmgr`) to manage (enable/disable) startup items. The System Configuration utility is NOT a startup management program.

> Unlike Windows 10 or 11, you will not see startup programs in `Task Manager` or in the Startup tab of `msconfig`. On these Windows server machines, the only reliable way to view user-level startup items is through the Startup folder itself. You can access it by pressing `Win + R`, which opens the Run Dialog, typing `shell:startup`, and then pressing Enter. This will display all startup programs as shortcuts or executables that are configured to run automatically the next time a user logs in. This is where you can verify applications that are configured to launch at startup.

+ *As you can see, it is very useful to understand each of the tools in the tab, main uses, file location. The benefit is being able to have them grouped together, but it also finds other ways to execute them.*
<br>

> \> Advanced System Settings
>
> Windows gives you some additional configuration settings as well, which you can use to control the performance behavior and system recovery. To access this option, you can search for `View advanced system settings` in your search bar and open it.

> Windows uses a page file as an extra virtual memory space when the physical RAM becomes full. This helps to prevent slowdowns or application crashes when the system runs out of memory. You can view or modify the page file by navigating to the `Advanced` option at the top and clicking `Settings` under the `Performance` tab.
<br>

>  In this Performance tab, the Advanced option can also tell you about the page file size configured for the drives. In this case, it's `1048 MB`. The other settings here can give you the following information:
> 
>> - The drive where the page file is stored
>> - The initial size (MB)
>> - The maximum size
>> - Whether Windows manages the size automatically

> There is another cool configuration that you can find in the Advanced System Settings. It is known as Startup and Recovery. Windows can create a crash dump file whenever it encounters a critical error, such as a Blue Screen of Death. This crash dump helps the administrators or analysts understand what went wrong during the crash. You can view or modify the crash dump settings by navigating to the `Advanced` option at the top and then clicking `Settings` under the `Startup and Recovery` section.
<br>

> Here, you will find different settings for the startup and recovery. The Write debugging information dropdown tells you the type of crash dump configured for the system. Windows supports different dump types, such as:
> 
>> - Automatic memory dump
>> - Kernel memory dump
>> - Small memory dump (256 KB)
>> - Complete memory dump
>> - None

+ *Another thing to consider is the startup and recovery logs. I can imagine a situation where we make a mistake by modifying system settings that prevents it from working correctly. Or perhaps there is some benefit to obtaining extra information by deliberately causing problems.*
<br>

| UAC Settings |
| - |

> You can find the current level by looking at the position of the slider in the `User Account Control settings` window.
<br>

> This slider has four security levels, each of which controls how Windows alerts you when apps or users try to make changes at the system level. They fall into four standard categories as explained below:
>
>> - Always notify: This is the highest security. Windows notifies you whenever any apps or you yourself try to make changes, and the desktop dims (Secure Desktop).
>>
>> - Notify for apps: Windows notifies only when apps try to make changes, but not when you change Windows settings. This option is enabled by default.
>>
>> - Notify without dimming: Same as above (Notify for apps), but this time the screen does not dim. 
>>
>> - Never notify: Notifications are turned off. Windows won’t warn you about any changes made by you or any apps. 
<br>

| Computer Management |
| - |

> The Computer Management (`compmgmt`) utility has three primary sections: System Tools, Storage, and Services and Applications.
<br>

> \> System Tools

> Let's start with `Task Scheduler`. Per Microsoft, with Task Scheduler, we can create and manage common tasks that our computer will carry out automatically at the times we specify.
>
> A task can run an application, a script, etc., and tasks can be configured to run at any point. A task can run at log in or at log off. Tasks can also be configured to run on a specific schedule, for example, every five mins.
<br>

> Next is `Event Viewer`, allows us to view events that have occurred on the computer. These records of events can be seen as an audit trail that can be used to understand the activity of the computer system. This information is often used to diagnose problems and investigate actions executed on the system. 
>
> 1. The pane on the left provides a hierarchical tree listing of the event log providers. (as shown in the image above).
> 2. The pane in the middle will display a general overview and summary of the events specific to a selected provider.
> 3. The pane on the right is the actions pane.

> `Shared Folders` is where you will see a complete list of shares and folders shared that others can connect to. As with any object in Windows, you can right-click on a folder to view its properties, such as Permissions (who can access the shared resource).

> The `Local Users and Groups` section you should be familiar with from Windows Fundamentals 1 because it's `lusrmgr.msc`.

> In `Performance`, you'll see a utility called Performance Monitor (`perfmon`). Perfmon is used to view performance data either in real-time or from a log file. This utility is useful for troubleshooting performance issues on a computer system, whether local or remote.

> `Device Manager` allows us to view and configure the hardware, such as disabling any hardware attached to the computer.
<br>

> \> System Tools
<br>

> Under Storage is Windows Server Backup and Disk Management. `Disk Management` is a system utility in Windows that enables you to perform advanced storage tasks.  Some tasks are:
>
>> - Set up a new drive
>> - Extend a partition
>> - Shrink a partition
>> - Assign or change a drive letter (ex. E:) 

> Recall from the previous task, a service is a special type of application that runs in the background. You can see all the services and their statuses by clicking the `Services` button given under the Services and Applications section.
>
> The services shown above have their display names, status, and other values. If you want to get more information about any service, right-click on the service and click `properties`. Here, you will see additional details, such as the service name (which differs from the display name), the path to its executable, its startup type, and other relevant information.
<br>

| System Information |
| - |

> What is the System Information (`msinfo32`) tool?
>
> Per Microsoft, "Windows includes a tool called Microsoft System Information (Msinfo32.exe).  This tool gathers information about your computer and displays a comprehensive view of your hardware, system components, and software environment, which you can use to diagnose computer issues."
>
> The  information in System Summary is divided into three sections:
>
>> - Hardware Resources
>>
>> The information displayed in Hardware Resources is not for the average computer user. If you want to learn more about this section, refer to the official Microsoft page(opens in new tab).
>> 
>> - Components
>>   
>> Under Components, you can see specific information about the hardware devices installed on the computer. Some sections don't show any information, but some sections do, such as Display and Input.
>> 
>> - Software Environment
>>   
>> In the Software Environment section, you can see information about software baked into the operating system and software you have installed. Other details are visible in this section as well, such as the Environment Variables and Network Connections. 

> Per Microsoft, "Environment variables store information about the operating system environment. This information includes details such as the operating system path, the number of processors used by the operating system, and the location of temporary folders.
>
> The environment variables store data that is used by the operating system and other programs. For example, the WINDIR environment variable contains the location of the Windows installation directory. Programs can query the value of this variable to determine where Windows operating system files are located".
<br>

| Resource Monitor |
| - |

> What is Resource Monitor (`resmon`)?
>
> Per Microsoft, "Resource Monitor displays per-process and aggregate CPU, memory, disk, and network usage information, in addition to providing details about which processes are using individual file handles and modules. Advanced filtering allows users to isolate the data related to one or more processes (either applications or services), start, stop, pause, and resume services, and close unresponsive applications from the user interface. It also includes a process analysis feature that can help identify deadlocked processes and file locking conflicts so that the user can attempt to resolve the conflict instead of closing an application and potentially losing data."
>
> In the Overview tab, Resmon has four sections:
>
> - CPU
> - Disk
> - Network
> - Memory

+ *It provides granular, per-process visibility into CPU, memory, disk, and network usage, making it useful for identifying malicious activity (malware, spyware, unauthorized connections) without needing third-party tools.*
<br>

| Commands Prompt |
| - |

> The command prompt (cmd) can seem daunting at first, but it's really not that bad once you understand how to interact with it. In early operating systems, the command line was the sole way to interact with the operating system.
>
> When the GUI (graphical user interface) was introduced, it allowed users to perform complex tasks with a few clicks of a button instead of entering commands in the command prompt. Even though the GUI is the primary way to interact with the operating system, a computer user can still interact via the command prompt.
<br>

```powershell
# Here are a couple of Linux commands we can reuse to learn about our computer.

hostname
whoami

# This command will show the network address settings for the computer.

ipconfig
ipconfig /?

# This command will display protocol statistics and current TCP/IP network connections.

netstat
netstat /?

# The net command is primarily used to manage network resources. This command supports sub-commands.

net
net help
```
<br>

+ *If at any point you'd like to start using the terminal in Windows, you can begin directly with PowerShell, as it not only offers the most control over the system, but also it has its own syntax and command logic.* 
<br>

| Registry Editor |
| - |

> The Windows Registry (per Microsoft) is a central hierarchical database used to store information necessary to configure the system for one or more users, applications, and hardware devices.
>
> The registry contains information that Windows continually references during operation, such as:
>
>> - Profiles for each user.
>> - Applications installed on the computer and the types of documents that each can create.
>> - Property sheet settings for folders and application icons.
>> - What hardware exists on the system.
>> - The ports that are being used.
>
> Warning: The registry is for advanced computer users. Making changes to the registry can affect normal computer operations.
>
> There are various ways to view/edit the registry. One way is to use the Registry Editor (`regedit`).

+ *The Windows Registry is a hierarchical database controlling Windows settings, acting as a critical target for attackers to establish persistence, elevate privileges, or hide malicious activity. Security teams monitor it for unauthorized changes, particularly in startup locations and services, while investigators use it to map user/attacker activity*

----
<br>



## Windows Fundamentals 3

| Windows Update |
| - |

> Windows Update is a service provided by Microsoft to provide security updates, feature enhancements, and patches for the Windows operating system and other Microsoft products, such as Microsoft Defender. 

> Updates are typically released on the 2nd Tuesday of each month. This day is called Patch Tuesday. That doesn't necessarily mean that a critical update/patch has to wait for the next Patch Tuesday to be released. If the update is urgent, then Microsoft will push the update via the Windows Update service to the Windows devices.

> Throughout the years, Windows users have grown accustomed to pushing Windows Updates off to a later date or not installing the updates at all. Various reasons caused this action, one being the fact that a reboot is typically required after a Windows update.  

> Microsoft notably addressed this issue with Windows 10. The updates can no longer be ignored or pushed to the side until forgotten. Windows updates can only be postponed, but eventually, the update will happen, and your computer will reboot. Microsoft provides these updates to keep the device safe and secure.

+ *If you thought Windows updates were inconvenient, you'll have fewer and fewer options about it LOL, but while I also hate how Microsoft does things, they're becoming increasingly necessary. It is the most widely used system, by people of a certain type and level of importance.*
<br>

| Windows Security |
| - |

> Per Microsoft, "Windows Security is your home to manage the tools that protect your device and your data". In case you missed it, Windows Security is also available in Settings. 
>
> In the above image, focus your attention on Protection areas.
>
>> - Virus & threat protection
>> - Firewall & network protection
>> - App & browser control
>> - Device security
<br>

| Virus & Threat Proteccion |
| - |

> \> Current threats
>
>> Scan options
>>
>> - Quick scan - Checks folders in your system where threats are commonly found.
>> - Full scan - Checks all files and running programs on your hard disk. This scan could take longer than one hour.
>> - Custom scan - Choose which files and locations you want to check.
>>
>> Threat history
>>
>> - Last scan - Windows Defender Antivirus automatically scans your device for viruses and other threats to help keep it safe.
>> - Quarantined threats - Quarantined threats have been isolated and prevented from running on your device. They will be periodically removed.
>> - Allowed threats - Allowed threats are items identified as threats, which you allowed to run on your device.
>
> Warning: Allow an item to run that has been identified as a threat only if you are 100% sure of what you are doing.
<br>

> \> Virus & threat protection settings
>
>> Manage settings 
>>
>> - Real-time protection - Locates and stops malware from installing or running on your device.
>> - Cloud-delivered protection - Provides increased and faster protection with access to the latest protection data in the cloud.
>> - Automatic sample submission - Send sample files to Microsoft to help protect you and others from potential threats. 
>> - Controlled folder access - This feature, if enabled, protects files, folders, and memory areas on your device from unauthorized changes by malicious or unknown applications. If it is enabled, only approved and trusted apps would be allowed to modify the files in the protected folders. To enable this feature, click on the `Manage controlled folder access` button under `Controlled Folder Access` and turn it on. 
>> - Exclusions - Windows Defender Antivirus allows you to exclude any files or folders from the antivirus scanning. This is done to reduce the number of false positives. Administrators might not want the antivirus to scan specific files or folders. By adding them to the exclusions list, the antivirus would ignore them and scan all the other files and folders. To add any file or folder to the Windows Defender exclusion list, click on the `Add or remove exclusions` button under `Exclusions` and add as many exclusions as you want. 
>> - Notifications - Windows Defender Antivirus will send notifications with critical information about the health and security of your device. 
> Warning: Excluded items could contain threats that make your device vulnerable. Only use this option if you are 100% sure of what you are doing. 
>
>> Virus & threat protection updates
>>
>> - Check for updates - Manually check for updates to update Windows Defender Antivirus definitions.
>
>> Ransomware protection
>>
>> - Controlled folder access - Ransomware protection requires this feature to be enabled, which in turn requires Real-time protection to be enabled.
>
> Warning: Excluded items could contain threats that make your device vulnerable. Only use this option if you are 100% sure of what you are doing.

+ *Having a system that analyzes for potential threats, and that offers tools not only to prevent major damage but also to contain the threat, is an extra layer of security for your system. But like any tool, it depends heavily on its correct use; it's not perfect, it's not the only option, and it requires constant updates to stay as close as possible to real-time attacks.*
<br>

| Firewall & Network Proteccion |
| - |

> What is a firewall?
> 
> Per Microsoft, "Traffic flows into and out of devices via what we call ports. A firewall is what controls what is - and more importantly isn't - allowed to pass through those ports. You can think of it like a security guard standing at the door, checking the ID of everything that tries to enter or exit".

> What is the difference between the 3 (Domain, Private, and Public)?
> 
> Per Microsoft, "Windows Firewall offers three firewall profiles: domain, private and public".
>
>> - Domain - The domain profile applies to networks where the host system can authenticate to a domain controller. 
>> - Private - The private profile is a user-assigned profile and is used to designate private or home networks.
>> - Public - The default profile is the public profile, used to designate public networks such as Wi-Fi hotspots at coffee shops, airports, and other locations.
> Warning: Unless you are 100% confident in what you are doing, it is recommended that you leave your Windows Defender Firewall enabled.

+ *While we're talking about an antivirus analyzing what's on the system, the firewall manages what access is allowed and what isn't. It goes into more detail about how to configure it, but it also has other functions.*
<br>

| App & Browser Control |
| - |

> In this section, you can change the settings for the Microsoft Defender SmartScreen.
> 
> Per Microsoft, "Microsoft Defender SmartScreen protects against phishing or malware websites and applications, and the downloading of potentially malicious files".
>
>> Check apps and files
>>
>> - Windows Defender SmartScreen helps protect your device by checking for unrecognized apps and files from the web.
>>
>> Exploit protection
>>
>> - Exploit protection is built into Windows 10 (and, in our case, Windows Server 2019) to help protect your device against attacks.
>
> Warning: Unless you are 100% confident in what you are doing, it is recommended that you leave the default settings.
<br>

| Device Security |
| - |

> Even though you'll probably never change any of these settings, for completion's sake, it will be covered briefly.
>
>> Core isolation
>>
>> - Memory Integrity - Prevents attacks from inserting malicious code into high-security processes.
>>
>> Security processor
>>
>> What is the Trusted Platform Module (TPM)?
>>
>> - Per Microsoft, "Trusted Platform Module (TPM) technology is designed to provide hardware-based, security-related functions. A TPM chip is a secure crypto-processor that is designed to carry out cryptographic operations. The chip includes multiple physical security mechanisms to make it tamper-resistant, and malicious software is unable to tamper with the security functions of the TPM".
<br>

| BitLocker |
| - |

> What is BitLocker?
>
> - Per Microsoft, "BitLocker Drive Encryption is a data protection feature that integrates with the operating system and addresses the threats of data theft or exposure from lost, stolen, or inappropriately decommissioned computers".
>
> On devices with TPM installed, BitLocker offers the best protection.
>
> - Per Microsoft, "BitLocker provides the most protection when used with a Trusted Platform Module (TPM) version 1.2 or later. The TPM is a hardware component installed in many newer computers by the computer manufacturers. It works with BitLocker to help protect user data and to ensure that a computer has not been tampered with while the system was offline".
<br>

| Volume Shadow Copy Service |
| - |

> Per Microsoft(opens in new tab), the Volume Shadow Copy Service (VSS) coordinates the required actions to create a consistent shadow copy (also known as a snapshot or a point-in-time copy) of the data that is to be backed up. 
> 
> Volume Shadow Copies are stored on the System Volume Information folder on each drive that has protection enabled.
<br>

> If VSS is enabled (System Protection turned on), you can perform the following tasks from within advanced system settings. 
> 
>> - Create a restore point
>> - Perform system restore
>> - Configure restore settings
>> - Delete restore points
>
> From a security perspective, malware writers know of this Windows feature and write code in their malware to look for these files and delete them. Doing so makes it impossible to recover from a ransomware attack unless you have an offline/off-site backup.

+ *Now, this is what really surprised me; I didn't know something like this existed. Which makes me a little nervous. What other things could offer more attack vectors? How is it that they usually manage to exploit it? Since they are options, they shouldn't be available unless there's a reason; it would involve weighing the pros and cons...*

----
<br>



## Active Directory Basics

| Windows Domains |
| - |

> Picture yourself administering a small business network with only five computers and five employees. In such a tiny network, you will probably be able to configure each computer separately without a problem. You will manually log into each computer, create users for whoever will use them, and make specific configurations for each employee's accounts. If a user's computer stops working, you will probably go to their place and fix the computer on-site.

> While this sounds like a very relaxed lifestyle, let's suppose your business suddenly grows and now has 157 computers and 320 different users located across four different offices. Would you still be able to manage each computer as a separate entity, manually configure policies for each of the users across the network and provide on-site support for everyone? The answer is most likely no.

> To overcome these limitations, we can use a Windows domain. Simply put, a Windows domain is a group of users and computers under the administration of a given business. The main idea behind a domain is to centralise the administration of common components of a Windows computer network in a single repository called Active Directory (AD). The server that runs the Active Directory services is known as a Domain Controller (DC).
<br>

> The main advantages of having a configured Windows domain are:
>
>> - Centralised identity management: All users across the network can be configured from Active Directory with minimum effort.
>> - Managing security policies: You can configure security policies directly from Active Directory and apply them to users and computers across the network as needed.

+ *For me, this is one of the sections that is furthest from what I know... And it's no longer because of the complexity, since again it's something you can create in your system today, but perhaps the sheer number of options is what's most paralyzing.*
<br>

| Active Directory |
| - |

> The core of any Windows Domain is the Active Directory Domain Service (AD DS). This service acts as a catalogue that holds the information of all of the "objects" that exist on your network. Amongst the many objects supported by AD, we have users, groups, machines, printers, shares and many others.

> \> Users
>
> Users are one of the most common object types in Active Directory. Users are one of the objects known as security principals, meaning that they can be authenticated by the domain and can be assigned privileges over resources like files or printers. You could say that a security principal is an object that can act upon resources in the network.
<br>

> Users can be used to represent two types of entities:
> 
>> - People: users will generally represent persons in your organisation that need to access the network, like employees.
>> - Services: you can also define users to be used by services like IIS or MSSQL. Every single service requires a user to run, but service users are different from regular users as they will only have the privileges needed to run their specific service.
<br>

> \> Machines
>
> Machines are another type of object within Active Directory; for every computer that joins the Active Directory domain, a machine object will be created. Machines are also considered "security principals" and are assigned an account just as any regular user. This account has somewhat limited rights within the domain itself.

> The machine accounts themselves are local administrators on the assigned computer, they are generally not supposed to be accessed by anyone except the computer itself, but as with any other account, if you have the password, you can use it to log in.

> Identifying machine accounts is relatively easy. They follow a specific naming scheme. The machine account name is the computer's name followed by a dollar sign. For example, a machine named `DC01` will have a machine account called `DC01$`.
<br>

> \> Security Groups
> 
> If you are familiar with Windows, you probably know that you can define user groups to assign access rights to files or other resources to entire groups instead of single users. This allows for better manageability as you can add users to an existing group, and they will automatically inherit all of the group's privileges. Security groups are also considered security principals and, therefore, can have privileges over resources on the network.
>
> Several groups are created by default in a domain that can be used to grant specific privileges to users. As an example, here are some of the most important groups in a domain:
> 
>> - Server Operators - Users in this group can administer Domain Controllers. They cannot change any administrative group memberships.
>>
>> - Backup Operators - Users in this group are allowed to access any file, ignoring their permissions. They are used to perform backups of data on computers.
>>
>> - Account Operators - Users in this group can create or modify other accounts in the domain.
>
>> - Domain Admins - Users of this group have administrative privileges over the entire domain. By default, they can administer any computer on the domain, including the DCs.
>> 
>> - Domain Users - Includes all existing user accounts in the domain.
>>
>> - Domain Computers - Includes all existing computers in the domain.
>>
>> - Domain Controllers - Includes all existing DCs on the domain.

+ *Wow, quite a lot of information, isn't it? So let's simplify it by groups of groups. Domain groups are the set of objects, such as users, computers, and controllers. Then there are the domain administrators, who have full permissions over the domain and all its content.*

+ *Then there are the operators, from the server operators who can modify the domain controllers, to the backup operators who have access to all files ignoring permissions, and finally the account operators who can modify or create users in the domain.*
<br>

> \> Active Directory Users and Computers
>
> To configure users, groups or machines in Active Directory, we need to log in to the Domain Controller and run "Active Directory Users and Computers"
>
> This will open up a window where you can see the hierarchy of users, computers and groups that exist in the domain. These objects are organised in Organizational Units (OUs) which are container objects that allow you to classify users and machines. OUs are mainly used to define sets of users with similar policing requirements. The people in the Sales department of your organisation are likely to have a different set of policies applied than the people in IT, for example. Keep in mind that a user can only be a part of a single OU at a time.
<br>

> You probably noticed already that there are other default containers apart from the THM OU. These containers are created by Windows automatically and contain the following:
>
>> - Builtin: Contains default groups available to any Windows host.
>> - Computers: Any machine joining the network will be put here by default. You can move them if needed.
>> - Domain Controllers: Default OU that contains the DCs in your network.
>> - Users: Default users and groups that apply to a domain-wide context.
>> - Managed Service Accounts: Holds accounts used by services in your Windows domain.
<br>

> \> Security Groups vs OUs
>
> You are probably wondering why we have both groups and OUs. While both are used to classify users and computers, their purposes are entirely different:
>
>> - OUs are handy for applying policies to users and computers, which include specific configurations that pertain to sets of users depending on their particular role in the enterprise. Remember, a user can only be a member of a single OU at a time, as it wouldn't make sense to try to apply two different sets of policies to a single user.
>> - Security Groups, on the other hand, are used to grant permissions over resources. For example, you will use groups if you want to allow some users to access a shared folder or network printer. A user can be a part of many groups, which is needed to grant access to multiple resources.

+ *Another somewhat complex topic, and one I'm still not entirely convinced I understand... The organizational units are the user configurations, the actions they can perform, the rules they have, etc...*

+ *On the other hand, security groups are the access levels that users have to different objects within the domain, such as printers, systems, folders, etc.*
<br>

| Managing Users in AD |
| - |

+ *In principle, all these sections are to demonstrate not only how to configure and modify an active directory, so feel free to go further and create more actions.*

+ *The first step is to take a general look at the system. How is it organized? What type of hierarchy is there, what type of objects are in the domain?*
<br>

> \> Deleting extra OUs and users
>
> The first thing you should notice is that there is an additional department OU in your current AD configuration that doesn't appear in the chart. We've been told it was closed due to budget cuts and should be removed from the domain. If you try to right-click and delete the OU, you will get the following error.
>
> By default, OUs are protected against accidental deletion. To delete the OU, we need to enable the Advanced Features in the View menu.
>
> This will show you some additional containers and enable you to disable the accidental deletion protection. To do so, right-click the OU and go to Properties. You will find a checkbox in the Object tab to disable the protection.
>
> Be sure to uncheck the box and try deleting the OU again. You will be prompted to confirm that you want to delete the OU, and as a result, any users, groups or OUs under it will also be deleted.
<br>

> \> Delegation
>
> One of the nice things you can do in AD is to give specific users some control over some OUs. This process is known as delegation and allows you to grant users specific privileges to perform advanced tasks on OUs without needing a Domain Administrator to step in.
>
> One of the most common use cases for this is granting IT support the privileges to reset other low-privilege users' passwords. According to our organisational chart, Phillip is in charge of IT support, so we'd probably want to delegate the control of resetting passwords over the Sales, Marketing and Management OUs to him.
>
> For this example, we will delegate control over the Sales OU to Phillip. To delegate control over an OU, you can right-click it and select Delegate Control
>
> This should open a new window where you will first be asked for the users to whom you want to delegate control

+ *With these simple steps, we see that there are several mechanisms to prevent errors / accidents. against deletion or modification of OUs, and be able to correctly assign delegations*

+ *Now there's an interesting detail: if Phillip wanted to perform any other action within the active directory, he couldn't, at least not with the interface. Therefore, I would have to use commands...*
<br>

```powershell
# With this command we are resetting Sophie's password with privileges
# We are also creating a prompt to enter the new password without saving or displaying it.

Set-ADAccountPassword sophie -Reset -NewPassword (Read-Host -AsSecureString -Prompt 'New Password') -Verbose

#New Password: *********
#VERBOSE: Performing the operation "Set-ADAccountPassword" on target "CN=Sophie,OU=Sales,OU=THM,DC=thm,DC=local".


# With this command we are enabling the requirement to enter a new password upon login.

Set-ADUser -ChangePasswordAtLogon $true -Identity sophie -Verbose

#VERBOSE: Performing the operation "Set" on target "CN=Sophie,OU=Sales,OU=THM,DC=thm,DC=local".
```
<br>

| Managing Computers in AD |
| - |

> By default, all the machines that join a domain (except for the DCs) will be put in the container called "Computers".
>
> We can see some servers, some laptops and some PCs corresponding to the users in our network. Having all of our devices there is not the best idea since it's very likely that you want different policies for your servers and the machines that regular users use on a daily basis.

> While there is no golden rule on how to organise your machines, an excellent starting point is segregating devices according to their use. In general, you'd expect to see devices divided into at least the three following categories:
>
>> Workstations - Are one of the most common devices within an Active Directory domain. Each user in the domain will likely be logging into a workstation. This is the device they will use to do their work or normal browsing activities. These devices should never have a privileged user signed into them.
>>
>> Servers - Are the second most common device within an Active Directory domain. Servers are generally used to provide services to users or other servers.
>>
>> Domain Controllers - Are the third most common device within an Active Directory domain. Domain Controllers allow you to manage the Active Directory Domain. These devices are often deemed the most sensitive devices within the network as they contain hashed passwords for all user accounts within the environment.

