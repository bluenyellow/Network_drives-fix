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
