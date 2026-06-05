# API Documentation Writing Rules

When generating API documentation, always use a clean, consistent, and professional Markdown structure.

### Description

Start immediately with a short and clear description in professional English. Explain what the endpoint does, its main purpose, and when it should be used.

Do not display a heading named **Short Description**. Only write the description content directly under the main endpoint title or section.

### Method

Add a bold Markdown heading for the method section:

### Method

Write the HTTP method and endpoint path in inline code format, for example:

`POST /register`

### Request Body Parameters

Add a bold Markdown heading for the request body section:

### Request Body Parameters

List all request body parameters in a Markdown table with the following columns:

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|

Rules:
- Use `Yes` or `No` in the **Required** column.
- Write clear, precise, and useful descriptions for each parameter.
- Keep descriptions concise but informative.

After the table, include at least one complete and realistic JSON request example.
If the endpoint supports multiple use cases, include more than one JSON example when necessary.

Example:

```json
{
  "email": "john.doe@example.com",
  "password": "StrongP@ssw0rd123"
}
```

### Response Codes

Add a bold Markdown heading for the response section:

### Response Codes

List all possible HTTP response codes as bullet points.

Format each response like this:

- `200 OK` — Request completed successfully.
- `201 Created` — Resource created successfully.
- `400 Bad Request` — Request body is invalid or missing required fields.
- `401 Unauthorized` — Authentication is required or failed.
- `403 Forbidden` — The client does not have permission to perform this action.
- `404 Not Found` — The requested resource does not exist.
- `422 Unprocessable Entity` — Validation failed for one or more fields.
- `500 Internal Server Error` — An unexpected server error occurred.

### Schemas

For **every API endpoint**, always generate the following schemas:

#### StandardResponse

```json
{
  "status": 200,
  "message": "Request successfully",
  "data": {}
}
```

Explanation:
- `success` (boolean) — Indicates whether the request succeeded.
- `message` (string) — Human-readable message describing the result.
- `data` (object) — Response payload containing the actual data.

#### ErrorResponse

```json
{
  "status": 401,
  "message": "Missing or invalid authorization header",
  "error": {}
}
```

Explanation:
- `status` (number) — HTTP status code for the error.
- `message` (string) — Human-readable error message.
- `error` (object) — Error details.

These schemas must be generated for each documented API endpoint.

## Formatting Rules

- Use the same heading size and bold style for all main documentation sections.
- Use Markdown headings such as:
  - `### Method`
  - `### Request Body Parameters`
  - `### Response Codes`
  - `### Schemas`
- Keep the structure clean, readable, and consistent.
- Use professional English.
- Avoid redundancy and unnecessary explanations.
- Ensure all JSON examples are valid and realistic.
- Keep the documentation concise but complete.

## Exclusions

Do not generate the following items in the documentation:
- a visible **Short Description** heading
- **Capability** fields
- **Rate limit** fields
- `securitySchemes`

These items must not appear in the generated API documentation unless explicitly requested.

However, always **do generate** the following schemas for every API:
- `StandardResponse`
- `ErrorResponse`
