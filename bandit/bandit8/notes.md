# Bandit 8 Notes

Bandit 8 was very simple, but I had to learn a couple new commands.

This lab used:

```
sort
```

and:

```
uniq
```

There was a `data.txt` file with what looked like hundreds of duplicate lines and only one unique line.

The instructions said the password was the only line that appeared once, so I needed a way to filter out all the duplicate lines and only show the unique one.

The command I used was:

```
sort data.txt | uniq -u
```

## Breakdown

```
sort data.txt
```

Sorts the lines inside `data.txt`.

This matters because `uniq` only compares duplicate lines that are next to each other. Sorting the file first puts matching lines beside each other so `uniq` can process them correctly.

```
|
```

Pipes the sorted output into the next command.

```
uniq -u
```

Shows only lines that are unique.

The `-u` option specifically tells `uniq` to only print lines that appear once and ignore the duplicates.

So the full command:

```
sort data.txt | uniq -u
```

sorted the file, filtered out the duplicate lines, and printed the one unique line, which was the password.

Password found:

```
EjmOSvuAu7sGAHqHVcBDPirRe9T03kxl
```
