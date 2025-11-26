---
title: Jobs
nav_order: 4
parent: API resources
description: "Job experience entries used to build résumé content."
toc: false
---

# Jobs API

This page explains the `jobs` resource in SmartCV.  
Each job entry stores a past or current role, including company information, dates, and responsibilities.

---

## GET `/jobs`
Returns all job entries.

## GET `/jobs/{id}`
Returns a single job entry by ID.

---

## Fields in this resource

| Field         | Type     | Description |
|---------------|----------|-------------|
| title         | string   | Job title. |
| company       | string   | Employer name. |
| location      | string   | City and region where the job was performed. |
| start_date    | string   | Start date in `YYYY-MM` format. |
| end_date      | string   | End date in `YYYY-MM` format, or `"Present"`. |
| responsibilities | array | Key accomplishments or duties. |
| id            | number   | Unique identifier. |

---

## Example response

```json
[
  {
    "id": 1,
    "title": "Technical Writer",
    "company": "Varicent",
    "location": "Toronto, ON",
    "start_date": "2022-05",
    "end_date": "Present",
    "responsibilities": [
      "Create structured user guides using DITA XML and metadata.",
      "Write UX copy in Figma including tooltips, empty states, and error messages.",
      "Maintain documentation consistency and clarity across channels.",
      "Support release documentation using GenAI-driven tools."
    ]
  }
]
```

## Try it with curl
```
curl http://localhost:3000/jobs
```

## Filter items

### Filter by company
```
curl "http://localhost:3000/jobs?company=Varicent"
```

### Partial match by company
```
curl "http://localhost:3000/jobs?company_like=Wallen"
```

### Filter by job title
```
curl "http://localhost:3000/jobs?title=Technical Writer"
```

### Partial match by title
```
curl "http://localhost:3000/jobs?title_like=Writer"
```

### Filter by location
```
curl "http://localhost:3000/jobs?location=Toronto"
```

### Filter by date ranges (string match)
```
curl "http://localhost:3000/jobs?start_date=2022-05"
```