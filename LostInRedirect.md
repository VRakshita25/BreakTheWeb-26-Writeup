LOST IN REDIRECT

Category: Open Redirect / URL Parsing
Difficulty: Medium

Challenge

Transit Auth claims to protect users from malicious redirects by allowing authentication to continue only to destinations within the application.

But URL paths aren't always interpreted the way developers expect.

Intended solution

The redirect validation checks whether the destination begins with:

/

The developer assumes this means the destination is an internal path.

However, URLs beginning with:

//

can be interpreted by browsers as protocol-relative URLs.

For example:

//example.com/path

may be treated as:

https://example.com/path

when loaded from an HTTPS page.

The validation accepts the value because it begins with /, but the browser interprets it differently.

The intended redirect bypass leads to the restricted destination and the flag.

Flag
```BTWCTF{slashes_can_mean_more_than_you_think_8Xk29P}```