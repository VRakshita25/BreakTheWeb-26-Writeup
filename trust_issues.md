TRUST ISSUES

Category: Header Trust / Access Control Bypass
Difficulty: Medium

Challenge

An internal administration service is protected by network-based access controls.

The gateway claims administrative services are only accessible from the internal network. However, the infrastructure relies on a legacy reverse proxy.

Can you convince it that you're already inside?

Intended solution

The application trusts a client-controlled forwarding header to determine the source IP.

Players inspect the request and experiment with:

X-Forwarded-For: 127.0.0.1

or the expected internal IP value used by the challenge.

Because the backend trusts the supplied header without ensuring it was inserted by a trusted proxy, the request is treated as coming from the internal network.

The protected admin resource then reveals the flag.

Flag
BTWCTF{never_trust_client_forwarded_headers_7K4MWV293HQQ}