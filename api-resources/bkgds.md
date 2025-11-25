---
title: Backgrounds
nav_order: 1
parent: API resources
description: "Career backgrounds and categories used to classify user experience."
---

# Backgrounds API

This page explains the `bkgds` resource in the SmartCV service. Each item lists a background category provided by the user.

---

## GET /bkgds
Returns all background entries.

## GET /bkgds/{id}
Returns a single background entry by ID.

---

## Fields in this resource

| Field | Type   | Description |
|-------|--------|-------------|
| bkgd  | string | A background category. |
| id    | number | Unique identifier. |

---

## Example response

```
[
  { "bkgd": "Multilingual Content", "id": 1 },
  { "bkgd": "Structured Authoring", "id": 2 },
  { "bkgd": "Technical Writing", "id": 3 },
  { "bkgd": "UI/Web Design", "id": 4 }
]
```

---

## Try it with curl

```
curl http://localhost:3000/bkgds
```

---

## Filter items

Filter by background category:

```
curl "http://localhost:3000/bkgds?bkgd=Technical Writing"
```

---

## Related topics

- [Tools API](tools.md)  
- [Credentials API](creds.md)  
- [Jobs API](jobs.md)  
- [Portfolio API](portfolio.md)  
- [Achievements API](achievements.md)  
- [Tutorials](../../tutorials/index.md)

[← Back to index](../index.md)
