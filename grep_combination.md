# cut - extract columns
    grep "ID:" practice.txt | cut -d '|' -f2

    output:
        Name: Alice Johnson 
        Name: Bob Smith 
        Name: Charlie Brown 
        Name: David Wilson 
        Name: Eva Adams 
    
    After the pipeline operator the output of grep is send to cut command

## Syntax of cut
    cut -d '|' -f2

        -d   -> delimiter, here the delimiter between values is '|' 
        -f2  -> this means 2nd field after separating
        -f2- -> this means the whole line after second field

### Examples
    cut -d '|' -f3
        output:
            Dept: HR 
            Dept: IT 
            Dept: Finance 
            Dept: IT 
            Dept: HR

    cut -d '|' -f2-
        output:
            Name: Alice Johnson | Dept: HR | Salary: 50000 | Location: Bangalore
            Name: Bob Smith | Dept: IT | Salary: 70000 | Location: Hyderabad
            Name: Charlie Brown | Dept: Finance | Salary: 65000 | Location: Pune
            Name: David Wilson | Dept: IT | Salary: 72000 | Location: Chennai
            Name: Eva Adams | Dept: HR | Salary: 52000 | Location: Bangalore

# sort - ordering data
    grep "ID:" practice.txt | cut -d '|' -f2 | sort
        output:
            Name: Bob Smith 
            Name: Charlie Brown 
            Name: David Wilson 
            Name: Eva Adams

    The sort command just sorts the names alphabetically

## Removing duplicate items using sort 
    grep "Name->" practice.txt | sort -u

    output:
        Name-> Alex
        Name-> Alice
        Name-> Bob
        Name-> John
    
    This removes the duplicates in the results

## Sorting the results numerically
    grep "ID:" practice.txt | cut -d '|' -f4 | sort -n

    output:
        Salary: 50000 
        Salary: 52000 
        Salary: 65000 
        Salary: 70000 
        Salary: 72000 
    
    The cut command selects the fourth field (salary) and sorts it numerically

## sort the results in reverse order
    grep "ID:" practice.txt | cut -d '|' -f4 | sort -nr

    output:
        Salary: 72000 
        Salary: 70000 
        Salary: 65000 
        Salary: 52000 
        Salary: 50000

    sort -nr -> sorts the fields in reverse order

# uniq - remove duplicates 
    grep "ID:" practice.txt | cut -d '|' -f3 | sort | uniq

    output:
        Dept: Finance 
        Dept: HR 
        Dept: IT 

    The uniq will also remove the duplicates but it needs the duplicates to be adjacent -> so if sort is not present before uniq then it will fail

## Count duplicates
    grep "ID:" practice.txt | cut -d '|' -f3 | sort | uniq -c

    output:
        1  Dept: Finance 
        2  Dept: HR 
        2  Dept: IT 

    The -c flag will count the number of occurences and print it
## Show only duplicates
    grep "ID:" practice.txt | cut -d '|' -f3 | sort | uniq -d

    output:
        Dept: HR 
        Dept: IT 

## Show only unique (non-repeated)
    grep "ID:" practice.txt | cut -d '|' -f3 | sort | uniq -u

    output:
        Dept: Finance 


## Importance of sort
    grep "ID:" practice.txt | cut -d '|' -f3 | uniq 

    output:
        Dept: HR 
        Dept: IT 
        Dept: Finance 
        Dept: IT 
        Dept: HR

    As the duplicates were not present adjacent it failed-> so the sort is needed for correct removal

