Concept:

HTTP Parameter Pollution (HPP)

Intended solve

The application appears to have a normal profile lookup:

/profile?user=guest

The frontend sends one user parameter.

But the backend processes duplicate parameters differently.

The interesting request is:

/profile?user=guest&user=admin

The frontend/parser sees the first value, while the vulnerable backend authorization logic ends up using the second value.

The admin profile contains the flag.




Actual vulnerability:

https://ghost-parameters-xxxx.vercel.app/api/profile?user=guest&user=admin