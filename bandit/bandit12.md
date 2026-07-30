# Bandit 12 Notes

Bandit 12 was way harder than I expected it to be.

The instructions said that the password for the next level was stored in `data.txt`, which was a hexdump of a file that had been repeatedly compressed. It also suggested making a working directory under `/tmp` so I could safely copy, rename, and extract files while figuring it out.

At first, I barely understood what the prompt was saying, so I read through the beginning of a writeup to understand the general idea. After that, I made my own directory:

```bash
mkdir /tmp/temptmp
```

Then I copied `data.txt` into it so I could work on a separate copy:

```bash
cp data.txt /tmp/temptmp
```

## Figuring Out the File

This was where I got stumped for a bit.

I ran `strings` on `data.txt` and saw a lot of hex-looking data. My first thought, coming from more of a Hack The Box mindset, was that I might need to decode it or open it in software. But the room had specifically said the file was repeatedly compressed, so I went back to that clue.

I renamed `data.txt` to `data` because it was not really a normal text file. Since it was a hexdump, I used `xxd` to reverse the hexdump back into the original binary data:

```bash
xxd -r data > binary
```

`xxd` can display binary data as hexadecimal, but the `-r` option reverses a hexdump back into its original binary form.

In this command:

```bash
xxd -r data
```

reverses the hexdump in `data`, while:

```bash
> binary
```

redirects that recovered binary data into a new file named `binary`.

After that, I inspected the new file with:

```bash
file binary
```

It showed that the file was gzip-compressed data. I renamed the file with a `.gz` extension and used `gzip -d` to decompress it.

I checked the resulting file with `file` again, and this time it showed bzip2-compressed data. I repeated the same process: rename the file with the matching extension, decompress it with `bzip2 -d`, then inspect the new output with `file` again.

The next file was gzip data again, then later I reached a POSIX tar archive. For tar files, I used:

```bash
tar -xf binary
```

The `-x` option extracts the archive, and `-f` tells `tar` that the next value is the archive filename.

That extraction gave me another file, which I inspected with `file` again. It turned out to be another tar archive, so I extracted it once more.

From there, I kept repeating the same cycle:

1. Run `file` to identify the current file type.
2. Rename the file with the matching extension when needed.
3. Decompress or extract it with `gzip`, `bzip2`, or `tar`.
4. Run `file` again on the result.

Eventually, the output became ASCII text instead of another compressed or archived file. I used `cat` on that final file, and it printed the password.

Password found:

```text
qQYQiHOBPR8zR61qxYqX45quvihF2uzk
```

This level taught me to stop treating a weird-looking file as one thing. The important move was repeatedly checking the file type with `file` after every extraction instead of guessing what the next format would be.
