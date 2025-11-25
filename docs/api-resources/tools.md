# Tools API

This page explains the `tools` resource in the SmartCV service. Each item lists a tool or software skill.

---

## GET /tools
Returns all tool entries.

## GET /tools/{id}
Returns a single tool entry by ID.

---

## Fields in this resource

| Field | Type   | Description |
|--------|--------|-------------|
| tool   | string | A skill or software tool. |
| type   | string | A category code for the tool. |
| id     | number | Unique identifier. |

---

## Example response

```
[
  { "tool": "Adobe FrameMaker", "type": "tw", "id": 1 },
  { "tool": "Confluence", "type": "tw", "id": 2 },
  { "tool": "Markdown", "type": "tw", "id": 4 }
]
```

---

## Try it with curl

```
curl http://localhost:3000/tools
```

---

## Filter items

Filter by tool name:

```
curl "http://localhost:3000/tools?tool=Markdown"
```

Filter by category:

```
curl "http://localhost:3000/tools?type=tw"
```

---

## Related topics

- [Backgrounds API](bkgds.md)  
- [Credentials API](creds.md)  
- [Jobs API](jobs.md)  
- [Portfolio API](portfolio.md)  
- [Achievements API](achievements.md)  
- [Tutorials](../../tutorials/index.md)

[← Back to index](../index.md)
