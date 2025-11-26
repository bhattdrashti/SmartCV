---
title: Getting started
nav_order: 2
has_children: true
---

# Getting started
Use this page to get oriented before working with SmartCV. This section explains what SmartCV does, how to prepare your environment, and where to go next.

## What SmartCV does
SmartCV models structured career-related data such as backgrounds, tools, credentials, jobs, achievements, and portfolio items. SmartCV lets you combine these resources to build résumé components. Once the prerequisites are complete, you can run SmartCV locally using JSON Server and make actual API requests.

## Before you begin
Review the setup requirements: [Prerequisites](./prerequisites.md)

## Quick start
After completing the prerequisites, verify your setup with these steps.

### Start the SmartCV JSON server
```
json-server --watch db.json --port 3000
```

### Test a simple GET request
```
curl http://localhost:3000/jobs
```

### Add a new job entry
```
curl -X POST http://localhost:3000/jobs
-H "Content-Type: application/json"
-d '{"title":"Software Engineer","company":"Example Corp"}'
```

If these commands work, your environment is ready.

## How to navigate this documentation
Follow this path for the best experience:

### 1. Learn the SmartCV resources
These pages explain each available resource and its fields:

- [Backgrounds](../api-resources/bkgds.md)
- [Tools](../api-resources/tools.md)
- [Credentials](../api-resources/creds.md)
- [Jobs](../api-resources/jobs.md)
- [Achievements](../api-resources/achievements.md)
- [Portfolio](../api-resources/portfolio.md)

### 2. Follow the step-by-step tutorials
These guides show how to use and combine resources:

- [Tutorials Overview](../tutorials/index.md)

### 3. Troubleshoot issues
If you encounter errors, read [Troubleshooting](../getting-started/prerequisites.md#troubleshooting)


