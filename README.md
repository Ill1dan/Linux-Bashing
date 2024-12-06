# Linux-Bashing

## Navigation

| Command       | Description                        |
|---------------|------------------------------------|
| `ls`          | List directory contents            |
| `cd`          | Change the current directory       |
| `pwd`         | Print the current working directory|

## Disolaying Data

| Command       | Description                        |
|---------------|------------------------------------|
| `cat`         | Displays all data in file          |
| `head`        | Displays the first 10 lines        |
| `echo`        | Displays output from OS            |

## Manage File Content

| Command       | Description                        |
|---------------|------------------------------------|
| `grep`        | Searches for specific string in the line and returns the line          |
| `\|`        | Sends the standard output of one command as standard input to another command for further processing        |
| `find`        | Searches for dir and files        |
| `find -name`        | Finds string name and case sensitive        |
| `find -iname`        | Finds string name and not case sensitive       |
| `find -mtime -d`        | Find files modified in last d days        |
| `locate`        | Find specific file/dir        |

## Create And Modify Directory

| Command       | Description                        |
|---------------|------------------------------------|
| `mkdir`       | Creates a new directory            |
| `rmdir`       | Removes or deletes directory       |
| `touch`       | Creates a new file                 |
| `rm`          | Removes or deletes a file          |
| `mv`          | Moves a file/dir to new location   |
| `cp`          | Copies a file/dir to new location  |
| `nano`        | A text file editor in CLI          |
| `gedit`       | A text file editor in GUI          |

## Standard Output Redirection

| Command       | Description                             |
|---------------|-----------------------------------------|
| `>`           | Overwrites the existing file            |
| `>>`          | Add the content at the end of the file  |

## Authenticate And Authorize Users

| Command       | Description                             |
|---------------|-----------------------------------------|
| `chmod`       | Changes permissions on files and directory  |
| `passwd`       | Change user password  |

## Adding And Deleting User

| Command       | Description                             |
|---------------|-----------------------------------------|
| `sudo`           | Grants elevated permissions temporarily to specific users    |
| `useradd`          | Adds user to the system  |
| `useradd -g`          | Adds user to the default primary group  |
| `useradd -G`          | Adds user to secondary group  |
| `usermod`          | Modify the existing account  |
| `usermod -g`          | Change the primary group  |
| `usermod -G`          | Change the secondary group  |
| `usermod -d`          | Change user home directory  |
| `usermod -l`          | Change login name  |
| `usermod -L`          | Lock the account  |
| `userdel`          | Deletes an user  |
| `userdel -r`          | Deletes the user and also all the files in the home dir of user  |
| `chown`          | Change ownership of file/dir  |
| `su`          | Switch user  |

## Common Network Commands

| Command       | Description                             |
|---------------|-----------------------------------------|
| `ifconfig`           | Shows the ip address, netmask and broadcast, mac address            |
| `iwconfig`          | Shows the details of wireless connections  |
| `ping`          | Sents ICMP traffic to a IP address  |
| `arp -a`          | Shows the IP address associated with the MAC address  |
| `netstat -ano`          | Used to see the connection of the ports  |
| `route`          | Shows where the traffic exits from the gateway to destination  |
| `service`          | Start any service or stop any service  |
| `systemctl`          | Enables any service for the entire time including reboot  |

## Package Manager

| Command       | Description                             |
|---------------|-----------------------------------------|
| `apt -get`           | Find what needs update and can also be upgraded           |

## Help in Linux

| Command       | Description                             |
|---------------|-----------------------------------------|
| `man`           | Displays info on all commands and how they work            |
| `whatis`          | Displays a description of a specific command on a single line  |
| `apropos`          | Searches the manual page distribution for a specified string  |
| `apropos -a`          | Searches the manual page distribution for more than one string  |

## Bashing Example
```bash
#!/bin/bash

for ip in $(seq 1 254); do
    ping -c 1 $1.$ip | grep "64 bytes" | cut -d " " -f4 | tr -d ":" &
done

```
## Explanation

- `#!/bin/bash`: This is a shebang line that tells the system to use the Bash shell to execute the script.
- `for ip in $(seq 1 254); do`: This starts a for loop that iterates over the sequence of numbers from 1 to 254. The seq 1 254 command generates this sequence.
- `ping -c 1 $1.$ip`: This sends a single (-c 1) ping request to the IP address formed by appending the current value of ip to the first argument passed to the script ($1).
- `| grep "64 bytes"`: This pipes the output of the ping command to grep, which filters the output to include only lines containing "64 bytes" (indicating a successful ping response).
- `| cut -d " " -f4`: This pipes the filtered output to cut, which extracts the fourth field of the line, using a space as the delimiter.
- `| tr -d ":"`: This pipes the extracted field to tr, which deletes (-d) any colons ( : ) from the output.
- `&`: This runs the entire command in the background, allowing the loop to continue without waiting for the current iteration to finish.
- `done`: This marks the end of the for loop.