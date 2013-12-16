ProofHub API
====================
This RESTful API is an interface to the resources in ProofHub e.g. projects, discussions, to-dos, people etc. 

If you are new to REST, you can understand the basics at http://en.wikipedia.org/wiki/REST. This API accepts and returns JSON format.

API key
----------------
With every request you'll need to pass the ProofHub account's API key. The key can be generated from the ProofHub Settings tab.

Making a request
----------------
All URLs (Base url) start with `https://api.proofhub.com/v1/` (No HTTP, only HTTPS). You'll also need to include the `Content-Type` header and `User-Agent` to infentify your app with every request.

**Here is a curl based example:**

```shell
curl -H 'X-API-KEY: YOUR API KEY' -H 'User-Agent: AppName (name@example.com)' https://api.proofhub.com/v1/projects.json
```

API endpoints
----------------

* [Projects](https://github.com/sdplabs/proofhub-api/blob/master/sections/projects.md)
* [People](https://github.com/sdplabs/proofhub-api/blob/master/sections/people.md)


Things to remember
----------------
* **JSON Format**

  We support JSON for receiving and sending the data. You must include `Content-Type: application/json; charset=utf-8` header with every POST and PUT request. Requests with invalid formats will be returned with `000` response. 

* **Identify your app**

  You must include the `User-Agent: AppName (name@example.com)` header with every request. If this header is not supplied, request will be returned with `400` response. 

* **Rate Limits**

  API calls are subject to rate limiting. Exceeding any rate limits will result in requests returning a status code of 429 (Too Many Requests). Rate limits are 100 requests per 10 second for the same account from the same IP.

* **Handling errors**

  Error codes 500 Internal Server Error, 502 Bad Gateway, 503 Service Unavailable, or 504 Gateway Timeout means an has occured at our end. Re-trying in some time should solve the problem.
  
