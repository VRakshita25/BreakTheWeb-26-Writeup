TOO MANY REQUESTS

Category: Rate Limiting / Client-Side Security Bypass
Difficulty: Beginner–Medium

Challenge

The authentication system proudly claims that brute-force protection is enabled.

Three attempts. That's all you're supposed to get.

But is the limit actually enforced where it matters?

Intended solution

The interface displays a rate-limit warning after three failed attempts.

However, inspection shows that the restriction is implemented only in the client-side application.

The backend endpoint itself does not properly enforce the attempt limit.

Players can continue submitting requests directly using:

Burp Suite
browser developer tools
another HTTP client

The UI believes the player is locked out, but the server continues processing requests.

The correct authentication value eventually reveals the flag.

Flag
```BTWCTF{rate_limits_mean_nothing_if_only_the_ui_checks_82KLM777UI}```