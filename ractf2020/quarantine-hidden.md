# **Quarantine - Hidden Information**

### 150 Points

#### **Problem**

We think there's a file they don't want people to see hidden somewhere! See if you can find it, it's gotta be on their webapp somewhere...

#### **Solution**

One of the fist places I always check is robots.txt, just to see if it gives us anything to go off of. So looking at that we see the following:

```
User-Agent: *
Disallow: /admin-stash
```

So we go to that page and the only thing on it is our flag: **ractf{1m_n0t_4_r0b0T}**

