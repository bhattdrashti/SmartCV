---
title: Combine job resources
nav_order: 4
parent: Tutorials
description: "Learn how to combine jobs, achievements, and portfolio items to build complete CV sections."
---

# Combine job, portfolio, and achievement data

This tutorial explains how to combine SmartCV data from many resources. It shows how to retrieve a job entry, find its linked achievements and portfolio items, and assemble them into one structured output for résumé building.

## Before you begin
Start the SmartCV service.

If the environment isn’t ready yet, review:

- [Prerequisites](prerequisites.md)

## Goal of this tutorial
This tutorial covers how to:

- Select a job entry  
- Retrieve portfolio items for that job  
- Retrieve achievements for that job  
- Combine the data into a unified structure  
- Use the combined data to build résumé sections  

## Step 1: Retrieve a job entry
Choose a job entry to work with.

Example: your **Varicent Technical Writer** role (`id: 1`)

```json
curl "http://localhost:3000/jobs/1"
```

Example response:

```json
{
"id": 1,
"title": "Technical Writer",
"company": "Varicent",
"location": "Toronto, ON",
"start_date": "2022-05",
"end_date": "Present",
"responsibilities": [
"Write UX copy in Figma including tooltips, empty states, and error messages.",
"Create structured content using DITA XML and metadata.",
"Maintain documentation consistency and clarity across channels."
]
}
```

## Step 2: Retrieve portfolio items for that job
Use the job’s `id` as the `jobId` filter.

```json
curl "http://localhost:3000/portfolio?jobId=1"
```

Example response:

```json
[
{
"id": 1,
"jobId": 1,
"title": "Release Notes Generator Documentation",
"description": "Authored structured documentation and workflows for an internal AI-powered tool."
},
{
"id": 2,
"jobId": 1,
"title": "DITA XML Documentation Library",
"description": "Created reusable metadata-driven content across multiple product modules."
}
]
```

## Step 3: Retrieve achievements for that job
Use the same `jobId` filter.

```json
curl "http://localhost:3000/achievements?jobId=1"
```

Example response:

```json
[
{
"id": 1,
"jobId": 1,
"title": "Implemented Release Notes Workflow",
"description": "Partnered with engineering to design an AI-powered Release Notes Generator."
}
]
```

## Step 4: Combine the data into one structure
Assemble the job, portfolio items, and achievements into one JSON object:

```json
{
"job": {
"id": 1,
"title": "Technical Writer",
"company": "Varicent",
"location": "Toronto, ON",
"start_date": "2022-05",
"end_date": "Present"
},
"portfolio_items": [
{
"title": "Release Notes Generator Documentation",
"description": "Authored structured documentation and workflows for an internal AI-powered tool."
},
{
"title": "DITA XML Documentation Library",
"description": "Created reusable metadata-driven content across multiple product modules."
}
],
"achievements": [
{
"title": "Implemented Release Notes Workflow",
"description": "Partnered with engineering to design an AI-powered Release Notes Generator."
}
]
}
```

Use this combined structure to create:

- Complete résumé experience sections  
- Job summaries  
- Achievement highlights  
- Work sample lists  

## Step 5: Review and refine the combined data
Keep only items that match the target role.

Example refined summary:

```json
{
"summary": [
"Authored UX copy and interface messaging across multiple Varicent modules.",
"Developed reusable DITA XML documentation components.",
"Designed structured workflows for the AI-driven Release Notes Generator."
]
}
```

## Frequently asked questions

### The response is empty. What does that mean?
SmartCV didn’t find any records matching your filter.

Example:
```json
curl "http://localhost:3000/achievements?jobId=0"
```

Response:
```json
[]
```

### Does the search ignore case for substring filters?
Yes. `_like` filters ignore case.

Example:
```json
curl "http://localhost:3000/achievements?description_like=release"
```

### How does SmartCV support substring matching?
Use `_like` to perform text searches.

Example:
```json
curl "http://localhost:3000/portfolio?title_like=XML"
```

### Why do values with symbols need encoding?
Characters such as `(`, `)`, `&`, `/`, `%` require encoding.

Example:
```json
curl "http://localhost:3000/jobs?company=Wallenstein%20Equipment%20Inc."
```

### Why do trailing spaces break a match?
Whitespace changes the value.

Example:
```json
curl "http://localhost:3000/jobs?company=Varicent%20"
```

Response:
```json
[]
```

Trim spaces before sending the request.