# Bugs Documentation

## Bug ???
Bcrypt work factor was 10, which could present a security issue. I changed it to 12.

## Bug 1
auth/login route was not actually authenticating. ```User.authenticate``` was not being awaited, which was resulting in the creation and return of a token bypassing password verification.


## Bug 2
Middleware function authUser was not verifying JWT, it was just decoding it and it was not passing the SECRET key to verify. This presents a security issue in authentication. I changed it to verify and passed it the SECRET_KEY.


## Bug 3
PATCH users/:username routes was not allowing users to update their own information. It was requiring ```requireLogin, requireAdmin,``` separately, which will always require for someone to be admin. I created a separate middleware ```function requireLoginOrAdmin``` 


## Bug 4 
PATCH users/:username routes lets admin or correct users to change username, passwords, _tokens, and admin. Docstrings tell us that this should not be allowed, only first_name, last_name, phone, and email can be patched. 

