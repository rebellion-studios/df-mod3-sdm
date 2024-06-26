# df-mod3-sdm

A series of assignments dealing with PowerShell commands several tasks involving SDM.

## Exercise 1

View all logs on your computer:

```Get-WinEvent -ListLog *```

Gathers everything from a application log and saves it to a file:

```Get-WinEvent -LogName Application | Out-File -FilePath "c:\Users\matth\OneDrive\Documents\df-mod3-sdm-1\exercise-1\logs.txt"```

Search for specific text within the newly created text file:

```Get-Content -Path "c:\Users\matth\OneDrive\Documents\df-mod3-sdm-1\exercise-1\logs.txt" | Select-String -Pattern "Warning"```

Pipe Get-WinEvent to Where-Object:

```Get-WinEvent -LogName Application | Where-Object {$_.LevelDisplayName -eq "Warning"} | Export-Csv -Path "c:\Users\matth\OneDrive\Documents\df-mod3-sdm-1\exercise-1\filtered-logs.csv" -NoTypeInformation```

## Exercise 2

Create a new directory:

```mkdir exercise-2```

Copy a file:

```Copy-Item -Path "c:\Users\matth\OneDrive\Documents\df-mod3-sdm-1\exercise-1\logs.txt" -Destination "c:\Users\matth\OneDrive\Documents\df-mod3-sdm-1\exercise-2\logs.txt"```

Retrieve the access control list:

```Get-Acl -Path "c:\Users\matth\OneDrive\Documents\df-mod3-sdm-1\exercise-2\logs.txt"```

Export data to a CSV file:

```Get-Acl -Path "c:\Users\matth\OneDrive\Documents\df-mod3-sdm-1\exercise-1" | Export-Csv -Path "c:\Users\matth\OneDrive\Documents\df-mod3-sdm-1\exercise-2\exercise-1.csv"```

These series of commands copies the contents from one file into another, then gets the ACL from the new file, before converting the data into a CSV file.


## Exercise 3

Encrypt sensitive data:

```$file = Get-Content -Path "c:\Users\matth\OneDrive\Documents\df-mod3-sdm-1\exercise-3\original.txt" -Raw```

```ConvertTo-SecureString -String $file -AsPlainText -Force | ConvertFrom-SecureString | Out-File "c:\Users\matth\OneDrive\Documents\df-mod3-sdm-1\exercise-3\secret.txt"```

Retrieve access control list:

```Get-Acl -Path "c:\Users\matth\OneDrive\Documents\df-mod3-sdm-1\exercise-3\secret.txt"```

modify access control list:

```Invoke-Expression "icacls "c:\Users\matth\OneDrive\Documents\df-mod3-sdm-1\exercise-3\secret.txt" /grant:r 'User:(R)'"```

Modifying the access control list didn't seem to always work. A processing error kept occurring.

These commands encrypt the contents of a file and place in inside another. Then the ACL is retrieved and user privileges are granted to the file.
