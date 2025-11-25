---
title: Combine job resources
nav_order: 4
parent: Tutorials
description: "Learn how to combine jobs, achievements, backgrounds, and portfolios."
---

# Combine job, portfolio, and achievement data

This tutorial explains how to combine SmartCV data from different resources. It shows how to gather job entries, link work samples, attach achievements, and produce a combined structure for analysis or cv building.

## Before you begin
Start the SmartCV service.  
If the environment isn’t ready yet, follow:

- [Prerequisites](prerequisites.md)

## Goal of this tutorial
This tutorial covers how to:
- Select a job entry  
- Retrieve portfolio items for that job  
- Retrieve achievements for that job  
- Combine the three resources into one structure  
- Use the combined data for summaries or cv sections  

## Step 1: Retrieve a job entry
Begin by selecting a job entry you want to use.

Example:
```
curl "http://localhost:3000/jobs?id=3"
```

Response:
```
[
  {
    "title": "Web Developer",
    "type": "wd",
    "employer": "Internet Publishing Service (IPS)",
    "startMonth": 1,
    "startYear": 2018,
    "endMonth": 2,
    "endYear": 2022,
    "id": 3
  }
]
```

## Step 2: Retrieve portfolio items for that job
Use the job id from Step 1 as the jobId filter:

```
curl "http://localhost:3000/portfolio?jobId=3"
```

Response:
```
[
  {
    "name": "WILDFIRE 5 ADMIN THEME",
    "url": "https://emcham.io/wildfire-5-admin-theme",
    "jobId": 3,
    "id": 2
  },
  {
    "name": "WILDFIRE CLARO ADMIN THEME",
    "url": "https://emcham.io/wildfire-admin-claro-theme",
    "jobId": 3,
    "id": 3
  }
]
```

## Step 3: Retrieve achievements for that job
Use the same job id for the achievements resource:

```
curl "http://localhost:3000/achievements?jobId=3"
```

Response:
```
[
  {
    "achievement": "Created multilingual documentation for Drupal modules and themes, including UI localization.",
    "jobId": 3,
    "id": 10
  },
  {
    "achievement": "Authored integration guides for custom theme features, enhancing visual customization and user experience.",
    "jobId": 3,
    "id": 11
  },
  {
    "achievement": "Provided peer training on theme configuration and documentation best practices.",
    "jobId": 3,
    "id": 12
  }
]
```

## Step 4: Combine the data into one structure
Create a combined output that includes the job entry, its work samples, and its achievements:

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
      "achievement": "Authored integration guides for custom theme features, enhancing visual customization and user experience.",
      "id": 11
    },
    {
      "achievement": "Provided peer training on theme configuration and documentation best practices.",
      "id": 12
    }
  ]
}
```

This combined structure acts as a single source of information about that job.

## Step 5: Review and refine the combined data
Review the combined content and keep the items that support the target role.  
Use this structure to build summaries, cv sections, or reports.

Example refined summary:

```
{
  "summary": [
    "Delivered multilingual Drupal themes with localized UI.",
    "Produced integration guides that improved customization.",
    "Trained peers on theme configuration and documentation practices."
  ]
}
```

## Questions and answers

### The response is empty. What does that mean?
SmartCV didn’t find records that match the filter value.

Example:
```
curl "http://localhost:3000/achievements?jobId=0"
```

Response:
```
[]
```

### Does the search ignore case for substring filters?
Yes. For `_like` queries, SmartCV compares text without considering case.

Example:
```
curl "http://localhost:3000/achievements?achievement_like=drupal"
```

This value matches achievements that mention “Drupal.”

### How does SmartCV support substring matching in achievements?
SmartCV uses the `_like` suffix.

Example:
```
curl "http://localhost:3000/achievements?achievement_like=training"
```

This value can match entries that describe training work.

### Why do values with symbols need encoding?
Characters such as `&`, `/`, or `+` need encoding.

Example:
```
curl "http://localhost:3000/jobs?employer=Non-Roman%20Script%20Initiative%20%28NRSI%29"
```

### Why do trailing spaces break a match?
Whitespace changes the value.

Example:
```
curl "http://localhost:3000/portfolio?name_like=WILDFIRE%20"
```

Response:
```
[]
```

Trim whitespace before sending the request.
