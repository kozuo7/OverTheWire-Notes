# Bandit 11 Notes

Bandit 11 was not too hard once I understood what ROT13 meant.

The instructions said that the password for the next level was stored in `data.txt`, with all lowercase and uppercase letters rotated by 13 positions.

At first, I thought `data.txt` was encoded with something simple that I could probably decode by hand. I quickly checked the page and saw that OverTheWire linked some helpful reading about ROT13.

After reading that, I learned that ROT13 is a simple letter-substitution cipher. Each letter is shifted 13 places in the alphabet. ROT13 works the same way for encoding and decoding, since applying it twice returns the original text.

I searched for a ROT13 decoder and used this one:

```text
https://rot13.com/
```

I pasted the contents of `data.txt` into the text box and got the decoded password.

Password found:

```text
GROozWPO8QyN0mGrjUkID0WCYkZiQxrN
```

This one was straightforward. I learned what ROT13 is and how a simple substitution cipher can be reversed.
