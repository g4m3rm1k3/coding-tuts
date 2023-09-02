help add /? after command
```console
rmdir /?
```

show current directory in command prompt
```lisp
dir
```
show contents of subdirectory ex. downloads
```lisp
dir "downloads"
```
use quotations for spaces in names
### change directory
```lisp
cd Downloads // or
chdir Downloads
```
### delete file in command prompt
```lisp
del Downloads\python-fundamentals-main.zip
```
Zip a file
```lisp
tar -a -c -f python-fundamentals.zip python-fundamentals
```
create a file in command prompt
```lisp
echo Michael Mclean > name.txt
```
This creates a file with the text Michael Mclean inside

---
unzip a file
```lisp
ar -xf python-fundamentals.zip
```
move a file
```terminal
move python-fundamentals.zip python-test
```
this will also change a folder name

echo file contents to command prompt
```console
C:\Users\g4m3r\Downloads>type name.txt
Michael Mclean
```

to remove a directory
```console
C:\Users\g4m3r\dev\fundamentals>rmdir /s notebooks
notebooks, Are you sure (Y/N)? Y
```

open file explorer
```console
start .
```
opens the file explorer in the current directory

## create file command prompt
```console
type nul > <filename>
```
## create file powershell
```powershell
New-Item <filename>
```
## check powershell version
```powershell
$PSVersionTable
```
output
```powershell
Name                           Value
----                           -----
PSVersion                      5.1.22621.1778
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
BuildVersion                   10.0.22621.1778
CLRVersion                     4.0.30319.42000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```
## Execution Policy on Powershell
```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser -Confirm
```

# oh my posh
install oh my posh
```powershell
Install-Module oh-my-posh -Scope CurrentUser
```
edit powershell profile
```powershell
notepad $profile
```
install fonts
```powershell
oh-my-posh font install --user
```

get posh themes
```powershell
Get-PoshThemes
```
Add oh my posh to profile
```powershell
Add-PoshGitToProfile -Force
```
## Powershell show hidden files
```powershell
Get-ChildItem . -Force
dir -Force
ls -Force
gci -Force
```
