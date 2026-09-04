# Loyalty Glitch

## Description:
Brewpoint's new loyalty app: buy coffee, earn points, redeem points for rewards. There's a VIP reward locked behind 1000 points.

Get to 1000 points. The flag is behind the VIP unlock.

## Flag: BTWCTF{n3g4tiv3_p0ints_ar3_still_p0ints}

## Solution:

1. Open the site and inspect the **Network** tab.

2. Redeeming a reward sends a request like:

```json
POST /api/redeem
{"amount":50}
```

3. Attempting to modify the `loyalty_session` cookie directly does not work because the cookie is HMAC-signed and any tampering invalidates it.

4. Looking at the redeem functionality, the server only checks whether the amount is greater than the current balance. It does not prevent **negative values**.

5. Send a request with a negative amount:

```json
POST /api/redeem
{"amount":-100}
```

6. Instead of deducting points, the server calculates:

```text
20 - (-100) = 120
```

which increases the balance.

7. Repeat the request multiple times until the balance exceeds 1000 points.

8. Visit `/api/flag` or click **Check VIP Status** to obtain the flag.


