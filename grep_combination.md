# cut - extract columns

```bash
grep "ID:" practice.txt | cut -d '|' -f2
```

    output:
        Name: Alice Johnson 
        Name: Bob Smith 
        Name: Charlie Brown 
        Name: David Wilson 
        Name: Eva Adams 
    
    After the pipeline operator the output of grep is send to cut command

## Syntax of cut

```bash    
cut -d '|' -f2
```
        -d   -> delimiter, here the delimiter between values is '|' 
        -f2  -> this means 2nd field after separating
        -f2- -> this means the whole line after second field

### Examples
```bash
cut -d '|' -f3
```
        output:
            Dept: HR 
            Dept: IT 
            Dept: Finance 
            Dept: IT 
            Dept: HR
```bash
cut -d '|' -f2-
```
        output:
            Name: Alice Johnson | Dept: HR | Salary: 50000 | Location: Bangalore
            Name: Bob Smith | Dept: IT | Salary: 70000 | Location: Hyderabad
            Name: Charlie Brown | Dept: Finance | Salary: 65000 | Location: Pune
            Name: David Wilson | Dept: IT | Salary: 72000 | Location: Chennai
            Name: Eva Adams | Dept: HR | Salary: 52000 | Location: Bangalore

# sort - ordering data
```bash    
grep "ID:" practice.txt | cut -d '|' -f2 | sort
```
        output:
            Name: Bob Smith 
            Name: Charlie Brown 
            Name: David Wilson 
            Name: Eva Adams

    The sort command just sorts the names alphabetically

## Removing duplicate items using sort 
```bash
grep "Name->" practice.txt | sort -u
```

    output:
        Name-> Alex
        Name-> Alice
        Name-> Bob
        Name-> John
    
    This removes the duplicates in the results

## Sorting the results numerically
```bash    
grep "ID:" practice.txt | cut -d '|' -f4 | sort -n
```
    output:
        Salary: 50000 
        Salary: 52000 
        Salary: 65000 
        Salary: 70000 
        Salary: 72000 
    
    The cut command selects the fourth field (salary) and sorts it numerically

## sort the results in reverse order
```bash
grep "ID:" practice.txt | cut -d '|' -f4 | sort -nr
```
    output:
        Salary: 72000 
        Salary: 70000 
        Salary: 65000 
        Salary: 52000 
        Salary: 50000

    sort -nr -> sorts the fields in reverse order

# uniq - remove duplicates 
```bash    
grep "ID:" practice.txt | cut -d '|' -f3 | sort | uniq
```
    output:
        Dept: Finance 
        Dept: HR 
        Dept: IT 

    The uniq will also remove the duplicates but it needs the duplicates to be adjacent -> so if sort is not present before uniq then it will fail

## Count duplicates
```bash    
grep "ID:" practice.txt | cut -d '|' -f3 | sort | uniq -c
```
    output:
        1  Dept: Finance 
        2  Dept: HR 
        2  Dept: IT 

    The -c flag will count the number of occurences and print it
## Show only duplicates
```bash
grep "ID:" practice.txt | cut -d '|' -f3 | sort | uniq -d
```
    output:
        Dept: HR 
        Dept: IT 

## Show only unique (non-repeated)
```bash
grep "ID:" practice.txt | cut -d '|' -f3 | sort | uniq -u
```
    output:
        Dept: Finance 


## Importance of sort
```bash    
grep "ID:" practice.txt | cut -d '|' -f3 | uniq 
```
    output:
        Dept: HR 
        Dept: IT 
        Dept: Finance 
        Dept: IT 
        Dept: HR

    As the duplicates were not present adjacent it failed-> so the sort is needed for correct removal

# Count number of appearences
```bash    
grep -c "ID:" practice.txt
```
    output:
        5 

    It only prints the number of occurences
    
# Count total lines 
```bash    
wc -l practice.txt
```
    output:
        34 practice.txt

    It prints the number of lines and file name

# tr - transform text
```bash    
echo "hello world" | tr 'a-z' 'A-Z'
```
    output:
        HELLO WORLD

    It transforms lower case to upper case
```bash
echo "apple banana mango" | tr ' ' ','
```
    output:
        apple,banana,mango

    It transforms spaces to commas

# paste - merge columns
```bash
grep "ID:" practice.txt | cut -d '|' -f2 practice.txt > names.txt
grep "ID:" practice.txt | cut -d '|' -f3 practice.txt > salary.txt
paste names.txt salary.txt
```
    output:
        Name: Alice Johnson     Dept: HR 
        Name: Bob Smith         Dept: IT 
        Name: Charlie Brown     Dept: Finance 
        Name: David Wilson      Dept: IT 
        Name: Eva Adams         Dept: HR
    
    It combines two outputs 