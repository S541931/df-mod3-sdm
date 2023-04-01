# df-mod3-sdm

For all Exercises, you can find my files in the respective folders.
I will be using "PS:" as an abbreviation for "PS C:\Users\s541931\Documents\Spring2023\DigitalForensics\GithubRepositories\df-mod3-sdm-1>:"

## Exercise 1: Digital Forensics
Use Get-WinEvent to collect event logs from a remote or local computer. Redirect the output to a text file. 

PS: Get-WinEvent -ListLog * | Out-File -Path C:\Users\s541931\Documents\Spring2023\DigitalForensics\GithubRepositories\df-mod3-sdm-1\E1_DigitalForensics\Get-WinEvent.txt

Use Get-Content and Select-String to search for specific text within the generated text file.

PS: Get-Content Get-WinEvent_Setup_Formatted.txt | Select-String -Pattern "Microsoft-Windows-SetupQueue" | Out-File -Path C:\Users\s541931\Documents\Spring2023\DigitalForensics\GithubRepositories\df-mod3-sdm-1\Get-Content_Setup.txt

Pipe Get-WinEvent to Where-Object to filter items in a pipeline. 

PS: Get-WinEvent -LogName System | Where-Object {$_.ID -like '7040'} | Out-File -Path C:\Users\s541931\Documents\Spring2023\DigitalForensics\GithubRepositories\df-mod3-sdm-1\Get-WhereObject.txt  

Use Export-Csv command to export data to a CSV file. 

PS: Get-WinEvent -LogName System | Where-Object {$_.ID -like '7040'} | Export-Csv -Path C:\Users\s541931\Documents\Spring2023\DigitalForensics\GithubRepositories\df-mod3-sdm-1\Get-WhereObject.cvs


## Exercise 2: File Systems
Use the mkdir command to create a new directory at the specified path.

PS: mkdir DemoFile

Use the copy command to copy a file from the source path to the destination path.

PS: Copy-Item "C:\Users\s541931\Documents\Spring2023\DigitalForensics\GithubRepositories\df-mod3-sdm-1\E2_FileSystems\DemoFile\mkdir.PNG" -Destination "C:\Users\s541931\Documents\Spring2023\DigitalForensics\GithubRepositories\df-mod3-sdm-1\E2_FileSystems"

Use the Get-Acl command to retrieve the access control list (ACL) for a file or directory.

PS: Get-Acl "C:\Users\s541931\Documents\Spring2023\DigitalForensics\GithubRepositories\df-mod3-sdm-1\E2_FileSystems\DemoFile\mkdir.PNG"

Use the Export-Csv command to export data to a CSV file.

PS: Get-Date | Select-Object -Property DateTime, Day, DayOfWeek, DayOfYear |                                                             
> > Export-Csv -Path C:\Users\s541931\Documents\Spring2023\DigitalForensics\GithubRepositories\df-mod3-sdm-1\E2_FileSystems\CvsExport_DateTime.csv -NoTypeInformation

## Exercise 3: Secure Data Management
Use the ConvertTo-SecureString command to encrypt sensitive data.

PS: Get-Content C:\Users\s541931\Documents\Spring2023\DigitalForensics\GithubRepositories\df-mod3-sdm-1\E3_SecureDataManagement\SensitiveData.txt | ConvertTo-SecureString -AsPlainText -Force | ConvertFrom-SecureString | Out-File C:\Users\s541931\Documents\Spring2023\DigitalForensics\GithubRepositories\df-mod3-sdm-1\E3_SecureDataManagement\ConvertTo-SecureString_EncryptedData.txt -NoNewline

Use the Get-Acl command to retrieve the access control list (ACL) for a file or directory.

PS: Get-Acl "C:\Users\s541931\Documents\Spring2023\DigitalForensics\GithubRepositories\df-mod3-sdm-1\E2_FileSystems\E3_SecureDataManagement\ConvertTo-SecureString_EncryptedData.txt"

Use the icacls command to set or modify the access control list (ACL) for a file or directory.

PS: icacls C:\Users\s541931\Documents\Spring2023\DigitalForensics\GithubRepositories\df-mod3-sdm-1\E3_SecureDataManagement\ConvertTo-SecureString_EncryptedData.txt /setintegritylevel l
