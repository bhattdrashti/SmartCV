---
title: Credentials
nav_order: 3
parent: API resources
description: "Degrees, certifications, and educational credentials stored in SmartCV."
toc: false
---

# Credentials API

This page explains the `creds` resource in SmartCV.  
Each item represents a degree, certificate, or professional training achievement.

---

## GET `/creds`
Returns all credential entries.

## GET `/creds/{id}`
Returns a single credential entry by ID.

---

## Fields in this resource

| Field    | Type   | Description |
|----------|--------|-------------|
| cred     | string | Name of the degree or certification. |
| provider | string | Institution or organization that issued the credential. |
| id       | number | Unique identifier. |

---

## Example response

```
[
  {
    "id": 1,
    "cred": "Certified AI Technical Writer",
    "provider": "Technical Writer HQ"
  },
  {
    "id": 2,
    "cred": "Fundamentals of UX Writing",
    "provider": "UX Content Collective"
  },
  {
    "id": 3,
    "cred": "Paligo Certified User",
    "provider": "Paligo"
  },
  {
    "id": 4,
    "cred": "Graduate Certificate - Technical Communication",
    "provider": "Seneca College"
  },
  {
    "id": 5,
    "cred": "Graduate Certificate - Information Technology",
    "provider": "Algoma University"
  },
  {
    "id": 6,
    "cred": "B.Sc. Information Technology & Computer Applications",
    "provider": "Gujarat University"
  }
]
```

## Try it with curl
```
curl http://localhost:3000/creds
```

## Filter items

### Filter by credential name
```
curl "http://localhost:3000/creds?cred=Paligo%20Certified%20User"
```

### Partial match
```
curl "http://localhost:3000/creds?cred_like=Certificate"
```

### Filter by provider
```
curl "http://localhost:3000/creds?provider=Seneca%20College"
```

### Partial match by provider
```
curl "http://localhost:3000/creds?provider_like=Collective"
```