# SYSTEM環境変数PATH, ユーザ環境変数PATH を確認

## 手順

```powershell
# PowerShell
Get-WmiObject Win32_Environment | 
  ?{ $_.Name -eq 'Path' } |
  %{ $_.VariableValue = ($_.VariableValue -replace ";","`n"); $_ } | 
  Format-List Name,UserName,VariableValue
```

```ps1
# 出力結果
Name          : Path
UserName      : <SYSTEM>
VariableValue : %SystemRoot%\system32
                %SystemRoot%
                %SystemRoot%\System32\Wbem
                %SYSTEMROOT%\System32\WindowsPowerShell\v1.0\
                %SYSTEMROOT%\System32\OpenSSH\
                C:\Program Files\dotnet\
                C:\Program Files\Git\cmd

Name          : Path
UserName      : NT AUTHORITY\SYSTEM
VariableValue : %USERPROFILE%\AppData\Local\Microsoft\WindowsApps


Name          : Path
UserName      : VM-WIN10\DEVADMIN
VariableValue : %USERPROFILE%\AppData\Local\Microsoft\WindowsApps
                C:\Data\path
                C:\Users\DEVADMIN\AppData\Local\Programs\Microsoft VS Code\bin
                %USERPROFILE%\.dotnet\tools
```
