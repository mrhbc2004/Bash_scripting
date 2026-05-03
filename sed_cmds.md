# sed - syntax 
```bash
sed 'command' practice.txt
```
    s/old/new/ -> substitute
    p          -> print
    d          -> delete
    -n         -> suppress automatic printing

## replace first occurence in each line
```bash
sed 's/Name/User/' practice.txt
```
    output:
        <It prints the whole contents of file with Name replaced with User>
        <It matches with only linewise>
## replace all occurences (g flag)
```bash
sed 's/Name/User/g' practice.txt
```
    output:
        <It prints the whole contents of file with Name replaced with User and g flag makes it global>
## replace only 2nd occurence
```bash
sed 's/Name/User/2' practice.txt
```
    output:
        <If a line has two words (Names) then the 2nd word is replaced with User>
## replace in a specific line
```bash
sed '3s/Name/User/' practice.txt
```
    output:
        <It matches only in the 3rd line and replaces it>
## replace in a range of lines
```bash
sed '1,5s/ID/EMP_ID/' practice.txt
```
    output:
        <It matches from 1st line till 5th line and replaces the matches>

## Case-insensitive Replace
```bash
sed 's/linux/LINUX/i' practice.txt
```
    output:
        <It replaces linux with LINUX, insensitive to cases>

## Print control (-n + p)
```bash
sed -n '/ERROR/p' practice.txt
```
    output:
        2024-01-01 10:05:23 ERROR Connection failed
        2024-01-01 10:15:00 ERROR Timeout occurred
    It finds for ERROR in the whole file and prints only that lines
## print specific line numbers
```bash
sed -n '5p' practice.txt
```
    output:
        ID: 104 | Name: David Wilson | Dept: IT | Salary: 72000 | Location: Chennai
    It only prints the line number 5
## print range 
```bash
sed -n '1,10p' practice.txt
```
    output:
        # Employee Records
        ID: 101 | Name: Alice Johnson | Dept: HR | Salary: 50000 | Location: Bangalore
        ID: 102 | Name: Bob Smith | Dept: IT | Salary: 70000 | Location: Hyderabad
        ID: 103 | Name: Charlie Brown | Dept: Finance | Salary: 65000 | Location: Pune
        ID: 104 | Name: David Wilson | Dept: IT | Salary: 72000 | Location: Chennai
    It prints the lines from 1 to 5th line number

## delete lines containing "ERROR"
```bash
sed '/ERROR/d' practice.txt
```
    output:
        <It removes all the lines containing ERROR>
## delete empty lines
```bash
sed '/^$/d' practice.txt
```
    output:
        <It removes all the empty lines and prints it in the terminal>
## delete specific line
```bash
sed '3d' practice.txt
```
    output:
        <It removes the 3rd line and prints the whole content>
## delete range of lines
```bash
sed '1,5d' practice.txt
```
    output:
        <It removes the lines 1 to 5 and prints the remaining content>

## Insert before a line
```bash
sed '/Server Logs/i === LOG START ===' practice.txt
```
    output:
        <It prints === LOG START === before the line containing Server Logs>
        === LOG START ===
        # Server Logs
        2024-01-01 10:00:01 INFO Server started
        2024-01-01 10:05:23 ERROR Connection failed
        2024-01-01 10:07:45 WARNING Disk space low
        2024-01-01 10:10:12 INFO User login successful
        2024-01-01 10:15:00 ERROR Timeout occurred
## Append after a line
```bash
sed '/Server Logs/a === LOG START ===/' practice.txt
```
    output:
        # Server Logs
        === LOG START ===
        2024-01-01 10:00:01 INFO Server started
        2024-01-01 10:05:23 ERROR Connection failed
        2024-01-01 10:07:45 WARNING Disk space low
        2024-01-01 10:10:12 INFO User login successful
        2024-01-01 10:15:00 ERROR Timeout occurred
## Replace entire line
```bash
sed 's/Server Logs/REPLACED LINE/' practice.txt
```
    output:
        # REPLACED LINE
        2024-01-01 10:00:01 INFO Server started
        2024-01-01 10:05:23 ERROR Connection failed
        2024-01-01 10:07:45 WARNING Disk space low
        2024-01-01 10:10:12 INFO User login successful
        2024-01-01 10:15:00 ERROR Timeout occurred
