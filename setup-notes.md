# Linux Dual Boot 
This file is for logging the dual boot I set up for my Lenovo LOQ 15AHP. Now I had heard a lot about dual booting, but I was hesitant in setting it up at the start 
because of the laptop being new and I did not want to wipe out windows accidentally, which I had done for my older laptop. But I took the leap and managed to get it 
setup as I wanted, with some minor hiccups along the way. 

## Process 1 
First I had to choose an OS to install on the system. I was already aware of Ubuntu due to my previous install, so I asked Gemini (PS, I relied heavily on it) which OS 
to install. Out of a few choices, I settled in on Pop_OS (Ver. 24.04) due to preloaded NVIDIA drivers for use with my RTX 5060. Now the next step was creating space 
on the hard drive. This was an issue which is discussed more in depth in the errors. After creating the space, I moved the iso file of Pop!_OS onto the USB with Ventoy
already there. This meant that now my USB holds both Pop!_OS iso file as well as BookWormPup iso file. However, I cannot boot into the Bookwormpup iso file because of 
the pendrive now being used as a storage instead of being flashed with one OS. Then I booted into the BIOS, put USB as first priority in boot, and loaded into Ventoy to open 
Pop!_OS. Now I did not choose clean install, which would have wiped out the Windows, I chose Custom Install which gave me the option to resize. I created roughly 60 GB of 
space for the OS, based on Gemini's recommendation. After this there was an error in the system, regarding both Windows being unaccessible and keyboard issue on Pop. This is 
described more in depth in errors. After fixing those errors, I wanted access to my windows file, so I asked Gemini how to do it, and I was given commands to execute which
gave me access to my windows data even if I was loaded into Pop. That was it for the process and I must say, Pop is a lot faster than Windows. 

## Errors
### Error 1: Not being able to create space
When I was trying to create space for Pop, I was not able to do effectively. In a bid to resolve this, I learned about something called Disk Cleanup. This is a inbuilt 
feature in the Windows OS that allows me to manually get rid of files. Now I am not sure what type of files they are, but I do know that removing those files did not affect
my Windows Performance in any known way. So I can always use that to clean up space. However, this was still not enough, there was some file that was just refusing to move 
from the end of the Disk Space so that I could create a partition. So I installed Gparted-live. This is an application that allows me to force the files to move so that I 
can make space. Gparted solved the issue of space and thus I could move forward. 

### Error 2: Keyboard Issue 
I do not even know how to describe this issue, and it is still there, thankfully it is just there for 2 keys. Basically `@` and `'` are exchanged on the keyboard. I have 
zero clue why, and I think I might fix it in the future, but for now, I don't intend on changing it.

### Error 3: Windows not being visible in GRUB 
This is actually a mix of two errors, first one is that there is no GRUB with Pop_OS, its with Ubuntu. Pop_OS uses something called as `systemd-boot`, I have no clue what 
that is, maybe I will study deeper into it later. The second error being that `systemd-boot` could not notice Windows existed on the same boot folder. So I manually copied Windows OS
onto the boot folder using `sudo cp -ax /mnt/EFI/Microsoft /boot/efi/EFI/`. This solved the issue and now I have 5 secs at the start to choose an OS. 

### Error 4: Trello not existing as a Linux App
Trello does not exist as an app for Linux. A bypass for this was that I can open it on the Browser, but it becomes a headache everytime. So I learned that I can install
a web page as app on the system and access it everytime. This was one of the craziest things I learned in the entire boot.


## Process 2 
Now after having dealt with the setup for the first time. I knew how to do the setup better the second time around. This time I ran into just 2 hiccups and I will detail them here as well. I removed the dual boot set up 
because I wanted more space to be able to play God of War: Ragnarok. Then I also had to enable bit locker and device encryption because I wanted to play Valorant. These two were the issues. 

## Errors
### Error 1: BitLocker enabled 
This was a pretty simple fix. I was actually trying to create space with Gparted live. However, I was not able to edit the partitions. This was because BitLocker was enabled so I logged into Windows and disabled Device
Encryption. After that I also disabled Secure Boot from BIOS menu to ensure smooth partitioning. 

### Error 2: /boot/efi partition
Now this was a new error for me, but this could be solved after using AI's help. This error occured because we need to select atleast two partitions, one for Root(ext4 filesystem) and one for Boot(fat32 filesystem). 
The boot partition was supposed to be bigger than 1GBs, but I was trying to use the Windows partition only which was smaller than 1 gig. So I had to create a new Boot partition and made that as the Boot Partition. This 
solved the problem.

### Note on Error 2 of process 1
I fixed this error in setup this time and now the keyboard keys are not switched. By being aware of the issue and being on the active lookout for it, I could solve it by choosing the correct keyboard and testing it out.

## Commands ran (After booting into Pop_OS)
1. `sudo apt update && sudo apt upgrade -y` - This is the basic command to update and upgrade all the packages after installtion to ensure optimum operation.
2. `sudo apt install -y git curl wget build-essential` - This is again a basic command used to set up a development machine. Here `sudo` is used to run the command with administrator privileges, `apt` is the packages 
manager, `install` is the command, `-y` automatically answers yes to all prompts. `git` is the version control system used for tracking changes in code and cloning repos. `curl` is a command line tool for transferring data
to and from URLs. `wget` is command line utility for downloading files from the web. `build-essential` is the meta-package that installs essential development tools, including GNU/C++ compiler and related libraries needed
to compile software.
3. `sudo apt install -y python3.11 python3.11-venv python3-pip` - This command works very similar to the previous command and installs Python Interpreter, support for creating isolated python virtual environments using 
`venv` and `pip` package manager for installing Python packages from PyPI
4. `python3 --version \t git --version` - This was used to verify the installation by simply checking version. 

5. I also installed VSCode for Linux by first installing a Debian package from the internet and then unpacking it by using the command `sudo dpkg -i code*.deb`. Here `dpkg` is a low level Debian package management tool and
`-i` is the flag for installing. Apart from this, I also added 3 extensions to the VSCode, GitLens, Python and Jupyter.

6. Afterwards, I created SSH keys and added it to the GitHub website so I can access the repositories and make changes directly from the command line. 
`ssh-keygen -t ed25519 -C "mishraishaan283@gmail.com"` - This command is used to generate a SSH key with comment being identified by `-C` flag.
`eval "$(ssh-agent -s)"` - This command runs a background process that stores decrypted SSH keys in memory. `eval` executes environment variable settings output by `ssh-agent`. Keep in mind that the process started by 
`ssh-agent` is not closed when terminal is closed and it needs to be started at every new terminal. Use `pkill ssh-agent` to kill all running ssh-agents. 
`ssh-add ~/.ssh/id_ed25519` - This command then add the private key to the `ssh-agent` that was started and allows you to freely communicate with your repository without needing to worry about adding private key again 
and again. 


## Summary 
Overall it was a learning experience, insanely satisfying, and definitely a lot faster than my first boot process. I do have more stuff to learn about, will do it later
on, but for now, I am done.

# Git useful commands and SOPs
## Updating branch in both local and remote
 # Rename locally
 `git branch -m master main`

 # Push new branch to remote
 `git push origin main`
 
 # Set remote tracking
 `git push origin -u main`

 # Delete old branch on remote
 `git push origin --delete master`

 # Set default branch on GitHub to main
 # (Settings → Branches → Default branch) 

Use the above sequence to rename a branch from master to main on local, then to push it to remote. After that, setup remote tracking and then go to settings and change default branch. Afterwards, delete branch on remote.
