THE BROKEN TOKEN

Category: JWT / Weak Signing Secret
Difficulty: Medium–Hard

Challenge

The Vault Authentication Service has recently undergone a migration.

Intended solution

Players begin with the provided analyst account and receive a JWT.

The token can be decoded to reveal information including:

alg: HS256
iss: vault-auth-v1

The dashboard exposes a system status endpoint containing legacy compatibility information.

The status response reveals the flawed key derivation scheme:

issuer + "::" + migration key

along with:

migration key: legacy-signing-key

The signing secret can therefore be reconstructed as:

vault-auth-v1::legacy-signing-key

The player changes the JWT payload:

{
  "role": "admin"
}

and signs the modified token using the predictable secret.

The forged token is then sent as the session cookie to the admin endpoint.

The vault returns the flag.

Flag
BTWCTF{predictable_signing_secrets_break_trust_7Kp29X}