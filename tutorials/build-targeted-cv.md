---
title: Build a targeted CV
nav_order: 3
parent: Tutorials
description: "Learn how to assemble a targeted CV using SmartCV by filtering jobs, skills, and credentials."
---

# Build a targeted CV

This tutorial explains how to create a targeted résumé by combining job experience, skills, and credentials. It shows how to use SmartCV filters to match a job posting and assemble a focused profile.

## Before you begin
Start the SmartCV service.

If the environment isn’t ready yet, review:

- [Prerequisites](prerequisites.md)

## Goal of this tutorial
This tutorial covers how to:

- Identify relevant job roles  
- Filter skills using keyword queries  
- Retrieve matching credentials  
- Combine data into a targeted résumé package  

## Step 1: Find relevant job experience
Use SmartCV filters to match job roles by title.

Example: retrieve your Technical Writer positions:

```
curl "http://localhost:3000/jobs?title_like=Technical"
```

Example output:

```json
[
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
]
```

## Step 2: Filter skills that match the job posting
Assume the targeted job requires DITA XML, Figma, Illustrator, and strong UX writing.

### Example: Search for Figma

```json
curl "http://localhost:3000/tools?items_like=Figma"
```

### Example: Search for DITA XML

```json
curl "http://localhost:3000/tools?items_like=DITA"
```

### Example: Search design tools

```json
curl "http://localhost:3000/tools?category=Design%20Tools"
```

## Step 3: Retrieve relevant credentials
Filter certifications and completed courses.

### Example: Find UX or AI writing certifications

```json
curl "http://localhost:3000/credentials?name_like=Technical"
```

### Example: List all certifications

```json
curl "http://localhost:3000/credentials?type=Certification"
```

## Step 4: Assemble the targeted CV content
A targeted CV typically includes:

- Matching job experience  
- Relevant tools and skills  
- Certifications supporting the role  
- Achievements and portfolio items  

You can combine the filtered responses into a structured packet:

```json
{
"experience": [...],
"skills": [...],
"credentials": [...],
"achievements": [...],
"portfolio": [...]
}
```

## Frequently asked questions

### Do I need to follow the steps in order?

No.  
SmartCV lets you filter in any sequence based on what the job posting requires.

### Why does the targeted CV include credentials?

Credentials strengthen your résumé by showing proof of specialization (for example, “Certified AI Technical Writer”).

### Can I generate a complete CV using one API call?

Not with JSON Server.  
You must combine the data manually or through a script.

### Why do skills appear under different categories?

SmartCV organizes them based on real résumé sections, such as:

- Authoring Tools  
- Design Tools  
- Programming  
- Frameworks  

This helps you build better structured CVs.