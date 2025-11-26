---
title: Filter jobs by employer
nav_order: 1
parent: Tutorials
description: "Learn how to filter job entries using employer (company) name queries."
---

# Filter jobs by employer

This tutorial explains how to retrieve job entries by company name. It shows how to use the `jobs` resource with filters, read JSON responses, and understand how SmartCV behaves when no records match.

## Before you begin
Start the SmartCV service.

If the environment isn’t ready yet, review:

- [Prerequisites](prerequisites.md)

## Goal of this tutorial
This tutorial covers how to:

- Call the `/jobs` API  
- Filter job records by company  
- Use query parameters  
- Read JSON responses  
- Handle empty results  

## Step 1: Understand the endpoint
The `jobs` resource stores your work experience.  
Each job entry includes:

- title  
- company  
- location  
- start_date  
- end_date  
- responsibilities  
- id  

For the full schema, see:

- [jobs](../api-resources/jobs.md)

## Step 2: Make a basic request
Retrieve all job entries:
```
curl http://localhost:3000/jobs
```
This returns every stored job.

## Step 3: Filter by company
Use the `company` query parameter to search for a specific employer.

Example: filter for **Varicent**:
```
curl "http://localhost:3000/jobs?company=Varicent"
```

Example response:
```
[
{
"id": 1,
"title": "Technical Writer",
"company": "Varicent",
"location": "Toronto, ON",
"start_date": "2022-05",
"end_date": "Present",
"responsibilities": [
"Write UX copy in Figma including tooltips, empty states, and error messages.",
"Create structured content using DITA XML and metadata.",
"Maintain documentation consistency and clarity across channels."
]
}
]
```

SmartCV returns every job entry that matches the company value.

## Step 4: Handle no results
If the company name doesn’t match any entry:
```
curl "http://localhost:3000/jobs?company=SpaceX"
```

Response:
```
[]
```
An empty array means the filter didn’t match any stored records.

## Step 5: Use partial company searches
Use the `_like` suffix for substring searches.

Example: find entries for **Wallenstein Equipment Inc.** using only part of the name:
```
curl "http://localhost:3000/jobs?company_like=Wallen"
```


This returns all jobs whose `company` value contains your search text.

## Frequently asked questions

### The response is empty. What does that mean?

SmartCV didn’t find records that match the filter value.

Example:
```
curl "http://localhost:3000/jobs?company=Unknown%20Company"
```

Response:

[]

### Does the search ignore case?

Yes. SmartCV compares company values without considering letter case.

These calls return the same results:
```
curl "http://localhost:3000/jobs?company=varicent"
curl "http://localhost:3000/jobs?company=Varicent"
```

### How does SmartCV handle substring matching?

SmartCV uses the `_like` suffix for substring queries.

Example:
```
curl "http://localhost:3000/jobs?company_like=Lorex"
```

This returns your internship at Lorex Technology.

### Why do values with symbols fail?

Characters such as `&`, `/`, or `+` need encoding.

Correct:
```
curl "http://localhost:3000/jobs?company=Wallenstein%20Equipment%20Inc."
```

Incorrect:
```
curl "http://localhost:3000/jobs?company=Wallenstein Equipment Inc."
```

### Why do trailing spaces break a match?

Whitespace changes the value.

Example:
```
curl "http://localhost:3000/jobs?company=Varicent%20"
```

Response:
```
[]
```

Trim whitespace before sending the request.