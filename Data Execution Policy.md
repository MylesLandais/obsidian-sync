- Data Execution Prevention (DEP) is a system-level memory protection feature 

- DEP prevents code from being run from data pages such as the default heap, stacks, and memory pools. If an application attempts to run code from a data page that is protected, a memory access violation exception occurs, and if the exception is not handled, the calling process is terminated.

``` 
PS C:\Windows\system32> bcdedit /enum

Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=\Device\HarddiskVolume2
path                    \EFI\Microsoft\Boot\bootmgfw.efi
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
default                 {current}
resumeobject            {e8c79ed5-f95d-11ea-95cf-92f9ffb889ac}
displayorder            {current}
toolsdisplayorder       {memdiag}
timeout                 30

Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \Windows\system32\winload.efi
description             Windows 10
locale                  en-US
inherit                 {bootloadersettings}
recoverysequence        {e8c79ed7-f95d-11ea-95cf-92f9ffb889ac}
displaymessageoverride  Recovery
recoveryenabled         Yes
isolatedcontext         Yes
allowedinmemorysettings 0x15000075
osdevice                partition=C:
systemroot              \Windows
resumeobject            {e8c79ed5-f95d-11ea-95cf-92f9ffb889ac}
nx                      OptIn
bootmenupolicy          Standard
```

bcdedit.exe is a Windows utility for editing boot configuration data, hence bdcedit.

/set tells bcedit to set an option value entry in the boot configuration.

{current} tells becedit to work with the boot configuration being used right now.

nx is short for no execute and is the setting name for DEP in the boot configuration.

AlwaysOff is self-explanatory.

    Restart the computer.
    DEP will now be completely, and permanently off.