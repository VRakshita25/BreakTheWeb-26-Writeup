THE LAZY LOAD

Category: Business Logic / Pagination Abuse
Difficulty: Medium

Challenge

ArchiveStream provides access to thousands of historical system reports.

The interface uses a legacy pagination service to retrieve records in small batches.

Everything looks normal... but are the pagination controls showing you everything the archive is willing to return?

Sometimes moving forward isn't the only direction worth exploring.

Intended solution

The frontend only allows normal pagination:

offset=0
offset=10
offset=20

Players inspect the API request and manually modify the pagination value.

The backend does not properly validate negative offsets.

Trying something such as:

offset=-1

or another negative value causes the backend to expose hidden archive records.

One of these records contains the flag.

Flag
```BTWCTF{negative_offsets_reveal_hidden_records43012WW4G7}```