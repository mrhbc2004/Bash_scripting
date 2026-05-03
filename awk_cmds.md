# awk - syntax understanding
> A mini programming language for working with columns in text

## basic syntax
```bash
awk 'pattern {action}' file
```
    pattern -> when to run
    action  -> what to do

## default behavior
```bash
awk '{print}' practice.txt
```
    output:
        <It prints the whole content of practice.txt>

## Fields
> By default `awk` splits using whitespace

| Variable | Meaning            |
|:--------:|:------------------:|
| $0       | Full line          |
| $1       | First column       |
| $2       | Second column      |
| $NF      | Last column        |
| NF       | number of fields   |
| NR       | number of lines    |

## custom field separator
```bash
awk -F '|' '{print $1 $2}' practice.txt
```
    output:
        <It prints the first and second column of the table as field separator as | >