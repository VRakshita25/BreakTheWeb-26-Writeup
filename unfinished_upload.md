THE UNFINISHED UPLOAD

Category: File Upload / MIME-Type Confusion
Difficulty: Medium

Challenge

The Evidence Intake system claims that every uploaded file is strictly validated before entering its processing pipeline.

A legacy evidence processor is still running somewhere in the system, and not every component seems to agree on what makes a file valid.

Intended solution

The application appears to validate uploaded files.

Players upload an approved file and inspect the processing response.

The key is that different parts of the pipeline trust different properties of the uploaded file.

For example:

filename extension
declared MIME type
actual file contents

The validation layer may accept one interpretation while the legacy processor handles the file differently.

By supplying a file that passes the initial validation but triggers the legacy processing path, players follow the resulting breadcrumb to the hidden resource.

The final response contains the flag.

Flag
```BTWCTF{mime_types_are_not_just_metadata_4Rk91Z}```