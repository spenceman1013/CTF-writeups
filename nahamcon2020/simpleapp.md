# Simple App

### 50 Points

### Problem

Here's a simple Android app. Can you get the flag?

Download the file below.

[simple-app.apk](files/simple-app.apk)

### Solution

This and [Candroid](candroid.md) have basically the same solution. APKs are really just zip files with several other files needed for the app to run included in it. 

I started by just unzipping the apk to take a look at the files. I tried a simple grep to see what it would find and this is what we got:

```bash
grep -r "flag{" *
Binary file classes.dex matches
```

So it looks like the flag may be in classes.dex . Let's use strings to find out:

```
strings classes.dex | grep flag{
flag{3asY_4ndr0id_r3vers1ng}
```

And there is the flag: **flag{3asY_4ndr0id_r3vers1ng}**