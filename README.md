# AD-Automation-with-Powershell
AD Automation with Powershell
PowerShell
# == User Details ==
# This is the only section you need to edit for each new user.
$firstname = "Jane"
$lastname = "Doe"
$username = "jdoe"
$password = "P@ssword1234!"
$domainName = "skool.local"

# == Create the Active Directory User ==
# This section takes the details above and creates the account.

# 1. Convert the password to a secure string required by Active Directory.
$securePassword = ConvertTo-SecureString $password -AsPlainText -Force

# 2. Create the user with all the specified attributes.
# The command `New-ADUser` is the main instruction to create the account.
New-ADUser -Name "$firstname $lastname" `
           -GivenName $firstname `
           -Surname $lastname `
           -SamAccountName $username `
           -UserPrincipalName "$username@$domainName" `
           -AccountPassword $securePassword `
           -Enabled $true

# 3. Print a confirmation message to the screen.
Write-Host "User '$username' was created successfully."

