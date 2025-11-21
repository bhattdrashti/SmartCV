# Prerequisites

Follow these steps before you start the SmartCV [tutorials](../tutorials/index.html). This page explains the tools you need, how to set up the project, how to run the local server, and how to confirm that SmartCV works on your machine.

---

## About the SmartCV API
- **Runs on:** your local computer  
- **Main address:** http://localhost:3000  
- **Data format:** JavaScript Object Notation (JSON)

SmartCV uses a simple REST-style layout. Each collection inside the database file becomes an endpoint.

---

## Getting started
Install these tools before you work with SmartCV:

- [GitHub account](https://github.com)  
- [Git](https://git-scm.com/downloads)  
- [Node.js and npm](https://nodejs.org)  
- [json-server](https://github.com/typicode/json-server)  
- [curl](https://curl.se) or the [Postman desktop app](https://www.postman.com/downloads)

These tools help you download the project, run the service, and make test requests.

---

## Set up

### Step 1: Fork the SmartCV repository
Open the SmartCV repository on GitHub. Select **Fork** to create your own copy under your account.

### Step 2: Clone your fork
Open a terminal and run:

```bash
git clone <your-fork-url>
```

Replace `<your-fork-url>` with the link to your forked copy of SmartCV.

### Step 3: Open the API folder
Move into the folder that contains the database file:

```bash
cd <your-github-workspace>/SmartCV/api
```

Example:

```bash
cd ~/Documents/GitHub/SmartCV/api
```

### Step 4: Start the json-server
Run the SmartCV database with this command:

```bash
json-server -w db-cv.json
```

If the server starts correctly, you see this list:

```
Resources
http://localhost:3000/bkgds
http://localhost:3000/tools
http://localhost:3000/creds
http://localhost:3000/jobs
http://localhost:3000/portfolio
http://localhost:3000/achievements

Home
http://localhost:3000
```

This means the database loaded and SmartCV is active.

---

## Test the service

### Step 1: Open a second terminal window
In a new window, send a request to the [`jobs`](../tutorials/index.html) endpoint:

```bash
curl http://localhost:3000/jobs
```

### Step 2: Check the response
A correct response looks like this:

```json
[
  {
    "title": "Technical Writer",
    "type": "wd",
    "employer": "SteelCloud LLC",
    "startMonth": 2,
    "startYear": 2023,
    "endMonth": null,
    "endYear": null,
    "id": 1
  }
]
```

This test uses the [`jobs`](../tutorials/index.html) collection because it has detailed data and is easy to review.  

You can test any other SmartCV resource the same way:

```
curl http://localhost:3000/tools
curl http://localhost:3000/bkgds
curl http://localhost:3000/creds
curl http://localhost:3000/portfolio
curl http://localhost:3000/achievements
```

If one request works, the server is running correctly.

---

## SmartCV resources

After you start json-server, you can open these links in your browser:

- http://localhost:3000/bkgds  
- http://localhost:3000/tools  
- http://localhost:3000/creds  
- http://localhost:3000/jobs  
- http://localhost:3000/portfolio  
- http://localhost:3000/achievements

Each link shows the raw JSON data for that resource. This helps you confirm that the server is running and that SmartCV loaded the database correctly.

If any link shows an error or empty data, refer to the Troubleshooting section to fix the issue.


---

## Troubleshooting

Use this table to fix common setup problems with SmartCV.

| Problem | Possible cause | How to fix it |
|--------|----------------|----------------|
| **json-server doesn't start** | You aren't in the `api` folder | Move into the `api` folder and try again |
| | Node.js or npm is missing | Install Node.js from https://nodejs.org |
| | json-server isn't installed | Install json-server: `npm install -g json-server` |
| **curl shows no data** | json-server isn't running | Start json-server with: `json-server -w db-cv.json` |
| | You typed the wrong URL | Use a valid endpoint such as `/jobs` |
| | Port 3000 is already in use | Stop the other program and restart json-server |
| | The database file has an error | Check `db-cv.json` for missing commas or brackets |
| **curl shows “404 not found”** | The endpoint doesn't exist | Use one of the SmartCV endpoints: `/bkgds`, `/tools`, `/creds`, `/jobs`, `/portfolio`, `/achievements` |
| **json-server stops with an error** | The terminal session crashed | Close the terminal window and open a new one |
| | json-server failed to load the file | Restart with: `json-server -w db-cv.json` |
| **“command not found”** | Node.js isn't installed | Install Node.js |
| | json-server isn't installed | Install json-server globally |



---

## Next steps

- [Prerequisites](../getting-started/prerequisites.html)
- [API References](../index.html#api-references)
- [Tutorials](../tutorials/index.html)

---

[← Back to home](../index.html)
