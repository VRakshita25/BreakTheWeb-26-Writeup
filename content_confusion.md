CONTENT CONFUSION

Category: Content-Type Confusion / Parser Differential
Difficulty: Medium

Challenge

ProfileHub recently migrated to a modern API format, but compatibility with legacy clients is still enabled.

The application claims that access permissions are managed automatically by the identity service.

But does every way of talking to the API follow the same rules?

Intended solution

The normal application sends JSON:

Content-Type: application/json

The JSON parser correctly prevents modification of protected fields.

However, the legacy parser handles:

Content-Type: application/x-www-form-urlencoded

differently.

The player sends the request using the alternate content type and supplies the privileged field through the legacy format.

For example:

displayName=Operator&accessLevel=admin

The vulnerable parser accepts the value and upgrades the access level.

The admin response reveals the flag.

Flag
```BTWCTF{parsers_should_not_define_authorization_9X4K5WEOJ}```