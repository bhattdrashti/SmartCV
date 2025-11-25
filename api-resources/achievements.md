---
title: Achievements
nav_order: 6
parent: API resources
description: "Achievements associated with jobs or skills, useful in CV targeting."
---

# Achievements API

This page explains the `achievements` resource in SmartCV. Each item lists a work achievement connected to a job.

---

## GET `/achievements`
Returns all achievement entries.

## GET `/achievements/{id}`
Returns a single achievement entry by ID.

---

## Fields in this resource

| Field       | Type   | Description |
|-------------|--------|-------------|
| achievement | string | Description of the achievement. |
| jobId       | number | Job this achievement belongs to. |
| id          | number | Unique identifier. |

---

## Example response

```
[
  {
    "achievement": "Authored user guides for ConfigOS MPO, supporting compliance workflows.",
    "jobId": 1,
    "id": 1
  }
]
```

---

## Try it with curl

```
curl http://localhost:3000/achievements
```

---

## Filter items

Filter by jobId:

```
curl "http://localhost:3000/achievements?jobId=1"
```

Filter by achievement text:

```
curl "http://localhost:3000/achievements?achievement=guides"
```

---

## Related topics

- [Jobs API](../api-resources/jobs.md)  
- [Portfolio API](../api-resources/portfolio.md)  
- [Tools API](../api-resources/tools.md)  
- [Credentials API](../api-resources/creds.md)  
- [Backgrounds API](../api-resources/bkgds.md)  
- [Tutorials](../index.md#tutorials)

[← Back to index](../index.md)
