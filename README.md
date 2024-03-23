# df-mod3-sdm

[ADD INTRO PARAGRAPH]

## Exercise 1

[1/2/3] View all logs on your computer: ```Get-WinEvent -ListLog *```

[4] Gathers everything from a application log and saves it to a file: ```Get-WinEvent -LogName Application | Out-File -FilePath "c:\Users\matth\OneDrive\Documents\df-mod3-sdm-1\exercise-1\logs.txt"```

[5] Search for specific text within the newly created text file: ```Get-Content -Path "c:\Users\matth\OneDrive\Documents\df-mod3-sdm-1\exercise-1\logs.txt" | Select-String -Pattern "Warning"```

[6] Pipe Get-WinEvent to Where-Object: ```Get-WinEvent -LogName Application | Where-Object {$_.LevelDisplayName -eq "Warning"} | Export-Csv -Path "c:\Users\matth\OneDrive\Documents\df-mod3-sdm-1\exercise-1\filtered-logs.csv" -NoTypeInformation```

## Exercise 2

Create a new directory: ```mkdir exercise-2```

Copy a file: ```Copy-Item -Path "c:\Users\matth\OneDrive\Documents\df-mod3-sdm-1\exercise-1\logs.txt" -Destination "c:\Users\matth\OneDrive\Documents\df-mod3-sdm-1\exercise-2\logs.txt"```

Retrieve the access control list: ```Get-Acl -Path "c:\Users\matth\OneDrive\Documents\df-mod3-sdm-1\exercise-2\logs.txt"```

Export data to a CSV file: ```Get-Acl -Path "c:\Users\matth\OneDrive\Documents\df-mod3-sdm-1\exercise-1" | Export-Csv -Path "c:\Users\matth\OneDrive\Documents\df-mod3-sdm-1\exercise-2\exercise-1.csv"```

[EXPLAIN THINGS HERE]


## Exercise 3

Encrypt sensitive data: $file = Get-Content -Path "c:\Users\matth\OneDrive\Documents\df-mod3-sdm-1\exercise-3\original.txt" -Raw

ConvertTo-SecureString -String $file -AsPlainText -Force | ConvertFrom-SecureString | Out-File "c:\Users\matth\OneDrive\Documents\df-mod3-sdm-1\exercise-3\secret.txt"

Retrieve access control list: ```Get-Acl -Path "c:\Users\matth\OneDrive\Documents\df-mod3-sdm-1\exercise-3\secret.txt"```

modify access control list: ```Invoke-Expression "icacls "c:\Users\matth\OneDrive\Documents\df-mod3-sdm-1\exercise-3\secret.txt" /grant:r 'User:(R)'"```

[EXPLAIN THINGS HERE]