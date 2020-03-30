# ps-sort-json
Powershell module that will sort JSON using JSON.NET.


## Installation
The following script below will download the powershell binary module to temp directory and load it into your powershell session with all needed utilities such as JSON.NET version 12.0.3.23909

```powershell
#Download the module
iwr -uri "https://raw.githubusercontent.com/TheUniquePaulSmith/ps-sort-json/master/TheUniquePaulSmith.PowerShell.Commands-Merged.dll" `
 -OutFile "$([System.IO.Path]::GetTempPath())TheUniquePaulSmith.PowerShell.Commands-Merged.dll"; 

#Import the module
Import-Module "$([System.IO.Path]::GetTempPath())TheUniquePaulSmith.PowerShell.Commands-Merged.dll"
```

Alternatively you can manually download the DLL and reference the path for import-module.
In the future when I have time to clean up the package i'll add it to nuget\PowerShell and remove the merged JSON.NET

## Usage

**Sort-JSON** can be piped or declared inline. Start with a JSON object, you can use below for reference, it can be either a string or string[] type

```powershell
$jObj = @'
{
zTest: "Value1",
cTest: [
    "z",
    1,
    "3"
],
aTest: "Value2"
}
'@                   
```

Convert string to sorted JSON string

```powershell
$jObj | Sort-JSON
```

Can also be explicit with or without named parameters

```powershell
Sort-JSON -InputObject $jObj 
```

## Disclaimer / Issues
While I have not seen any issues with sorting JSON, I'd still validate that the sort does not affect the data integrity of the original JSON document
If you a discover an issue please add to issues list