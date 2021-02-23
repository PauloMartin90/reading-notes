## Rest

- Our brains are somehow smart enough to know that the same verbs, like GET, can be applied to many different nouns. Some verbs are more specific than others and apply only to a small set of nouns. For instance, I can't drive a cup and I can't drink a car. But some verbs are almost universal like GET, PUT, and DELETE.

- So anyway, HTTP—this protocol Fielding and his friends created—is all about applying verbs to nouns. For instance, when you go to a web page, the browser does an HTTP GET on the URL you type in and back comes a web page. Web pages usually have images, right? Those are separate resources. The web page just specifies the URLs to the images and the browser goes and does more GETs using the HTTP protocol on them until all the resources are obtained and the web page is displayed. But the important thing here is that very different kinds of nouns can be treated the same. Whether the noun is an image, text, video, an mp3, a slideshow, whatever. I can GET all of those things the same way given a URL.

- Look, we've been talking about this with a lot of abstraction. How about we take a real example. Imagine you are a teacher - at school you probably have a big computer system, or three or four computer systems more likely, that would let you manage students: what classes they're in, what grades they're getting, emergency contacts, information about the books you teach out of, etc. If the systems are web-based, then there's probably a URL for each of the nouns involved here: student, teacher, class, book, room, etc. Right now, getting the URL through the browser gives you a web page. If there were a machine readable representation for each URL, then it would be trivial to latch new tools onto the system because all of that information would be consumable in a standard way. It would also make it quite a bit easier for each of the systems to talk to each other. Or, you could build a state or country-wide system that was able to talk to each of the individual school systems to collect testing scores. The possibilities are endless.

- Each of the systems would retrieve information from each other using a simple HTTP GET. If one system needs to add something to another system, it would use an HTTP POST. If a system wants to replace something in another system, it uses an HTTP PUT, or, to do a partial update, it'll hopefully use PATCH. The only thing left to figure out is what the data models should look like.

## Super Agent
SuperAgent is light-weight progressive ajax API crafted for flexibility, readability, and a low learning curve after being frustrated with many of the existing request APIs. It also works with Node.js!

```
request
   .post('/api/pet')
   .send({ name: 'Manny', species: 'cat' })
   .set('X-API-Key', 'foobar')
   .set('Accept', 'application/json')
   .then(res => {
      alert('yay got ' + JSON.stringify(res.body));
   });
```

### Retrying requests
When given the .retry() method, SuperAgent will automatically retry requests, if they fail in a way that is transient or could be due to a flaky Internet connection.

This method has two optional arguments: number of retries (default 1) and a callback. It calls callback(err, res) before each retry. The callback may return true/false to control whether the request should be retried (but the maximum number of retries is always applied).

```
 request
   .get('https://example.com/search')
   .retry(2) // or:
   .retry(2, callback)
   .then(finished);
   .catch(failed);
```

Use `.retry()` only with requests that are idempotent (i.e. multiple requests reaching the server won't cause undesirable side effects like duplicate purchases).

All request methods are tried by default (which means if you do not want POST requests to be retried, you will need to pass a custom retry callback).

By default the following status codes are retried:

- 408
- 413
- 429
- 500
- 502
- 503
- 504
- 521
- 522
- 524

By default the following error codes are retried:

- 'ETIMEDOUT'
- 'ECONNRESET'
- 'EADDRINUSE'
- 'ECONNREFUSED'
- 'EPIPE'
- 'ENOTFOUND'
- 'ENETUNREACH'
- 'EAI_AGAIN'

### Response properties
Many helpful flags and properties are set on the `Response` object, ranging from the response text, parsed response body, header fields, status flags and more.

#### Response text
The `res.text` property contains the unparsed response body string. This property is always present for the client API, and only when the mime type matches "text/", "/json", or "x-www-form-urlencoded" by default for node. The reasoning is to conserve memory, as buffering text of large bodies such as multipart files or images is extremely inefficient. To force buffering see the "Buffering responses" section.

#### Response body
Much like SuperAgent can auto-serialize request data, it can also automatically parse it. When a parser is defined for the Content-Type, it is parsed, which by default includes "application/json" and "application/x-www-form-urlencoded". The parsed object is then available via `res.body`.

#### Response header fields
The `res.header` contains an object of parsed header fields, lowercasing field names much like node does. For example `res.header['content-length']`.

#### Response Content-Type
The Content-Type response header is special-cased, providing `res.type`, which is void of the charset (if any). For example the Content-Type of "text/html; charset=utf8" will provide "text/html" as `res.type`, and the `res.charset` property would then contain "utf8".

#### Response status
The response status flags help determine if the request was a success, among other useful information, making SuperAgent ideal for interacting with RESTful web services. These flags are currently defined as:
```
 var type = status / 100 | 0;

 // status / class
 res.status = status;
 res.statusType = type;

 // basics
 res.info = 1 == type;
 res.ok = 2 == type;
 res.clientError = 4 == type;
 res.serverError = 5 == type;
 res.error = 4 == type || 5 == type;

 // sugar
 res.accepted = 202 == status;
 res.noContent = 204 == status || 1223 == status;
 res.badRequest = 400 == status;
 res.unauthorized = 401 == status;
 res.notAcceptable = 406 == status;
 res.notFound = 404 == status;
 res.forbidden = 403 == status;
```


### Resources
- [REST](https://gist.github.com/brookr/5977550)
- [Super Agent](https://visionmedia.github.io/superagent/)