# API request with Python

Scope Of Project: 
- Need to get the list of projects from my github account.

# Implementation

```bash

$: pip install requests

# main.py

import requests

response = requests.get("https://gitlab.com/api/v4/users/naunchi/projects")
my_projects = response.json()

for project in my_projects:
    print(f"Project Name: {project['name']}\nProject Url: {project['web_url']}\n")
