---
title: Search tools and credentials by type
nav_order: 5
parent: Tutorials
description: "Learn how to retrieve specific tools, skills, and credentials using category and keyword filters."
---

# Search tools and credentials by type

This tutorial explains how to filter SmartCV’s `tools` and `credentials` resources. It shows how to search for specific skills, tool categories, and certifications to support targeted résumé building.

## Before you begin
Start the SmartCV service.

If the environment isn’t ready yet, review:

- [Prerequisites](prerequisites.md)

## Goal of this tutorial
This tutorial covers how to:

- Filter tools by category  
- Search tool items using keyword filters  
- Retrieve credentials by type  
- Search certifications and courses  
- Use filtered results to build skill and certification sections  

## Step 1: Search tools by category
Tools are grouped into résumé-relevant categories such as:

- Authoring Tools  
- Design Tools  
- Programming Languages  
- Frameworks  

Example: list your **authoring tools**:
```
curl "http://localhost:3000/tools?category=Authoring%20Tools"
```
Example categories based on your dataset:

- Adobe FrameMaker  
- Paligo  
- RoboHelp  
- MadCap Flare  

---

## Step 2: Search design tools
Retrieve design tools used for documentation and UI work.
```
curl "http://localhost:3000/tools?category=Design%20Tools"
```

Returns skills such as:

- Figma  
- Photoshop  
- Illustrator  
- Canva  

---

## Step 3: Search tools by keyword
Use the `_like` suffix for partial matches.

### Example: Search for Figma
```
curl "http://localhost:3000/tools?items_like=Figma"
```

### Example: Search for DITA XML
```
curl "http://localhost:3000/tools?items_like=DITA"
```

### Example: Search for SolidWorks
```
curl "http://localhost:3000/tools?items_like=SolidWorks"
```

---

## Step 4: Search credentials by type
You can filter credentials by:

- Certification  
- Course  
- Education  

### Example: List all certifications
```
curl "http://localhost:3000/credentials?type=Certification"
```

### Example: List all UX or writing-related courses
```
curl "http://localhost:3000/credentials?name_like=Writing"
```

### Example: List AI-related certifications
```
curl "http://localhost:3000/credentials?name_like=AI"
```
---

## Step 5: Find education records
Use keyword filters to locate relevant degrees.

### Example: Search IT-related education
```
curl "http://localhost:3000/credentials?name_like=Information"
```

### Example: Search Technical Communication programs
```
curl "http://localhost:3000/credentials?name_like=Technical"
```
---

## Frequently asked questions

### Can a tool belong to multiple categories?
No.  
Each tool category is fixed, similar to a résumé section.

### Are `_like` searches case-insensitive?
Yes.  
SmartCV ignores letter case for all substring matches.

Example:
```
curl "http://localhost:3000/tools?items_like=dita"
```

### Why do credentials sometimes return multiple results?
Keyword searches match all credentials that contain the search text.

Example:
```
curl "http://localhost:3000/credentials?name_like=Technical"
```

This matches:

- Technical Communication (Seneca College)  
- Certified AI Technical Writer  

### Why do some values require encoding?
Characters such as `&`, `/`, `(`, `)` require encoding to be valid in URLs.

Example:
```
curl "http://localhost:3000/credentials?name=Paligo%20Certified%20User"
```

### Why do trailing spaces break a match?
Whitespace changes the value, so SmartCV treats it as a different string.

Example:
```
curl "http://localhost:3000/tools?category=Design%20Tools%20"
```

Response:
```
[]
```

Trim extra spaces before sending the request.
