---
title: Credentials
nav_order: 3
parent: API resources
description: "Degrees, certificates, and educational credentials stored in SmartCV."
---

# Credentials API

This page explains the `creds` resource in SmartCV. Each item lists a degree, course, or certificate.

---

## GET /creds
Returns all credential entries.

## GET /creds/{id}
Returns a single credential entry by ID.

---

## Fields in this resource

| Field    | Type   | Description |
|-----------|--------|-------------|
| cred      | string | A degree or certificate name. |
| location  | string | Where the user earned the credential. |
| id        | number | Unique identifier. |

---

## Example response

```
[
  {
    "cred": "API Documentation",
    "location": "University of Washington",
    "id": 1
  },
  {
    "cred": "B. Sc., Computer Information Systems",
    "location": "East Texas Baptist University",
    "id": 3
  }
]
```

---

## Try it with curl

```
curl http://localhost:3000/creds
```

---

## Filter items

Filter by credential name:

```
curl "http://localhost:3000/creds?cred=API Documentation"
```

Filter by location:

```
curl "http://localhost:3000/creds?location=Washington"
```

---

## Related topics

- [Backgrounds API](bkgds.md)  
- [Tools API](tools.md)  
- [Jobs API](jobs.md)  
- [Portfolio API](portfolio.md)  
- [Achievements API](achievements.md)  
- [Tutorials](../../tutorials/index.md)

[← Back to index](../index.md)
