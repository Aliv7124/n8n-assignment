# n8n Assignment Submission



---

## Overview
This project contains an automated workflow built using n8n that fetches data from a public API, processes it, and sends alerts based on conditions.

It also includes a QA report identifying issues in a demo web application.

---

## APIs Used

### 1. GitHub REST API
- Endpoint: https://api.github.com/search/repositories
- Purpose: To fetch trending repositories based on a search query
- Reason: It provides structured JSON data suitable for automation and filtering

### 2. Webhook.site API
- Purpose: To receive and verify alerts from the n8n workflow
- Reason: Easy testing endpoint to validate outgoing HTTP requests

---

## Workflow Description

The n8n workflow performs the following steps:

1. A **Schedule Trigger** runs the workflow every few minutes.
2. An **HTTP Request node** fetches repository data from GitHub API.
3. A **transformation step** extracts important fields like:
   - repository name
   - star count
   - repository URL
4. An **IF condition** checks if the repository has more than 1000 stars or valid results exist.
5. If the condition is true, the workflow sends a **POST request to Webhook.site** with formatted JSON data.

---

## Data Transformation Logic

The transformation step reduces the API response to only required fields:

- full repository name
- number of stars
- repository URL
- timestamp of execution

This ensures only relevant data is passed forward and improves efficiency.

---

## Error Handling Behavior

- If the API request fails, the workflow does not crash.
- The IF condition ensures empty or invalid responses are ignored.
- Only valid API responses trigger the alert system.
- Webhook receives data only when conditions are satisfied.

---

## Conclusion

This project demonstrates API integration, data transformation, conditional logic, and external service communication using n8n automation.
