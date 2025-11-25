---
title: Search tools and credentials
nav_order: 5
parent: Tutorials
description: "Search and filter SmartCV tools and credentials by category or type."
---

# Search tools and credentials by type

This tutorial explains how to search SmartCV tools and credentials by type or category. It shows how to filter skills, degrees, and certificates, read JSON responses, and understand how SmartCV organizes user-provided data.

## Before you begin
Start the SmartCV service.  
If the environment isn’t ready yet, follow:

- [Prerequisites](prerequisites.md)

## Goal of this tutorial
This tutorial covers how to:
- Search tools by type  
- Search credentials by name or location  
- Use query parameters  
- Read JSON responses  
- Handle empty results  

## Step 1: Understand the tools endpoint
The `/tools` resource lists skills and tool categories.  
Each entry contains:

- tool  
- type  
- id  

For the full schema, see:

- [tools](../api/tools.md)

## Step 2: Filter tools by type
Search for tools within a type code.

Example for technical writing tools:

```
curl "http://localhost:3000/tools?type=tw"
```

Example for web-development tools:

```
curl "http://localhost:3000/tools?type=wd"
```

SmartCV returns every tool that matches the type value.

## Step 3: Filter tools by name
Search for a tool directly:

```
curl "http://localhost:3000/tools?tool=Markdown"
```

For substring matching, use `_like`:

```
curl "http://localhost:3000/tools?tool_like=script"
```

This value can match “JavaScript” and related style-sheet tools such as Sass and Less.

## Step 4: Understand the credentials endpoint
The `/creds` resource lists degrees, classes, and certificates.  
Each entry contains:

- cred  
- location  
- id  

For the full schema, see:

- [creds](../api/creds.md)

## Step 5: Filter credentials by name or location
Search by credential name:

```
curl "http://localhost:3000/creds?cred_like=Computer"
```

Search by location:

```
curl "http://localhost:3000/creds?location_like=Washington"
```

Example response:

```
[
  {
    "cred": "Society for Technical Communication (STC)",
    "location": "Washington, DC chapter",
    "id": 2
  }
]
```

## Frequently asked questions

### The response is empty. What does that mean?
SmartCV didn’t find records that match the filter value.

Example:
```
curl "http://localhost:3000/tools?type=ux"
```

Response:
```
[]
```

### Does the search ignore case for substring filters?
Yes. For `_like` queries, SmartCV compares text without considering case.

Examples:
```
curl "http://localhost:3000/tools?tool_like=javascript"
```

```
curl "http://localhost:3000/tools?tool_like=JavaScript"
```

These calls return the same results.

### How does SmartCV support substring matching in tools and creds?
SmartCV uses the `_like` suffix for substring filters.

Examples:
```
curl "http://localhost:3000/tools?tool_like=script"
```

```
curl "http://localhost:3000/creds?cred_like=B."
```

### Why do values with symbols need encoding?
Characters such as `&`, `/`, or `+` need encoding.

Example:
```
curl "http://localhost:3000/creds?cred_like=Society%20for%20Technical%20Communication"
```

### Why do trailing spaces break a match?
Whitespace changes the value.

Example:
```
curl "http://localhost:3000/tools?tool_like=Markdown%20"
```

Response:
```
[]
```

Trim whitespace before sending the request.

## Related resources
These tutorials show how to use other SmartCV data:

- [Filter jobs by employer](filter-jobs-by-employer.md)  
- [Get portfolio items for a job](get-portfolio-for-job.md)  
- [Build a targeted cv](build-targeted-cv.md)  
- [Combine job, portfolio, and achievement data](combine-job-resources.md)  
- [Return to the main index](../index.md)
