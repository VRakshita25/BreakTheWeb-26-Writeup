THE OTHER ADMIN

Category: Unicode Homograph / Authorization Confusion
Difficulty: Hard

Challenge

IDENTIQ protects administrative resources by assigning permissions based on identity.

The admin identity is reserved and cannot be registered.

But in a system where identities are handled across different character sets, appearances can sometimes be deceptive.

Intended solution

The exact ASCII username:

admin

is blocked during registration.

However, the registration check only blocks that exact character sequence.

The authorization system later performs Unicode normalization and maps visually similar characters to ASCII equivalents.

Players register:

аdmin

The first character is Cyrillic а, Unicode:

U+0430

It visually resembles:

a

but is a different character.

The registration system accepts the username.

Later, the authorization logic normalizes it and treats it as:

admin

The player is therefore recognized as an administrator and can access the vault.

Flag
```BTWCTF{the_other_admin_was_never_ascii_7X9K2}```