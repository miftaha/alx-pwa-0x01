# alx-project-0x14

API Explorer: Mastering RESTful Connections

## API overview:

The MoviesDatabase API provides real-time data on movies, TV shows, and celebrities, including detailed data, cast information, genres, ratings, reviews, images, and trailers, with flexible search.

## API Version:

version 3

### key feature of version 3

- Real time data and updates
- Flexible search options
- Detailed Content Information on movies,tv show and celebrities

## Available Endpoints:

- **/search/movie**: Search for movies by title or keywords.
- **/search/tv**: Search for TV shows by title or keywords
- **/movie/{movie_id}**: Retrieve detailed information about a specific movie.
- **/tv/{tv_id}**: Get detailed information about a specific TV show, including seasons and episodes.
- **/person/{person_id}**: Access detailed information about a specific person.
- **/genre/movie/list**: Retrieve the list of movie genres available in the database.
- **/genre/tv/list**: Get the list of TV show genres available.
- **/discover/movie**: Find movies based on criteria like genres, release dates, or ratings.
- **/discover/tv**: Discover TV shows with filters for genres, air dates, and popularity.

## Request and Response Format

### Request Format

Requests to the API are typically made using HTTPS and include the following components:

- **Base URL**: `https://api.themoviesdatabase.org/v3`
- **Authentication**: An API key passed as a query parameter or in the request headers (e.g., `api_key=YOUR_API_KEY`).
- **HTTP Methods**: Common methods include `GET` for retrieving data.
- **Parameters**: Query parameters for filtering and customizing responses (e.g., `language=en-US` or `sort_by=popularity.desc`).

**Example Request**:

```
GET /search/movie?api_key=YOUR_API_KEY&query=Inception&language=en-US
Host: api.themoviesdatabase.org
```

### Response Format

Responses are returned in JSON format and include:

- **Status Codes**: HTTP status codes indicating success (e.g., `200 OK`) or errors (e.g., `401 Unauthorized`).
- **Data Structure**: Organized as key-value pairs with hierarchical data.

**Example Response**:

```json
{
  "page": 1,
  "results": [
    {
      "id": 27205,
      "title": "Inception",
      "overview": "A thief who steals corporate secrets through the use of dream-sharing technology...",
      "release_date": "2010-07-16",
      "vote_average": 8.8,
      "poster_path": "/qmDpIHrmpJINaRKAfWQfftjCdyi.jpg"
    }
  ],
  "total_pages": 1,
  "total_results": 1
}
```

## Authentication

To authenticate your requests to the MoviesDatabase API, you need to include an API key. This can be done in one of the following ways:

### Query Parameter

Include the API key as a query parameter in the request URL:

```
GET /search/movie?api_key=YOUR_API_KEY&query=Inception
```

### Request Headers

Alternatively, you can pass the API key in the request headers:

```
Authorization: Bearer YOUR_API_KEY
```

## Error Handling

The MoviesDatabase API uses standard HTTP status codes to indicate success or failure of requests. Below are common error responses and how to handle them:

### Common Error Responses

- **400 Bad Request**: The request was invalid or cannot be served. This may occur due to malformed syntax or missing required parameters.
  **Example Response**:

  ```json
  {
    "status_code": 400,
    "status_message": "Invalid request. Please check your query parameters.",
    "success": false
  }
  ```

  **How to Handle**: Verify the request parameters and ensure all required fields are included.

- **401 Unauthorized**: Authentication failed due to an invalid or missing API key.
  **Example Response**:

  ```json
  {
    "status_code": 401,
    "status_message": "Invalid API key: You must be granted a valid key.",
    "success": false
  }
  ```

  **How to Handle**: Check the API key for correctness and ensure it is included in the request.

- **403 Forbidden**: The API key does not have sufficient permissions to access the resource.
  **Example Response**:

  ```json
  {
    "status_code": 403,
    "status_message": "You do not have access to this resource.",
    "success": false
  }
  ```

- **404 Not Found**: The requested resource could not be found.
  **Example Response**:

  ```json
  {
    "status_code": 404,
    "status_message": "The resource you requested could not be found.",
    "success": false
  }
  ```

  **How to Handle**: Confirm the resource ID or endpoint URL.

- **500 Internal Server Error**: An unexpected error occurred on the server.
  **Example Response**:
  ```json
  {
    "status_code": 500,
    "status_message": "An error occurred. Please try again later.",
    "success": false
  }
  ```
  **How to Handle**: Retry the request after some time or contact support if the issue persists.

## Usage Limits and Best Practices

### Usage Limits

- **Rate Limits**: The API enforces rate limits to ensure fair usage and prevent abuse. Typical limits include a maximum number of requests per second or day.
- **Quota**: Each API key is assigned a usage quota, which resets periodically (e.g., daily or monthly).

### Best Practices

- **Efficient Querying**: Optimize your requests by using appropriate filters and parameters to fetch only the necessary data.
- **Caching**: Cache frequently accessed data to minimize redundant API calls and improve performance.
- **Retry Logic**: Implement retries with exponential backoff for transient errors (e.g., 500 Internal Server Error).
- **Error Logging**: Log errors and monitor usage patterns to identify and resolve issues promptly.
- **Secure API Key Management**: Keep your API key confidential and avoid exposing it in public repositories or client-side code.
- **Stay Updated**: Regularly review the API documentation for changes or new features to ensure compatibility and take advantage of improvements.
