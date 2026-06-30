## Bandit 4 Notes

Bandit 4 was relatively simple, but I had a small issue with catting the file.

I started by going into the `inhere` directory:

```bash
cd inhere
```

Then I ran `ls` inside the directory and saw nothing:

```bash
ls
```

At first it looked empty, so I used:

```bash
ls -la
```

That showed hidden files/directories, and I saw:

```bash
-rw-r----- 1 bandit4 bandit3 33 Jun 24 14:59 ...Hiding-From-You
```

So the file was there, but it was hidden because the filename started with periods.

At first, I tried:

```bash
cat Hiding-From-You
```

but that did not work because I ignored the periods at the beginning of the filename.

The fix was to include the full exact filename:

```bash
cat ...Hiding-From-You
```

That worked because the periods are actually part of the filename. In Linux, files that start with `.` are hidden from normal `ls`, but the dot is still part of the real name.

Password found:

```text
xzTXq1rDJQVVAzdv5cHq1TQytTWufAMq
```
