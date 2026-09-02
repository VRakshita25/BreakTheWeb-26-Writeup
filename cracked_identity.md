# Full intended solve
Step 1

Player visits:

/

Only sees a normal login portal.

Step 2

Player performs recon:

/robots.txt

Finds:

Disallow: /backup/
Step 3

Visits:

/backup/

Finds:

users.db.bak
Step 4

Opens:

/backup/users.db.bak

Finds:

username=admin

password_hash=25d55ad283aa400af464c76d713c07ad

hash_algorithm=MD5
Step 5

Cracks the MD5 hash and gets:

123456789
Step 6

Logs in with:

Username: admin
Password: 123456789
Step 7

Server returns:

```BTWCTF{legacy_hashes_are_not_identity_protection_7F2933ROP}```