# Candroid

### 50 Points

### Problem

I think I can, I think I can!

Download the file below.

[candroid.apk](files/candroid.apk)

### Solution

This and [Simple App](simpleapp.md) have basically the same solution. APKs are really just zip files with several other files needed for the app to run included in it. 

I started by just unzipping the apk to take a look at the files. I tried a simple grep to see what it would find and this is what we got:

```bash
grep -r "flag{" *
Binary file resources.arsc matches
```

So it looks like the flag may be in resources.arsc. Let's use strings to find out:

```
strings resources.arsc | grep flag{
flag{4ndr0id_1s_3asy}
```

And there is the flag: **flag{4ndr0id_1s_3asy}**



