#shutdown

  Shutdown and reboot the system.

  - Power off (halt) immediately:
    `shutdown -h now`

  - Reboot immediately:
    `shutdown -r now`

  - Reboot in 5 minutes:
    `shutdown -r +5 &`

  - Shutdown at 1:00 pm (Uses 24h clock):
    `shutdown -h 13:00`

  - Cancel a pending shutdown/reboot operation:
    `shutdown -c`
    
SEE: https://serverfault.com/a/787208  

`shutdown -r now 'Kernel upgrade requires reboot'`  
`shutdown -r 22:00 'Work around kernel memory leak'`  