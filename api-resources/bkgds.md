---
title: Backgrounds
nav_order: 1
parent: API resources
description: "Career backgrounds and categories used to classify user experience."
toc: false
---

# Backgrounds API

This page explains the `bkgds` resource in SmartCV.  
Each item represents a background category—areas of expertise or domains supporting résumé building.

---

## GET `/bkgds`
Returns all background entries.

## GET `/bkgds/{id}`
Returns a single background entry by ID.

---

## Fields in this resource

| Field | Type   | Description |
|-------|--------|-------------|
| bkgd  | string | A background category representing a domain of expertise. |
| id    | number | Unique identifier. |

---

## Example response

```json
[
  { "id": 1, "bkgd": "Technical Writing" },
  { "id": 2, "bkgd": "Structured Authoring (DITA XML)" },
  { "id": 3, "bkgd": "UX Writing & Microcopy" },
  { "id": 4, "bkgd": "Documentation Architecture" },
  { "id": 5, "bkgd": "User Assistance & Help Systems" }
]
```

## Try it with curl
```
curl http://localhost:3000/bkgds
```

## Filter items

### Filter by background category:
```
curl "http://localhost:3000/bkgds?bkgd=Technical Writing"
```

### Partial match search:
```
curl "http://localhost:3000/bkgds?bkgd_like=DITA"
```