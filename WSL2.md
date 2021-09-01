**Checking your WSL version**

_example output for wsl2 _
```
PS C:\Windows\system32> wsl --status
Default Version: 2

The Windows Subsystem for Linux kernel can be manually updated with 'wsl --update', but automatic updates cannot occur due to yo
ur system settings.
To receive automatic kernel updates, please enable the Windows Update setting: 'Receive updates for other Microsoft products whe
n you update Windows'.
For more information please visit https://aka.ms/wsl2kernel.

The WSL 2 kernel file is not found. To update or restore the kernel please run 'wsl.exe --update'.
```

**Installing a distro**

_example output of installing debian_
```
PS C:\Windows\system32> wsl
Windows Subsystem for Linux has no installed distributions.
Distributions can be installed by visiting the Microsoft Store:
https://aka.ms/wslstore
PS C:\Windows\system32> wsl --list
Windows Subsystem for Linux has no installed distributions.
Distributions can be installed by visiting the Microsoft Store:
https://aka.ms/wslstore
PS C:\Windows\system32> wsl --list --online
The following is a list of valid distributions that can be installed.
Install using 'wsl --install -d <Distro>'.

NAME            FRIENDLY NAME
Ubuntu          Ubuntu
Debian          Debian GNU/Linux
kali-linux      Kali Linux Rolling
openSUSE-42     openSUSE Leap 42
SLES-12         SUSE Linux Enterprise Server v12
Ubuntu-16.04    Ubuntu 16.04 LTS
Ubuntu-18.04    Ubuntu 18.04 LTS
Ubuntu-20.04    Ubuntu 20.04 LTS
PS C:\Windows\system32> wsl --install -d debian
Downloading: Debian GNU/Linux
Installing: Debian GNU/Linux
Debian GNU/Linux has been installed.
Launching Debian GNU/Linux...
```

