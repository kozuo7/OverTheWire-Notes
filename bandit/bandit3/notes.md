Bandit 3 was tricky because the filename was `--spaces in this filename--`.

At first, I thought quotes would fix it, like with `cat "message is here"`, because quotes handle spaces in filenames. But this file had another issue: it started with `--`.

When I ran:

`cat "--spaces in this filename--"`

the shell treated the whole quoted text as one argument, but `cat` still saw that argument starting with `--` and tried to interpret it as an option/flag instead of a filename.

The fix was:

`cat -- "--spaces in this filename--"`

The standalone `--` tells `cat` to stop parsing options. Anything after it should be treated as a normal filename, even if it starts with `-` or `--`.

So quotes fix spaces, but `--` fixes filenames that look like command options.
