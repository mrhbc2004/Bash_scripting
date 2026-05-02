# Basic search:
    grep "Alice" practice.txt 

    output: 
        ID: 101 | Name: Alice Johnson | Dept: HR | Salary: 50000 | Location: Bangalore

    It is case sensitive

# Case insensitive search
    grep -i "linux" practice.txt

    output: 
        Linux is awesome.

    It matches both "Linux" "linux" etc

# Show line numbers
    grep -n "ERROR" practice.txt

    output: 
        10:2024-01-01 10:05:23 ERROR Connection failed
        13:2024-01-01 10:15:00 ERROR Timeout occurred
    
    Prints the line numbers with matched lines

# Count matches
    grep -c "ERROR" practice.txt

    output:
        2 
    
    Only prints the number of matches -> not the lines

# Invert matches
    grep -v "INFO" practice.txt

    output:
        <It prints the whole practice.txt file but not the lines with INFO in it>

# Matches whole words
    grep -w "IT" practice.txt

    output:
        ID: 102 | Name: Bob Smith | Dept: IT | Salary: 70000 | Location: Hyderabad
        ID: 104 | Name: David Wilson | Dept: IT | Salary: 72000 | Location: Chennai

    It matches the whole word and avoids partial matches like "BIT"

# Multiple patterns
    grep -E "ERROR|WARNING" practice.txt

    output:
        2024-01-01 10:05:23 ERROR Connection failed
        2024-01-01 10:07:45 WARNING Disk space low
        2024-01-01 10:15:00 ERROR Timeout occurred
    
    It matches both the patterns either ERROR or WARNING

# Show context (Before/After lines)
    grep -A 1 "ERROR" practice.txt  # After
    grep -B 1 "ERROR" practice.txt  # Before
    grep -C 1 "ERROR" practice.txt  # Both

    output:
        After: 
            2024-01-01 10:05:23 ERROR Connection failed
            2024-01-01 10:07:45 WARNING Disk space low
            -- <This is printed by grep itself>
            2024-01-01 10:15:00 ERROR Timeout occurred
            <empty line>

        Before:
            2024-01-01 10:00:01 INFO Server started
            2024-01-01 10:05:23 ERROR Connection failed
            -- <printed by grep>
            2024-01-01 10:10:12 INFO User login successful
            2024-01-01 10:15:00 ERROR Timeout occurred

        Centre:
            2024-01-01 10:00:01 INFO Server started
            2024-01-01 10:05:23 ERROR Connection failed
            2024-01-01 10:07:45 WARNING Disk space low
            2024-01-01 10:10:12 INFO User login successful
            2024-01-01 10:15:00 ERROR Timeout occurred
            <empty line>

    It will print both the matched line and number of lines given in command based on the context (A/B/C)

# Highlight matches
    grep --color=auto "ERROR" practice.txt

    output:
        2024-01-01 10:05:23 ERROR Connection failed
        2024-01-01 10:15:00 ERROR Timeout occurred

    It will highlight the matched pattern with a color automatically

# Match Beginning of line
    grep "^ID" practice.txt

    output:
        ID: 101 | Name: Alice Johnson | Dept: HR | Salary: 50000 | Location: Bangalore
        ID: 102 | Name: Bob Smith | Dept: IT | Salary: 70000 | Location: Hyderabad
        ID: 103 | Name: Charlie Brown | Dept: Finance | Salary: 65000 | Location: Pune
        ID: 104 | Name: David Wilson | Dept: IT | Salary: 72000 | Location: Chennai
        ID: 105 | Name: Eva Adams | Dept: HR | Salary: 52000 | Location: Bangalore
    
    It will match the lines with starting of the pattern exactly

# Match end of line
    grep "awesome.$" practice.txt

    output:
        Linux is awesome.

    The lines which end with the exact pattern will be printed

# Search in Multiple files
    grep "Alice" *.txt

    output:
        practice.txt:ID: 101 | Name: Alice Johnson | Dept: HR | Salary: 50000 | Location: Bangalore
    
    It will search the pattern in all txt files with printing the file name as well

# Workaround for removing group-separator in grep multiple matches
    grep -A 2 --no-group-separator "ERROR" practice.txt

    output:
        2024-01-01 10:05:23 ERROR Connection failed
        2024-01-01 10:07:45 WARNING Disk space low
        2024-01-01 10:10:12 INFO User login successful
        2024-01-01 10:15:00 ERROR Timeout occurred
        <empty line>
        # Emails

    It doesn't print any group-separator

## Alternative (if grep version is older)
    grep -A 2 "ERROR" practice.txt | grep -v '^--$'

    Prints the same output as above. The '|' (pipe) operator forwards the output of first command as input to second command

