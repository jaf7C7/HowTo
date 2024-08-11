# How To Make Ctrl-Backspace Work In VSCode Terminal

If you have admin access, run the following in an administrator powershell terminal:
```powershell
PS > Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
```

Powershell will now execute startup commands from your profile, located at `%USERPROFILE%\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1`

Add the following to your profile:
```powershell
if ($Env:TERM_PROGRAM -eq "vscode") {
	"Set-PSReadLineKeyHandler -Chord 'Ctrl+w' -Function BackwardKillWord"
}
```

If you don't have admin access and your administrator can't or won't do it for you, add the following to your VSCode `settings.json`:
```json
{
	"terminal.integrated.profiles.windows": {
		"Powershell (VSCode)":  {  // <-- This can be whatever you like.
			"path": "powershell.exe",
			"args": [
				"-NoExit",
				"-Command",
				"Set-PSReadLineKeyHandler -Chord 'Ctrl+w' -Function BackwardKillWord"
			]
		}
	}
}
```
