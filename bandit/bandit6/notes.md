# Bandit 6 Notes

This one was a little messy at first, but I reused the `find` command again with almost the same principle as before.

Instead of using:

```bash
find .
```

I used:

```bash
find /
```

because this time I needed to scan from the root directory `/`, not just the current directory.

The challenge was asking for a file with specific properties:

- owned by user `bandit7`
- owned by group `bandit6`
- exactly `33` bytes in size

From the last room, I already knew that to search by bytes with `find`, you can use:

```bash
-size 33c
```

The `c` means bytes.

So the full command was:

```bash
find / -type f -user bandit7 -group bandit6 -size 33c
```

## Breakdown

```bash
find /
```

Starts searching from the root directory `/`, meaning it scans the whole filesystem.

```bash
-type f
```

Only looks for regular files.

```bash
-user bandit7
```

Searches for files owned by the user `bandit7`.

```bash
-group bandit6
```

Searches for files owned by the group `bandit6`.

```bash
-size 33c
```

Searches for files that are exactly 33 bytes. The `c` means bytes.

At first, this command worked, but it printed a lot of `Permission denied` errors because I was scanning the whole filesystem and did not have permission to access everything.

A cleaner version is:

```bash
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
```

The `2>/dev/null` part hides error messages.

The `2` represents stderr, which is where error messages go.  
`/dev/null` basically throws that output away.

So instead of seeing a bunch of permission denied errors, it only shows the file that matches.

Then I catted the file it found and got the password.

Password found:

```text
Bmnnvf82KzQlfxgAI2d1zYbr1u9pr3E3
```
