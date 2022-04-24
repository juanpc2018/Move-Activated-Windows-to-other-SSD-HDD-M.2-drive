# Move-Activated-Windows-to-other-SSD-HDD-M.2-drive

This is Microsoft Official Approved Method,
to transfer an Activated Windows hdd to another New hhd ssd m.2.

there are softwares that doit Automatically,
EaseUS, MiniTool, etc...

This is the Manual Method.
Tools Required:
1) External USB3.0 HDD 
formatted in NTFS
bigger than the C: drive partition usually 1TB or more.
2) USB pen drive 1GB or more.
3) New drive, 
same size or bigger than old C: partition/drive.


WARNING #1.
Do Not use Clonezilla or Gparted
both are amazing softwares,
BUT...
when you copy or clone an Activated Windows,
bit-by-bit, sector-by-sector
Windows Defender Security Detects it´s a Copy or Clone, 
and makes Windows Slow on purpose.
SATA drivers are speed limited, slowed,
pagefile.sys is slowed,
defrag does the opposite,
etc...

WARNING #2
UEFI BIOS
When Windows8.1 or W10 is installed the first time in a
BIOS machine "old" 2010-2013, or Newer with Legacy Mode Active.

Windows Installer BCD creates a BIOS bootloader,
IF want to move Windows to a New M.2 drive requires UEFI Boot,
USB Recovery Pen Drive does Not allow to Move a Bios to UEFI.
aditional steps are required.

Moving Windows in the same machine, New HDD or SSD, 1-step,
Moving Windows to M.2 from Bios machine, is 2-steps or more.


WARNING #3.
OEM Windows License "White Envelope",
when Activated, cannot be moved to another Hardware,
license is Hardware locked.
You need a New OEM license to Activate Windows in another HW.
IF Hardware fails or changes too much, License is lost.
Thats for Companies with lots of PCs with Windows, to avoid stealing Windows HDD/SSD.
But OEM are also used in Pre-Built Machines, to avoid moving Windows to another Machine.

Full Retail Standard Boxed version or Virtual purchased from Microsoft Store Web allows to Move Windows to another HW, just requires Phone reactivation for each New machine.

Enterprise version allows Windows-To-Go WTG "Boot from USB3.0",
limited to approved external USB drives, Not all work.
Some External USB Controller IC like Asmedia AS2105 have a config tool that allows to upgrade the FW and set Config Flags "Activate or Deactivate feaures",
One Flag is to Allow Win8-WTG, disabled by-default in most external USB3.0 cases.


WARNING #4.
Windows8.1 in a MacPro 4,1 2009 or 5,1 2010/2012, 
internal SATA is 3Gbps, 
3 options:
Buy a PCIe to SATA card with UEFI / Bios boot like:
 Sonnet Tempo Dual SATA.
Buy a PCIe to M.2 card,
use internal SATA-II 3Gbps "slow".

Sonnet Tempo PCie is a Big improvement,
has a controller IC between Mac and SSD,
that allows 6Gbps, but... Windows BCD bootloader must be Bios or UEFI, cannot be "All/Both" with Standard Firmware 160120_10_4E_01.
There are Optional Firmwares available 150xxx, 190xxx and 210xxx

Bios Bootloader allows MBR partitions,
UEFI bootloader seems to require GPT partitions.
UEFI+Bios BCD with MBR does Not Boot.

WARNING #5.
Windows10 cannot be installed directly,
overwrites the Mac EFI with a Serial code,
DAMAGES the Mac,
Options:
A) Install in other PC, move the SSD or M.2
B) Install in Virtual Machine .vhdx
create & modify ssd or m.2 Bootloader partition to detect .vhdx file as a real partition.
C) use a software like twocanoes winclone. 

MacPro 6,1 2013
has Apple SSD AHCI mini PCIe propietary connector, 
different than M.2 B-or M-Key connector.

there are adapters some better than others, 
some have problems with Stand-by Resume power.

Anyway... Original Apple drives are AHCI,
M.2 are usually NVMe, that requires OSX HighSierra minimum,
there are 3rd party unoficial NVMe drivers for older OSX, but is unknown if Boots only as Storage drive. 

MacMini 2014 with FusionDrive have SATA-III 6Gbps, and Apple mini PCIe AHCI port, 
SATA-III 6Gbps is 500MB/s, mini PCIe x4 is 800MB/s.

MacMini 2018 and Newer have soldered SSD, 
cannot be upgraded Nor Removed by user.

older MacMini 2010 have SATA-II 3Gbps.
6Gbps does make a big difference.


WARNING #6.
SSD or M.2 
AHCI or NVMe have different Technologies:

SLC rare and most powrer hungry, most expensive.
MLC high-end prosumer, 2-Bits per cell, long lasting, but most are limited to PCIe v3.0 speeds 2600MB/s

TLC cheaper 3-Bits per cell, Balanced between Price vs. Performance,
does Not last as long as MLC, 
but Newer are PCIe v4.0 that allows much faster speeds in New boards.

QLC the cheapest 4-Bits per cell, very slow when used as QLC,
when used constantly "Not as a storage device Only", last very little.
Some have a controller IC that emulates SLC with QLC, increases speed and makes it last longer.

Cheaper TLC does Not have DRAM, very important to minimuze wear and increase speed.
example:
Crucial MX is True TLC SSD,
Crusial BX is cheap TLC SSD.
Samsung 970 Pro is MLC PCIe v3.0
Samsung 980 Pro is TLC PCIe v4.0
WD Black 850 is PCIe v4.0
WD Black 750 is PCIe v3.0
etc...


WARNING #7.
Make anual Back-up / Restore image to external USB3.0 HDD spinning mechanic magnetic drive "differnt technology".
Specially with Cheaper TLC or QLC.

SLC, MLC. TLC, QLC loose information when Stored for long periods of time and Not turned-on in 1 year or less, depends on Storage Temperature, Heat 40°C = Bad.

Magnetic Mechanic discs can tolerate a bit more Heat,
but Not vibration.
Also does Not require to be Turned-On for long periods of Time.
Ferro Magnetic particles does Not change orientation, if Not exposed to a Megnetic field.

----
PROCEDURE:
BIOS to BIOS or UEFI to UEFI Machine
HDD to HDD 
HDD to SSD
SSD to SSD
Same Size or Bigger Destination.

A) Create a System image Backup
Mouse Right Button click in Windows Taskbar / StartUp logo,
Control Panel / System and Security / File History
Connect External USB3.0 drive formatted in NTFS
click: System Image Backup.

B) when System Image Backup is complete,
Eject large Drive,
Instert Small 1GB USB Pen Drive.
click Recovery
Create a Recovery drive "USB"

C) Turn-Off
D) Remove the Old Windows Drive.
E) insert the New Empty Windows Drive.
F) Turn-On, Select USB drive from Boot Menu F11 or F10 in most boards.
G) IF the New Drive is Not Empty,
IF New drive has been formated previously
IF has partitions.
you need to enter Command Line:
DISKPART
list disk
select disk 0 or 1 "the disk that maches the size, brand"
list partition
list volume
list disk again to see a * next to the disk selected

type clean only when you are absolutely sure.
clean will wipe the entire drive empty,
will Not ask confirmation.

then type exit to exit Diskpart
type exit again to exit Command line.

the procede with System Restore.
instert the Big USB3.0 drive with the System Restore image backup
Exclude the USB pen drive.
continue,
when computer reboots remove the USB pen drive before enters the Bios boot screen.
or probably will return to USN Recovery.
Turn-Off.
Remove both USB drives.
Turn-On.
DONE.

Sometimes Windows will require Phone Reactivation.
usually if moving HDD to HDD,
but Not when moving HDD to SSD.
Must be connected to Internet to Windows "Detect Activation".

-----
PROCEDURE:
Big Size to Smaller
Inside Windows, before everything else,
Move all personal Files Out to an External USB3.0 hdd
Make a System Image Restore Backup.
In Disk Management,
Shrink Volume.
Reboot to confirm everythin is working OK.
Then continue with Standard Procedure, create a New System Restore Image Backup.

-----
PROCEDURE:
BIOS to UEFI

Make a System Image Recovery Backup
Reboot with Original HDD,
Boot to Windows Recovery USB drive,
go to Command Line
DISKPART
list disk
Select proper disk
list partition
select small boot partition
list volume 
select proper boot volume
list again to see * next to all.
list disk
list volume
list partition

NEVER TYPE CLEAN
NEVER TYPE CLEAN.
NEVER TYPE CLEAN.

NEVER TYPE ERASE DISK.
NEVER TYPE ERASE DISK.
NEVER TYPE ERASE DISK.


type Erase Selected * Small Boot Partition

create a new boot partition with 
bcdedit /help

Boot partition must be /UEFI 
/ALL = Bios+UEFI for PC Boards,
Not Macs.
/Bios if want to create a standard Bios Legacy Boot Partition.
Not compatible with M.2 NVMe drives.
M.2 NVMe requires UEFI Boot.

HDD SSD works with Bios Legacy or UEFI, depends on the Board.

M.2 AHCI can Boot BIOS legacy.
M.2 AHCI are rare, old & discontinued.

