# Azure AD B2C PowerShell module

This module utilizes the Azure AD B2C REST API to manage managing B2C policies from the PowerShell commandline or Azure DevOps. 
See https://docs.microsoft.com/en-us/graph/api/resources/trustframeworkpolicy?view=graph-rest-beta for the API specification. 
For more info support@fortigi.nl

This module will work in both PowerShell 5.0 as well as PowerShell 6.0 and will therefor work on both Windows, Mac and Linux. No aditional modules are required.

This module requires you to authenticate using a ServicePrincipal, Secret and TenantID. 
To create a ServicePrincipal using the Az module run the following commands;

```powershell
Connect-AzAccount

$Secret = '<Secret>'
$ServicePrincipleName = '<ServicePrincipal>'
$credentials = New-Object Microsoft.Azure.Commands.ActiveDirectory.PSADPasswordCredential -Property @{ StartDate=Get-Date; EndDate=Get-Date -Year 2024; Password=$Secret}
$sp = New-AzAdServicePrincipal -DisplayName $ServicePrincipleName -PasswordCredential $credentials
```

After this you will need to authorize your ServicePrincipal to "Read and write your organization's trust framework policies". To do that open the Azure Portal. Open App registraitons (Legacy) > Select all apps > Find your app > go to settings > required permissions > Microsoft Graph > Select "Read and write your organization's trust framework policies" click add and click grant permissions.



* Supported functions
  - Get-AADB2CPolicy
  - New-AADB2CPolicy
  - Remove-AADB2CPolicy

