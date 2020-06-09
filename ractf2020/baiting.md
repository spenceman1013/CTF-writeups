#*Baiting*

### 200 Points

####*Problem*
That user list had a user called loginToGetFlag. Well, what are you waiting for?
####*Solution*

This is really similar to the [Admin Attack](admin-attack.md) except we need to get in as a different user.

Lets try the same query with the changed username `' or 1=1 and username = 'loginToGetFlag';--`

And Just like that we are in again and get the flag: *ractf{injectingSQLLikeNobody'sBusiness}*
