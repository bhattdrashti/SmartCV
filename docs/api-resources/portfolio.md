# Portfolio API

This page explains the `portfolio` resource in SmartCV. Each item lists a work sample linked to a job.

---

## GET /portfolio
Returns all portfolio entries.

## GET /portfolio/{id}
Returns a single portfolio entry by ID.

---

## Fields in this resource

| Field | Type   | Description |
|--------|--------|-------------|
| name   | string | Name of the work sample. |
| URL    | string | Link to the sample. |
| jobId  | number | Job this sample belongs to. |
| id     | number | Unique identifier. |

---

## Example response

```
[
  {
    "name": "INSTRUCTIONS FOR USE, Welch Allyn FlexiPort Disposable Blood Pressure Cuff",
    "url": "https://bit.ly/46vnUdU",
    "jobId": 2,
    "id": 1
  }
]
```

---

## Try it with curl

```
curl http://localhost:3000/portfolio
```

---

## Filter items

Filter by jobId:

```
curl "http://localhost:3000/portfolio?jobId=2"
```

Filter by sample name:

```
curl "http://localhost:3000/portfolio?name=WordPress"
```

---

## Related topics

- [Jobs API](jobs.md)  
- [Achievements API](achievements.md)  
- [Tools API](tools.md)  
- [Credentials API](creds.md)  
- [Backgrounds API](bkgds.md)  
- [Tutorials](../../tutorials/index.md)

[← Back to index](../index.md)
