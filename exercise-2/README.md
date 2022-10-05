
# TEN LINUX COMMANDS

## SYSTEM INFORMATION:

### 1. w -Display who is online
    Command to Run: sudo w 
### Screenshot
![w- Command screenshot](/exercise-2/images/display-whois-online.PNG)

## 2. uname -r -Display the kernel release information
    Command to Run: sudo uname -r
### Screenshot
![uname -r Command screenshot](/exercise-2/images/kernel-release-info.PNG)

### 3. uname -a -Display linux system information
    Command to Run: sudo uname -a
### Screenshot
![uname -a Command screenshot](/exercise-2/images/linux-system-info.PNG)

## HARDWARE INFORMATION:

### 4. badblocks -Test for unreadable blocks on disk sda
    Command to Run: sudo badblocks -s /dev/sda
### Screenshot
![badblocks Command screenshot](/exercise-2/images/test-unreadable-blocks.PNG)

### 5. hdparm -Perform a read speed test on disk sda
    Command to Run: sudo hdparm -tT /dev/sda
### Screenshot
![adblocks Command screenshot](/exercise-2/images/read-speed-test-on-disk-sda.PNG)

## SEARCH

### 6. Find files smaller than 10MB in /home using -find 
    Command to Run: find /home -size -10M
### Screenshot
![find Command screenshot](/exercise-2/images/find-size-less-than-10M.PNG)

## NETWORKING

### 7. dig -Display DNS information for domain
    Command to Run: sudo dig domain
### Screenshot 
![dig command](/exercise-2/images/dig-command.PNG)

### 8. netstat -Display listening tcp and udp ports and corresponding programs
    Command to Run: sudo netstat -nutlp
### Screenshot
![netstat command](/exercise-2/images/netstat.PNG)

### 9. ip a -Display all network interfaces and IP address
    Command to Run: ip a
### Screenshot 
![ip a Command](/exercise-2/images/ip_-a.PNG)

## PROCESS MANAGEMENT

### 10. htop -Interactive process viewer (top alternative)
    Command to Run: htop
### Screenshot 
![htop Command](/exercise-2/images/iteractive-process-viewer.PNG)