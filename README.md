# PSLongPath
Powershell Script which reveals long paths on a drive

# Which PowerShell Version is required?
This script is utilising WinForms from C#, therefore it requires PowerShell v5.1

# Should I run this in an elevated terminal?
Yes you should. In order to retrieve the MFT file from the hard disk, administrator rights are required.

# How can it be so fast?
On my tests it took less than 60 seconds to scan my C: and read 700k+ files. The technology behind this is the same that is being used by the likes of TreeSize, WizTree etc. Instead of scanning the whole disk and creating threads upon threads to get the results, my script with the help of PowerForensicsV2 reads the MFT of the hard drive. 
>[https://github.com/Invoke-IR/PowerForensics](https://github.com/Invoke-IR/PowerForensics)

# Why versions after 1.2 are slower?
This is because the scan folder feature was introduced and the code had to be changed to accomodate this need.

# How to use
Download the script (.ps1) and open a command prompt on the folder where you've downloaded it. 
Type in 

> powershell.exe -executionPolicy Bypass -File PSLongPath.ps1

A form will appear and the rest is self explanatory. 
Select your drive, set the least path length from which you want to create your report and click Scan Drive.
After the initial scan has finished you will be able to Export to CSV and to HTML.

The Export to HTML is using the PSWriteHTML from EvotecIT
> [https://github.com/EvotecIT/PSWriteHTML](https://github.com/EvotecIT/PSWriteHTML)

From the HTML file you can then export to Excel, CSV if you want, PDF, filter it and more. Please note that if you have a lot of files returned, the HTML file might become large. On my tests for 30k files, it rendered a 7MB file, which Chrome was struggling to open on a Ryzen 7 3700X, 16GB RAM with NVMe SSD.

# What's that settings.ini file created next to the script file?
This ini file stores settings, currently only the file path length. Without it the script runs fine, so if you delete it don't worry. 

# Is it stable?
Currently, I have only been able to test this on my personal computer and it won't work with network drives which you don't have physically attached to the computer. I guess VMDKs and VHDs on VMs should work fine. If you test it and it works on your environment, please drop me a message or create a new issue and give me the details, so I can update this section.

# Where was the icon taken from?
See below:
> <a target="_blank" href="https://icons8.com/icons/set/happy-document">Winking Document icon</a> icon by <a target="_blank" href="https://icons8.com">Icons8</a>

# Tips

 - If you click on the first column, it will open the parent folder of the file.
 - Keyboard Shortcuts

| Keys | Function |
|--|--|
| Ctrl + X | Close Window |
| Ctrl + S | Export to C**S**V |
| Ctrl + H| Export to **H**TML |
| Ctrl + I | Open About Form |
| Ctrl + F | Scan **F**older |
| Ctrl + P | Open O**p**tions Form |

# Screenshots
Scan Drive

![Results](https://i.imgur.com/2HHCeXF.png)

Scan Folder

![File](https://i.imgur.com/5uwYzvt.png)

![File](https://i.imgur.com/Gl1ydR3.png)

About

![About](https://i.imgur.com/97WvtNu.png)
