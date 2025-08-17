# Advanced PowerShell Study Notes

A complete guide to PowerShell from basics to expert level.  
Covers cmdlets, scripting, error handling, modules, remoting, automation, and DevOps use cases.

---

## 1. PowerShell Basics (Refresher)

### 1.1 Cmdlets
- PowerShell commands are called **cmdlets**.
- Syntax: `Verb-Noun`
- Examples:
  ```powershell
  Get-Command            # List available cmdlets
  Get-Help Get-Process   # Show help for a cmdlet
  Get-Service            # List services
  Start-Service Spooler  # Start a service
  ```



### 1.2 Variables

#### Variables are declared with $
```powershell
        $name = "Felix"
        $age = 25
        $array = 1,2,3,4
        $hash = @{ Name="Felix"; Role="DevOps" }
```


### 1.3 Pipeline
- Unlike Linux, PowerShell passes objects through pipelines.
``` powershell
Get-Process | Where-Object {$_.CPU -gt 100} | Sort-Object CPU -Descending
```

### Conditionals & Loops
```powershell
if ($x -gt 5) { "Big" } else { "Small" }

for ($i=1; $i -le 5; $i++) { $i }
foreach ($a in $array) { $a }

```

### Functions
```powershell
function Get-Square($n) { return $n*$n }
```

### Files & Text
```powershell
Get-Content file.txt
Set-Content file.txt "Hello"
Add-Content file.txt "Append"
"abc123" -match "\d+"   # Regex
```

### Error Handling
```powershell
try { Get-Item fake.txt } catch { "Error: $_" }
```

### Modules
```powershell
Get-Module -ListAvailable
Install-Module Az
Import-Module Az
```

### Jobs & Scheduling
```powershell
Start-Job { Get-Process }
Get-Job
Receive-Job -Id 1
```

### Remoting & APIs
```powershell
Enter-PSSession -ComputerName Server01 -Credential Admin
Invoke-Command -ComputerName Server01 -ScriptBlock { Get-Service }

Invoke-RestMethod -Uri "https://api.com/data"
```
### JSON / XML
```powershell
$json = Get-Content data.json | ConvertFrom-Json
$xml  = [xml](Get-Content data.xml)
```

### Security
```powershell
Get-ExecutionPolicy
Set-ExecutionPolicy RemoteSigned

$cred = Get-Credential
$pass = Read-Host "Enter Password" -AsSecureString
```

### Cloud & DevOps
```powershell
# Azure
Connect-AzAccount
Get-AzVM

# AWS
Install-Module AWSPowerShell
Get-S3Bucket

# Git
git status
git add .
git commit -m "update"
```

### Desired State Configuration (DSC)
```powershell
Configuration WebServer {
  Node "Server01" {
    WindowsFeature IIS { Name="Web-Server"; Ensure="Present" }
  }
}
```