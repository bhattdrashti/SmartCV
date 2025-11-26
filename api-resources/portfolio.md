---
title: Portfolio
nav_order: 5
parent: API resources
description: "Portfolio items linked to jobs, used for building targeted CV outputs."
toc: false
---

# Portfolio API

This page explains the `portfolio` resource in SmartCV.  
Each item represents a work sample, demo, UX writing artifact, or documentation sample connected to a specific job.

---

## GET `/portfolio`
Returns all portfolio entries.

## GET `/portfolio/{id}`
Returns a single portfolio entry by ID.

---

## Fields in this resource

| Field | Type   | Description |
|--------|--------|-------------|
| name   | string | Name or title of the work sample. |
| url    | string | Link to the sample (or `null` if not publicly available). |
| jobId  | number | ID of the job this sample is associated with. |
| id     | number | Unique identifier. |

---

## Example response

```
[
  {
    "id": 1,
    "jobId": 1,
    "name": "Release Notes – GenAI Automation Workflow",
    "url": null
  },
  {
    "id": 2,
    "jobId": 1,
    "name": "DITA XML User Guide (Structured Authoring)",
    "url": null
  },
  {
    "id": 3,
    "jobId": 2,
    "name": "Operator's Manual – Agricultural Equipment",
    "url": null
  },
  {
    "id": 4,
    "jobId": 3,
    "name": "Quick Start Guide – Security Camera Setup",
    "url": null
  }
]
```

## Try it with curl
```
curl http://localhost:3000/portfolio
```

## Filter items

### Filter by jobId
```
curl "http://localhost:3000/portfolio?jobId=1"
```

### Filter by sample name (exact match)
```
curl "http://localhost:3000/portfolio?name=Operator%27s%20Manual%20%E2%80%93%20Agricultural%20Equipment"
```

### Partial match by sample name
```
curl "http://localhost:3000/portfolio?name_like=Guide"
```