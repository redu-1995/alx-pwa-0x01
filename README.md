## API overview
The **MoviesDatabase API** provides a collection of information for movies, tv-show, actors, youtube trailer url, awards, full biography, and many other usefull informations.
   Features 
 -Searching movies, TV shows, or people by name.
- Retrieving detailed information about a specific title or person.
- Accessing trending or popular movie/TV data.
- Fetching movie posters and other media assets.

   ##API Version:
  **API Version**: v1

 ## Available Endpoints

1. `/titles/search/keyword/{keyword}` – Returns an array of titles based on keyword and query parameters.
2. `/titles/search/title/{title}` – Returns an array of titles by title and filters.
3. `/actors/{id}` – Returns detailed info about an actor.
4. `/title/utils/titleType` – Returns available title types.


  ## Request and Response Format
  
### Request Example

```js
const url = 'https://moviesdatabase.p.rapidapi.com/titles/search/title/{title}?exact=true&titleType=movie';
const options = {
  method: 'GET',
  headers: {
    'x-rapidapi-key': 'YOUR_API_KEY',
    'x-rapidapi-host': 'moviesdatabase.p.rapidapi.com'
  }
};

try {
  const response = await fetch(url, options);
  const result = await response.json();
  console.log(result);
} catch (error) {
  console.error(error);
}

 ### Response example

{
  "results": [
    {
      "id": "tt0848228",
      "titleText": { "text": "The Avengers" },
      "releaseYear": { "year": 2012 },
      "primaryImage": {
        "url": "https://m.media-amazon.com/..."
      },
      ...
    }
  ],
  "page": 1,
  "next": "/titles/search/title/{title}?page=2"
}


 ## Authentication

The API requires authentication via RapidAPI headers:

X-RapidAPI-Key: Your personal API key from RapidAPI.

X-RapidAPI-Host: Always set to moviesdatabase.p.rapidapi.com.

Without these headers, your request will be denied with a 401 Unauthorized error.

  ## Error Handling

| Status Code | Meaning           | How to Handle                                     |
| ----------- | ----------------- | ------------------------------------------------- |
| `400`       | Bad Request       | Ensure query parameters are correct.              |
| `401`       | Unauthorized      | Check your API key and headers.                   |
| `404`       | Not Found         | Endpoint or resource doesn’t exist.               |
| `429`       | Too Many Requests | You've hit the rate limit; wait and retry.        |
| `500`       | Server Error      | Retry after a short delay or contact API support. |

## Usage Limits and Best Practices

Rate Limit: Typically 500 requests/month for free tier (check RapidAPI dashboard for actual limits).

Use caching strategies for repeat requests to reduce API calls.

Always handle errors gracefully.

Avoid hardcoding your API key – use environment variables.

Log important errors to help with debugging.



