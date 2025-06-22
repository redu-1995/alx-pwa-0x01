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
  1,/titles/search/keyword/{keyword} ---- returns array of titles according to filters / sorting query parameters provided and the keyword provided in path.
  2,/titles/search/title/{title} ------returns array of titles according to filters / sorting query parameters provided and the title provided in path.
  3, /actors/{id} ----- returs array of title types
  4, /title/utils/titleType -----returs array of title types

  ## Request and Response Format
  To search for a title:

```http
const url = 'https://moviesdatabase.p.rapidapi.com/titles/search/title/%7Btitle%7D?exact=true&titleType=movie';
const options = {
	method: 'GET',
	headers: {
		'x-rapidapi-key': 'b3e51a2006msh2ee698ac725e36bp18b62fjsn02a758d172ee',
		'x-rapidapi-host': 'moviesdatabase.p.rapidapi.com'
	}
};

try {
	const response = await fetch(url, options);
	const result = await response.text();
	console.log(result);
} catch (error) {
	console.error(error);
}
  Response example

{
  "results": [
    {
      "id": "tt0848228",
      "titleText": {
        "text": "The Avengers"
      },
      "originalTitleText": {
        "text": "The Avengers"
      },
      "releaseYear": {
        "year": 2012
      },
      "primaryImage": {
        "url": "https://m.media-amazon.com/images/M/MV5BMjAxNjYxMzY4MF5BMl5BanBnXkFtZTcwODc2NjY0Nw@@._V1_.jpg"
      },
      "releaseDate": {
        "day": 4,
        "month": 5,
        "year": 2012
      },
      "titleType": {
        "text": "movie",
        "id": "movie"
      }
    }
  ],
  "page": 1,
  "next": "/titles/search/title/{title}?exact=true&page=2&titleType=movie"
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



