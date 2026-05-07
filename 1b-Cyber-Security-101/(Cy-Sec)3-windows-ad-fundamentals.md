
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

> + *Part of having an overview is knowing what types of users are in the system and how they are configured. What type of permissions do they have, what access do they have, and what groups do they belong to...*
<br>

| User Account Control |
| - |

