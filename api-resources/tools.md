---
title: Tools
nav_order: 2
parent: API resources
description: "Tools, technologies, and skill categories available in SmartCV."
toc: false
---

# Tools API

This page explains the `tools` resource in SmartCV.  
Each item represents a technical skill, authoring tool, design tool, or programming language used to support résumé generation.

---

## GET `/tools`
Returns all tool entries.

## GET `/tools/{id}`
Returns a single tool entry by ID.

---

## Fields in this resource

| Field | Type   | Description |
|--------|--------|-------------|
| tool   | string | Name of the software, technology, or skill. |
| category | string | The skill category (for example, Writing, Design, Programming). |
| id     | number | Unique identifier. |

---

## Example response

```
[
  {
    "id": 1,
    "tool": "Paligo",
    "category": "Authoring"
  },
  {
    "id": 2,
    "tool": "DITA XML",
    "category": "Architecture"
  },
  {
    "id": 3,
    "tool": "Figma",
    "category": "Design"
  },
  {
    "id": 4,
    "tool": "SolidWorks Composer",
    "category": "3D Illustration"
  },
  {
    "id": 5,
    "tool": "GitHub",
    "category": "Dev Tools"
  },
  {
    "id": 6,
    "tool": "HTML / CSS / JavaScript",
    "category": "Programming"
  }
]
```

## Try it with curl
```
curl http://localhost:3000/tools
```

## Filter items

### Filter by tool name
```
curl "http://localhost:3000/tools?tool=Figma"
```

### Partial match
```
curl "http://localhost:3000/tools?tool_like=XML"
```

### Filter by category
```
curl "http://localhost:3000/tools?category=Authoring"
```

### Partial match by category
```
curl "http://localhost:3000/tools?category_like=Design"
```