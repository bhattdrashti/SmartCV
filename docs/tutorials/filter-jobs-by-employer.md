# Filter jobs by employer

This tutorial explains how to search job entries by employer name. It shows how to use the `jobs` resource with filters, read JSON responses, and understand how SmartCV behaves when no records match.

## Before you begin
Start the SmartCV service.  
If the environment isn’t ready yet, follow:

- [Prerequisites](prerequisites.md)

## Goal of this tutorial
This tutorial covers how to:
- Call the `/jobs` API  
- Filter job records by employer  
- Use query parameters  
- Read JSON responses  
- Handle empty results  

## Step 1: Understand the endpoint
The `jobs` resource stores the user’s work experience.  
Each entry contains:

- title  
- type  
- employer  
- startMonth  
- startYear  
- endMonth  
- endYear  
- id  

For the full schema, see:

- [jobs](../api/jobs.md)

## Step 2: Make a basic request
Retrieve all job entries:

```
curl http://localhost:3000/jobs
```

This returns every stored job record.

## Step 3: Filter by employer
Use the `employer` query parameter to search for a specific employer:

```
curl "http://localhost:3000/jobs?employer=SteelCloud%20LLC"
```

Example response:

```
[
  {
    "title": "Technical Writer",
    "type": "wd",
    "employer": "SteelCloud LLC",
    "startMonth": 2,
    "startYear": 2023,
    "endMonth": null,
    "endYear": null,
    "id": 1
  }
]
```

SmartCV returns every job entry that matches the employer value.

## Step 4: Handle no results
If the employer name doesn’t match any entry:

```
curl "http://localhost:3000/jobs?employer=SpaceX"
```

Response:

```
[]
```

An empty array means the filter didn’t match any stored records.

## Step 5: Use partial employer searches
SmartCV supports substring matching for employer names by using the `_like` suffix:

```
curl "http://localhost:3000/jobs?employer_like=Script"
```

This example matches records from the Non-Roman Script Initiative.

## Frequently asked questions

### The response is empty. What does that mean?
SmartCV didn’t find records that match the filter value.

Example:
```
curl "http://localhost:3000/jobs?employer=Unknown%20Company"
```

Response:
```
[]
```

### Does the search ignore case?
Yes. SmartCV compares employer values without considering case.

Examples:
```
curl "http://localhost:3000/jobs?employer=steelcloud%20llc"
```

```
curl "http://localhost:3000/jobs?employer=SteelCloud%20LLC"
```

These calls return the same results.

### How does SmartCV handle substring matching for employers?
SmartCV uses the `_like` suffix for substring queries.

Example:
```
curl "http://localhost:3000/jobs?employer_like=NRSI"
```

This example matches records from the Non-Roman Script Initiative.


### Why do values with symbols fail?
Characters such as `&`, `/`, or `+` need encoding.

Correct:
```
curl "http://localhost:3000/jobs?employer=Non-Roman%20Script%20Initiative%20%28NRSI%29"
```

Incorrect:
```
curl "http://localhost:3000/jobs?employer=Non-Roman Script Initiative (NRSI)"
```

### Why do trailing spaces break a match?
Whitespace changes the value.

Example:
```
curl "http://localhost:3000/jobs?employer=SteelCloud%20LLC%20"
```

Response:
```
[]
```

Trim whitespace before sending the request.

## Related resources
These tutorials continue the workflow and show how to use other SmartCV data:

- [Get portfolio items for a job](get-portfolio-for-job.md)  
- [Build a targeted cv](build-targeted-cv.md)  
- [Combine job, portfolio, and achievement data](combine-job-resources.md)  
- [Search tools and credentials by type](search-tools-and-creds.md)  
- [Return to the main index](../index.md)
