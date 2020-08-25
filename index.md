Explanation of a problem:

One of updates(I think) cause disconnecting network drives after reboot. A little red cross appears on the network drive icon, and it is not possible to open network drive. The device name is already in use appears.

-Things I tried to solve this:

-Remapping drives to other letters
-Finding phantom mounted drives in registry
-Mounting drives through powershell(net use)

-Nothing works


Pressure of time was immense(it was in work environment), so I must bring the solution.

Explanation of solution:

The script below needs to run from Task Scheduler as action invited by event 10000(Microsoft-Windows-NetworkProfile/Operational), which is change of network connection.
Script deletes previously created drive mappings and Shortcuts from desktop, then create them again.
Yes, it is "duck tape" repair, but it works.

```
net use H: /delete
net use U: /delete
Remove-Item -Force "C:\Users\user\Desktop\H_disk.lnk"
Remove-Item -Force "C:\Users\user\Desktop\U_disk.lnk"

net use H: \\path\share
net use U: \\path\share


$TargetFile = "H:\"
$ShortcutFile = "C:\Users\user\Desktop\H_disk.lnk"
$WScriptShell = New-Object -ComObject WScript.Shell
$Shortcut = $WScriptShell.CreateShortcut($ShortcutFile)
$Shortcut.TargetPath = $TargetFile
$ShortCut.IconLocation = "C:\WINDOWS\system32\imageres.dll, 28";
$Shortcut.Save()


$TargetFile = "U:\"
$ShortcutFile = "C:\Users\user\Desktop\U_disk.lnk"
$WScriptShell = New-Object -ComObject WScript.Shell
$Shortcut = $WScriptShell.CreateShortcut($ShortcutFile)
$Shortcut.TargetPath = $TargetFile
$ShortCut.IconLocation = "C:\WINDOWS\system32\imageres.dll, 28";
$Shortcut.Save()
```
