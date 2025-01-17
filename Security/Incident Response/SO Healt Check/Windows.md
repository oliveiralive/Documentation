### Verificar usuarios locais

```
$localUsers = Get-WmiObject -Class Win32_UserAccount
$date = Get-Date -Format "dd/MM/yyyy HH:mm"
foreach ($user in $localUsers) {
    $name = $user.Name
    $status = if ($user.Disabled) { "Disabled" } else { "Enabled" }
    $accountType = if ($user.LocalAccount) { "Local" } else { "Domain" }
    $message = "$date - Check-Users: Name: $name, Status: $status, AccountType: $accountType"
    Write-Output $message
}
```
