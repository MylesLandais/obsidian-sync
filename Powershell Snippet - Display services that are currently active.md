202112181608
Status: #bookmarks
Tags:
Content-Type:
Source: 

# Powershell Snippet - Display services that are currently active

### Example 5: Display services that are currently active

This example displays only the services with a status of Running.

PowerShell

```
Get-Service | Where-Object {$_.Status -eq "Running"}
```

`Get-Service` gets all the services on the computer and sends the objects down the pipeline. The `Where-Object` cmdlet, selects only the services with a **Status** property that equals Running.

Status is only one property of service objects. To see all of the properties, type `Get-Service | Get-Member`.

---
# Refrences
https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-service?view=powershell-7.2