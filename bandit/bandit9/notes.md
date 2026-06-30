# Bandit 9 Notes

Bandit 9 was light work.

The instructions said the password was in `data.txt`, and it was one of the few human-readable strings. It was also preceded by several `=` characters.

My instant thought was that I might have to chain a few commands together, like:

```bash
strings | sort | uniq | grep
```

So I started building weird commands that did not work, like:

```bash
strings data.txt | sort data.txt | grep "="
```

My thought process was that `strings` would pull out the human-readable text, then I could funnel that into `sort`, and then use `grep` to search for the `=` characters.

But the issue was this part:

```bash
sort data.txt
```

By writing `sort data.txt`, I was telling `sort` to read from `data.txt` again instead of sorting the output from `strings`.

So the pipe was basically getting messed up because `sort data.txt` was not using the output from the command before it.

A better version would have been something like:

```bash
strings data.txt | grep "="
```

or even:

```bash
strings data.txt | grep "=="
```

But I ended up realizing I did not need to overcomplicate it.

I just ran:

```bash
strings data.txt
```

That printed out the human-readable text from the file, and the password was right there with a bunch of `=` characters behind it.

Password found:

```text
B0s2khmbT9u0geKuOoVGW3JZKhndE3BG
```

I actually could not believe it at first, so I immediately exited and tried to SSH into the next stage, and it worked.

Overall, this one was simple, but I overcomplicated it a little at the beginning.
