---
title: Getting started
nav_order: 2
has_children: true
toc: false
description: "Learn what SmartCV does, how to set up your environment, and how to navigate the documentation."
---

# Getting started

Use this page to get oriented before working with SmartCV. This section explains what SmartCV does, how to prepare your environment, and where to go next in the documentation.

## What SmartCV does
SmartCV models structured career-related data—jobs, tools, credentials, achievements, and portfolio items.  
You can use SmartCV to:

- Explore career data  
- Filter and combine resources  
- Build résumé sections  
- Generate targeted CV content  

SmartCV runs locally using JSON Server, allowing you to make real API calls with your dataset.

## Before you begin
Before using SmartCV, complete the setup instructions:

- [Prerequisites](./prerequisites.md)

Once the prerequisites are installed, you will be able to start the SmartCV JSON Server and test API requests.

## Quick start
Follow these steps to verify your environment:

### 1. Start the SmartCV JSON server
```
json-server --watch db.json --port 3000
```

### 2. Test a simple GET request
Confirm the server is running by retrieving all jobs:
```
curl http://localhost:3000/jobs
```

### 3. Add a sample job entry
Use this example to confirm that POST requests work:
```
curl -X POST http://localhost:3000/jobs
-H "Content-Type: application/json"
-d '{"title":"Technical Writer","company":"Example Corp","location":"Remote","start_date":"2025-01"}'
```

If these commands succeed, SmartCV is ready.

## How to navigate this documentation
Follow this recommended path to learn SmartCV efficiently.

### 1. Learn the SmartCV resources
These pages describe each resource and its data fields:

- [Backgrounds](../api-resources/bkgds.md)  
- [Tools](../api-resources/tools.md)  
- [Credentials](../api-resources/creds.md)  
- [Jobs](../api-resources/jobs.md)  
- [Achievements](../api-resources/achievements.md)  
- [Portfolio](../api-resources/portfolio.md)

### 2. Follow step-by-step tutorials
The tutorials show how to filter, combine, and apply SmartCV data:

- [Tutorials Overview](../tutorials/index.md)

### 3. Troubleshoot errors
If anything fails during setup or requests, see:

- [Troubleshooting](./prerequisites.md#troubleshooting)

## Next steps
After completing this section, you will be able to:

- Navigate the SmartCV documentation  
- Run SmartCV locally  
- Make API calls against your résumé dataset  
- Follow the tutorials to build targeted and combined CV outputs  

You can now begin exploring SmartCV resources or start your first tutorial.