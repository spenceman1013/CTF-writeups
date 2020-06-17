# Agent 95

### 50 Points

### **Problem**

They've given you a number, and taken away your name~

Connect here:
[http://jh2i.com:50000](http://jh2i.com:50000/)

### **Solution**

When you initially connect you get a page that just says the following:

```
You don't look like our agent!
We will only give our flag to our Agent 95! He is still running an old version of Windows...
```

So it sounds like we need our browser User agent to be from windows 95.

I did a quick google search for user agent strings from windows 95 just so I would have an accurate one. You can either install an extension that allows you to switch your user agent string or use a proxy like Burp to intercept the request and change the default user agent string.

I ended up using the string `[Mozilla/4.0 (compatible; MSIE 4.01; Windows 95)]`. When you visit the page with that string you get the flag: **flag{user_agents_undercover}**

