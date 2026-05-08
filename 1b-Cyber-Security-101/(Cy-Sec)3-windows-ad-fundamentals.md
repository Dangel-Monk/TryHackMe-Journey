
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

+ *Another thing to consider is the startup and recovery logs. I can imagine a situation where we make a mistake by modifying system settings that prevents it from working correctly. Or perhaps there is some benefit to obtaining extra information by deliberately causing problems.
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
>
> 
