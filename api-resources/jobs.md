---
title: Jobs
nav_order: 4
parent: API resources
description: "Professional work experience entries with employer, title, and date fields."
---

# Jobs API

This page explains the `jobs` resource in SmartCV. Each job item lists a past or current role.

---

## GET /jobs
Returns all job entries.

## GET /jobs/{id}
Returns a single job entry by ID.

---

## Fields in this resource

| Field      | Type           | Description |
|------------|----------------|-------------|
| title      | string         | The job title. |
| type       | string         | A job category code. |
| employer   | string         | The employer name. |
| startMonth | number         | Start month. |
| startYear  | number         | Start year. |
| endMonth   | number or null | End month. |
| endYear    | number or null | End year. |
| id         | number         | Unique identifier. |

---

## Example response

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

---

## Try it with curl

```
curl http://localhost:3000/jobs
```

---

## Filter items

Filter by employer:

```
curl "http://localhost:3000/jobs?employer=SteelCloud"
```

Filter by job type:

```
curl "http://localhost:3000/jobs?type=wd"
```

Filter by job title:

```
curl "http://localhost:3000/jobs?title=Web Developer"
```

---

## Related topics

- [Backgrounds API](bkgds.md)  
- [Tools API](tools.md)  
- [Credentials API](creds.md)  
- [Portfolio API](portfolio.md)  
- [Achievements API](achievements.md)  
- [Tutorials](../../tutorials/index.md)

[← Back to index](../index.md)
