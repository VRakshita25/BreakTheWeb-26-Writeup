THE UNSENT DRAFT

Category: Client-Side Storage / Information Disclosure
Difficulty: Beginner

Challenge

A secure messaging platform claims that deleted drafts are gone forever.

But something from a previous recovery process may have been left behind.

Sometimes the browser remembers more than the application intends.

Intended solution

The application does not visibly show the deleted draft.

Players inspect browser-side storage using Developer Tools.

The intended locations include:

Local Storage
Session Storage

A leftover recovery value contains data from the old draft workflow.

The player decodes or follows the stored recovery information to retrieve the flag.

Flag
BTWCTF{drafts_should_not_contain_secrets_7K9M8DH4T5}