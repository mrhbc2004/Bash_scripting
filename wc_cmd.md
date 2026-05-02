# wc - word count syntax and output

```bash
wc practice.txt
```
    output:
        34 157 976 practice.txt

    This prints three fields like <lines><words><bytes(size of file)> <file_name>

## Variants

### Number of lines
```bash
wc -l practice.txt
```
    output:
        34 practice.txt

    Only prints the number of lines
### Number of words
```bash
wc -w practice.txt
```
    output:
        157 practice.txt
    Only prints the number of words
### Bytes
```bash
wc -c practice.txt
```
    output:
        976 practice.txt
    This is the size of the file in bytes
### If you don't want the file name
```bash
wc -l < practice.txt
```
    output:
        34
    It only prints the output like number of lines,words or bytes not the file name