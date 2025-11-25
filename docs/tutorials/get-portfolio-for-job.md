---
title: Get portfolio items for a job
nav_order: 2
parent: Tutorials
description: "Retrieve portfolio items related to a specific job entry."
---

# Get portfolio items for a job

This tutorial explains how to retrieve portfolio items linked to a specific job. It shows how to use the `portfolio` resource with filters, read JSON responses, and understand how SmartCV connects work samples to job entries.

## Before you begin
Start the SmartCV service.  
If the environment isn’t ready yet, follow:

- [Prerequisites](prerequisites.md)

## Goal of this tutorial
This tutorial covers how to:
- Call the `/portfolio` API  
- Filter portfolio items by jobId  
- Use query parameters  
- Read JSON responses  
- Handle empty results  

## Step 1: Understand the endpoint
The `portfolio` resource stores work samples linked to jobs.  
Each entry contains:

- name  
- URL  
- jobId  
- id  

For the full schema, see:

- [portfolio](../api/portfolio.md)

## Step 2: Retrieve the job id
First, find the job entry you want to use and note its `id` value.

Example:
```
curl "http://localhost:3000/jobs?employer_like=NRSI"
```

Response:
```
[
  {
    "title": "Web Developer",
    "type": "wd",
    "employer": "Non-Roman Script Initiative (NRSI)",
    "startMonth": 6,
    "startYear": 2015,
    "endMonth": 10,
    "endYear": 2017,
    "id": 4
  }
]
```

In this example, the job id is `4`.

## Step 3: Filter portfolio items by jobId
Use the job id from Step 2 to fetch linked work samples:

```
curl "http://localhost:3000/portfolio?jobId=4"
```

Example response:

```
[
  {
    "name": "SIL PRODUCT WEBSITES",
    "url": "https://emcham.io/product-sites/",
    "jobId": 4,
    "id": 4
  },
  {
    "name": "WORDPRESS SHORT CODE TO GENERATE CSS FOR ARABIC CALLIGRAPHY",
    "url": "https://emcham.io/wp-css-arabic/",
    "jobId": 4,
    "id": 5
  }
]
```

SmartCV returns every portfolio item linked to jobId `4`.

## Step 4: Handle no results
If the jobId doesn’t match any portfolio item:

```
curl "http://localhost:3000/portfolio?jobId=999"
```

Response:

```
[]
```

An empty array means no portfolio items link to that job.

## Step 5: Filter portfolio items by name
You can also filter by the portfolio name field:

```
curl "http://localhost:3000/portfolio?name_like=THEME"
```

This value can match entries that include the word “theme” in the name.

## Frequently asked questions

### The response is empty. What does that mean?
SmartCV didn’t find records that match the filter value.

Example:
```
curl "http://localhost:3000/portfolio?jobId=0"
```

Response:
```
[]
```

### Does the search ignore case?
Yes. SmartCV compares text without considering case for `_like` queries.

Example:
```
curl "http://localhost:3000/portfolio?name_like=websites"
```

This value matches `"SIL PRODUCT WEBSITES"`.

### How does SmartCV handle substring matching for names?
SmartCV uses the `_like` suffix for substring matching.

Example:
```
curl "http://localhost:3000/portfolio?name_like=WILDFIRE"
```

This value can match entries with “WILDFIRE” in the name.

### Why do values with symbols fail?
Characters such as `&`, `/`, or `+` need encoding.

Example:
```
curl "http://localhost:3000/portfolio?name_like=CSS%20FOR%20ARABIC"
```

### Why do trailing spaces break a match?
Whitespace changes the value.

Example:
```
curl "http://localhost:3000/portfolio?name_like=WEBSITES%20"
```

Response:
```
[]
```

Trim whitespace before sending the request.

## Related resources
These tutorials continue the workflow and show how to use other SmartCV data:

- [Filter jobs by employer](filter-jobs-by-employer.md)  
- [Build a targeted cv](build-targeted-cv.md)  
- [Combine job, portfolio, and achievement data](combine-job-resources.md)  
- [Search tools and credentials by type](search-tools-and-creds.md)  
- [Return to the main index](../index.md)
