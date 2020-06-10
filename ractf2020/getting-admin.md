# **Getting Admin**

### 300 Points

#### *Problem*

See if you can get an admin account.

#### *Solution*

Being newer to this, I wasn't sure exactly where to go, so I got the hint for this challenge. It said to research JWT, Especially the none method. I looked into this and it turns on that for some servers that use JavaScript Web Tokens you can set the hashing algorithm to none and that will bypass the signature validation that is normally done. Not all servers will accept that type, but there is a pretty good chance that this one will. We grab the Token from our cookie and it is:

```
eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjogIkhhcnJ5IiwgInByaXZpbGVnZSI6IDF9.A7OHDo-b3PB5XONTRuTYq6jm2Ab8iaT353oc-VPPNMU
```

Each section of the cookie is separated by a dot. The first is the header which includes the algorithm that will be used. The second section is the token information and the third section is the signature.  When decoded that shows as the following:

```json
{"typ":"JWT","alg":"HS256"} . {"user": "Harry", "privilege": 1}
```

What we want to do is modify our json to look more like this:

```json
{"typ":"JWT","alg":"none"} . {"user": "Harry", "privilege": 2}
```

When encoded back into base64 that gives us:

```
eyJ0eXAiOiJKV1QiLCJhbGciOiJub25lIn0=.eyJ1c2VyIjogIkhhcnJ5IiwgInByaXZpbGVnZSI6IDJ9
```

We replace our cookie value with that and then click on the admin page and we get our flag: **ractf{j4va5cr1pt_w3b_t0ken}**