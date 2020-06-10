# **Insert Witty Name**

###  200 Points

### *Problem*

Having access to the site's source would be really useful, but we don't know how we could get it. All we know is that the site runs python.

### *Solution*

Having already found a way to get files from the server in [Entrypoint](entreypoint.md) I figured that this would be something using that method. We just had to find the name of the file. I tried app.py but that returned nothing. I then tried main.py and that got me the following:

```py
from application import main
import sys

# ractf{d3velopersM4keM1stake5}

if __name__ == "__main__":
    main(*sys.argv)
```

 And there we have the flag: **ractf{d3velopersM4keM1stake5}**