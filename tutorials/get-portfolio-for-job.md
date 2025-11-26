---
title: Get portfolio items for a job
nav_order: 2
parent: Tutorials
description: "Learn how to retrieve portfolio items associated with a specific job using jobId filters."
---

# Get portfolio items for a job

This tutorial explains how to retrieve portfolio items linked to a specific job. It shows how to use the `portfolio` resource with filters, read JSON responses, and understand how SmartCV associates work samples with job roles.

## Before you begin
Start the SmartCV service.

If the environment isn’t ready yet, review:

- [Prerequisites](prerequisites.md)

## Goal of this tutorial
This tutorial covers how to:

- Call the `/portfolio` API  
- Filter portfolio items by `jobId`  
- Understand how SmartCV links jobs and portfolio records  
- Read JSON responses  
- Handle empty results  

## Step 1: Understand the endpoint
The `portfolio` resource stores work samples or deliverables tied to your job history.  
Each entry includes:

- id  
- jobId  
- title  
- description  

For the full schema, see:

- [portfolio](../api-resources/portfolio.md)

## Step 2: Identify the job you want to reference
Each portfolio item links to a job through the `jobId` field.

Example: retrieve your **Varicent** job:
```
curl http://localhost:3000/jobs/1
```

This returns the job entry with `id: 1`.

## Step 3: Retrieve portfolio items for that job
Use the `jobId` query parameter to find associated portfolio items.

Example: portfolio items for **Varicent** (`jobId: 1`):
```
curl "http://localhost:3000/portfolio?jobId=1"
```

Example response:
```
[
{
"id": 1,
"jobId": 1,
"title": "Release Notes Generator Documentation",
"description": "Authored structured documentation and workflows for an internal AI-powered tool."
},
{
"id": 2,
"jobId": 1,
"title": "DITA XML Documentation Library",
"description": "Created reusable metadata-driven content across multiple product modules."
}
]
```


SmartCV returns every portfolio item linked to this job.

## Step 4: Handle no results
If the job has no associated portfolio items:
```
curl "http://localhost:3000/portfolio?jobId=999"
```

Response:
```
[]
```

An empty array means SmartCV found no portfolio items for that job.

## Step 5: Combine this with a job lookup
You can construct a complete “job + portfolio” view by retrieving both:
```
curl http://localhost:3000/jobs/1
curl "http://localhost:3000/portfolio?jobId=1"
```

You can merge these in your script or editor to build a full résumé profile section.

## Frequently asked questions

### What happens if I pass an invalid jobId?
SmartCV returns an empty array:
```
curl "http://localhost:3000/portfolio?jobId=12345"
```

Response:
```
[]
```

### Can one job have many portfolio items?
Yes.  
SmartCV returns all matching entries for the `jobId`.

### Can multiple jobs share the same portfolio item?
No.  
Each portfolio item stores a single `jobId` value.

### Does SmartCV allow partial matching for jobId?
No.  
`jobId` must match exactly:

Correct:
```
curl "http://localhost:3000/portfolio?jobId=1"
```

Incorrect:
```
curl "http://localhost:3000/portfolio?jobId_like=1"
```

### Why does SmartCV use jobId instead of company names?
SmartCV uses IDs so records remain stable even if job titles or companies change.
