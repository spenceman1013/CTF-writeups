# **Quarantine** 

### 200 Points

#### **Problem**

See if you can get access to an account on the webapp.

#### **Solution**

Since we have a login lets just see if we are able to use some SQL injection to get into the webapp. 
I started with `' or 1=1;--` and that got me the following error:

![Login Error](files/quarantine-1.png)

So it complains that we are trying to use to log in as more than one user. I think that easy way would be to limit our sql query to only return one user. I modified my query to `' or 1=1 limit 1; --` and with that we got logged in.

![quarantine login](files/quarantine-2.png)

And there we see our flag is: **ractf{Y0u_B3tt3r_N0t_h4v3_us3d_sqlm4p}**