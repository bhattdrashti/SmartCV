---
title: Achievements
nav_order: 6
parent: API resources
description: "Achievements associated with jobs, useful for résumé generation and targeting."
toc: false
---

# Achievements API

This page describes the `achievements` resource in SmartCV.  
Each achievement represents a measurable accomplishment tied to a specific job.

---

## GET `/achievements`
Returns all achievement entries.

## GET `/achievements/{id}`
Returns a single achievement entry by ID.

---

## Fields in this resource

| Field       | Type   | Description |
|-------------|--------|-------------|
| achievement | string | Description of the accomplishment. |
| jobId       | number | ID of the job this achievement belongs to. |
| id          | number | Unique identifier. |

---

## Example response

```
[
  {
    "id": 1,
    "jobId": 1,
    "achievement": "Created structured user guides using DITA XML and metadata for findability and reuse."
  },
  {
    "id": 2,
    "jobId": 1,
    "achievement": "Authored release documentation and leveraged GenAI-driven tooling to automate note creation."
  },
  {
    "id": 3,
    "jobId": 1,
    "achievement": "Produced UX copy for tooltips, empty states, and error messages in Figma."
  }
]
```
## Try it with curl

```
curl http://localhost:3000/achievements
```
## Filter items

### Filter achievements by job:
```
curl "http://localhost:3000/achievements?jobId=1"
```
### Filter by keyword:
```
curl "http://localhost:3000/achievements?achievement_like=DITA"
```