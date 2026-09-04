THE WAF THAT BLINKED

Category: WAF Bypass / Directory Traversal
Difficulty: Medium

Challenge

The archive is protected by a legacy Web Application Firewall.

It claims to inspect every request before processing it.

Maybe the order of operations matters.

Intended solution

A normal traversal attempt using:

../

is blocked.

The vulnerability exists because the WAF validates the input before normalization.

The application later replaces the custom placeholder:

.{.}

with:

..

Therefore, the intended payload is:

/.{.}/.{.}/flag.txt

The WAF does not see a direct traversal sequence.

Later processing transforms the path into:

/../../flag.txt

which resolves to the protected file.

Flag
```BTWCTF{waf_checked_before_normalization_9X7Khu4h4347}```