---
title: Build a targeted CV
nav_order: 3
parent: Tutorials
description: "Build a CV that matches job description keywords using SmartCV resources."
---

# Build a targeted CV

This tutorial explains how to build a targeted cv from SmartCV data. It shows how to select job entries, gather work samples, link achievements, and create a focused output that matches a job description.

## Before you begin
Start the SmartCV service.  
If the environment isn’t ready yet, follow:

- [Prerequisites](prerequisites.md)

## Goal of this tutorial
This tutorial covers how to:
- Identify relevant jobs  
- Gather portfolio items for those jobs  
- Gather achievements for those jobs  
- Combine the data into a targeted cv structure  
- Read JSON responses used in cv generation  

## Step 1: Identify relevant jobs
Search for job entries that relate to the new role.

Example: filter by employer:

```
curl "http://localhost:3000/jobs?employer_like=Baxter"
```

Example: filter by title:

```
curl "http://localhost:3000/jobs?title_like=Developer"
```

Use values from the job description to guide these filters.

## Step 2: Gather portfolio items for each job
For each selected job, use its `id` as the `jobId` filter in the portfolio resource.

Example for job id 3:

```
curl "http://localhost:3000/portfolio?jobId=3"
```

This call returns portfolio entries linked to that job.

## Step 3: Gather achievements for each job
Use the same job id to fetch achievements:

```
curl "http://localhost:3000/achievements?jobId=3"
```

These entries describe outcomes and results for that job.

## Step 4: Combine job, portfolio, and achievement data
Create a combined structure that merges a job with its work samples and achievements.

Example combined structure:

```
{
  "job": {
    "title": "Web Developer",
    "type": "wd",
    "employer": "Internet Publishing Service (IPS)",
    "startMonth": 1,
    "startYear": 2018,
    "endMonth": 2,
    "endYear": 2022,
    "id": 3
  },
  "portfolio_items": [
    {
      "name": "WILDFIRE 5 ADMIN THEME",
      "url": "https://emcham.io/wildfire-5-admin-theme"
    },
    {
      "name": "WILDFIRE CLARO ADMIN THEME",
      "url": "https://emcham.io/wildfire-admin-claro-theme"
    }
  ],
  "achievements": [
    {
      "achievement": "Created multilingual documentation for Drupal modules and themes, including UI localization.",
      "id": 10
    },
    {
      "achievement": "Authored integration guides for custom theme features.",
      "id": 11
    }
  ]
}
```

This combined structure acts as the base for a targeted cv section.

## Step 5: Focus on the target role
Filter the combined data so it aligns with the new role.  
Highlight items that show:

- relevant tools  
- relevant responsibilities  
- strong achievements  

Example trimmed cv section:

```
{
  "job_title": "Web Developer",
  "employer": "Internet Publishing Service (IPS)",
  "highlights": [
    "Created multilingual documentation for Drupal themes.",
    "Authored integration guides for custom theme features.",
    "Delivered theme work that improved user experience."
  ],
  "samples": [
    "WILDFIRE 5 ADMIN THEME",
    "WILDFIRE CLARO ADMIN THEME"
  ]
}
```

## Frequently asked questions

### The response is empty. What does that mean?
SmartCV didn’t find records that match the filter value.

Example:
```
curl "http://localhost:3000/jobs?title_like=Architect"
```

Response:
```
[]
```

### Does the search ignore case?
Yes. SmartCV compares text without considering case for `_like` queries.

Examples:
```
curl "http://localhost:3000/jobs?title_like=developer"
```

```
curl "http://localhost:3000/jobs?title_like=Developer"
```

These calls return the same results.

### How does SmartCV support substring matching for titles?
SmartCV uses the `_like` suffix for substring matching.

Example:
```
curl "http://localhost:3000/jobs?title_like=Writer"
```

This value can match “Technical Writer.”

### Why do values with symbols need encoding?
Characters such as `&`, `/`, and `+` need encoding.

Example:
```
curl "http://localhost:3000/jobs?employer=Internet%20Publishing%20Service%20%28IPS%29"
```

### Why do trailing spaces break a match?
Whitespace changes the value.

Example:
```
curl "http://localhost:3000/jobs?title_like=Developer%20"
```

Response:
```
[]
```

Trim whitespace before sending the request.

## Related resources
These tutorials continue the workflow and show how to use other SmartCV data:

- [Filter jobs by employer](filter-jobs-by-employer.md)  
- [Get portfolio items for a job](get-portfolio-for-job.md)  
- [Combine job, portfolio, and achievement data](combine-job-resources.md)  
- [Search tools and credentials by type](search-tools-and-creds.md)  
- [Return to the main index](../index.md)
