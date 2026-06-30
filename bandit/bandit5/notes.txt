## Bandit 5 Notes

Bandit 5 started in the `inhere` directory, so I went into it with:

```
cd inhere
```

Inside, there were 10 files.

At first, I just started catting each file individually:

```
cat ./-file00
cat ./-file01
cat ./-file02
```

I found that file `07` had readable text, and that revealed the password.

That worked, but it was inefficient. A better way is to quickly check what type of file each one is before trying to read them.

The better command was:

```
file ./*
```

The `file` command checks the file type, and `./*` means “scan everything in the current directory.”

Most of the files were just `data` files. A few were different, like an OpenPGP secret key and one file that was non-ISO extended ASCII text with NEL line terminators.

File `07` showed up as ASCII text, so that was the readable one.

Then I catted it:

```
cat ./-file07
```

That revealed the password.

Password found:

```
6C7h9GD8M6ai5nr7wo1RonrzFjj9yIrG
```
