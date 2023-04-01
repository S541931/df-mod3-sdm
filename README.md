# df-mod3-sdm

#### For all Exercises, you can find my files in the respective folders.
#### I will be using "PS:" as an abbreviation for: "PS C:\Users\s541931\Documents\Spring2023\DigitalForensics\GithubRepositories\df-mod3-sdm-1>:"

## Exercise 1: Digital Forensics
* Use Get-WinEvent to collect event logs from a remote or local computer. Redirect the output to a text file. 
  - PS: Get-WinEvent -ListLog * | Out-File -Path C:\Users\s541931\Documents\Spring2023\DigitalForensics\GithubRepositories\df-mod3-sdm-1\E1_DigitalForensics\Get-WinEvent.txt
* Use Get-Content and Select-String to search for specific text within the generated text file.
  - PS: Get-Content Get-WinEvent_Setup_Formatted.txt | Select-String -Pattern "Microsoft-Windows-SetupQueue" | Out-File -Path C:\Users\s541931\Documents\Spring2023\DigitalForensics\GithubRepositories\df-mod3-sdm-1\Get-Content_Setup.txt
* Pipe Get-WinEvent to Where-Object to filter items in a pipeline. 
  - PS: Get-WinEvent -LogName System | Where-Object {$_.ID -like '7040'} | Out-File -Path C:\Users\s541931\Documents\Spring2023\DigitalForensics\GithubRepositories\df-mod3-sdm-1\Get-WhereObject.txt  
* Use Export-Csv command to export data to a CSV file. 
  - PS: Get-WinEvent -LogName System | Where-Object {$_.ID -like '7040'} | Export-Csv -Path C:\Users\s541931\Documents\Spring2023\DigitalForensics\GithubRepositories\df-mod3-sdm-1\Get-WhereObject.cvs


## Exercise 2: File Systems
* Use the mkdir command to create a new directory at the specified path.
  - PS: mkdir DemoFile.
  - With this command you can create a folder where you need it without leaving PowerShell.
* Use the copy command to copy a file from the source path to the destination path.
  - PS: Copy-Item "C:\Users\s541931\Documents\Spring2023\DigitalForensics\GithubRepositories\df-mod3-sdm-1\E2_FileSystems\DemoFile\mkdir.PNG" -Destination "C:\Users\s541931\Documents\Spring2023\DigitalForensics\GithubRepositories\df-mod3-sdm-1\E2_FileSystems"
  - With the Copy command you could copy evidence without leaving PowerShell.
* Use the Get-Acl command to retrieve the access control list (ACL) for a file or directory.
  - PS: Get-Acl "C:\Users\s541931\Documents\Spring2023\DigitalForensics\GithubRepositories\df-mod3-sdm-1\E2_FileSystems\DemoFile\mkdir.PNG"
  -With this command you can check the file permissions for a file, this will let you know if you need to make any changes. 
* Use the Export-Csv command to export data to a CSV file.
  - PS: Get-Date | Select-Object -Property DateTime, Day, DayOfWeek, DayOfYear | >> Export-Csv -Path C:\Users\s541931\Documents\Spring2023\DigitalForensics\GithubRepositories\df-mod3-sdm-1\E2_FileSystems\CvsExport_DateTime.csv -NoTypeInformation
  -This will let you Export any information obtained with a PowerShell command into a .csv File.

## Exercise 3: Secure Data Management
* Use the ConvertTo-SecureString command to encrypt sensitive data.
  - PS: Get-Content C:\Users\s541931\Documents\Spring2023\DigitalForensics\GithubRepositories\df-mod3-sdm-1\E3_SecureDataManagement\SensitiveData.txt | ConvertTo-SecureString -AsPlainText -Force | ConvertFrom-SecureString | Out-File C:\Users\s541931\Documents\Spring2023\DigitalForensics\GithubRepositories\df-mod3-sdm-1\E3_SecureDataManagement\ConvertTo-SecureString_EncryptedData.txt -NoNewline
  -Took inspiration from Cody's ConvertTo-SecureString command.
  -This Can be used to Encrypt a string or text file to secure information.
* Use the Get-Acl command to retrieve the access control list (ACL) for a file or directory.
  - PS: Get-Acl "C:\Users\s541931\Documents\Spring2023\DigitalForensics\GithubRepositories\df-mod3-sdm-1\E2_FileSystems\E3_SecureDataManagement\ConvertTo-SecureString_EncryptedData.txt"
  - With this command you can check the file permissions for a file, this will let you know if you need to make any changes. 
  - This should not be used for finding out who had access to a file if it is possible the file permissions have been altered.
* Use the icacls command to set or modify the access control list (ACL) for a file or directory.
  - PS: icacls C:\Users\s541931\Documents\Spring2023\DigitalForensics\GithubRepositories\df-mod3-sdm-1\E3_SecureDataManagement\ConvertTo-SecureString_EncryptedData.txt /setintegritylevel l
  -You may make alterations to file permissions with the icacls command.
