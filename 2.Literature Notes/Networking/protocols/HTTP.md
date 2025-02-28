## Header Example

- Get Request is Idempotent (Executing it multiple times has no side effects)
```java
GET /index.html HTTP/1.1 //Method, Resource & Protocol Version
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.8; rv:20.0) Gecko/20100101 Firefox/20.0 //for Browser tailred Responses
Host: en.wikipedia.org 
Connection: keep-alive //Since HTTP1.1 to prevent opening a new Conn
Accept-Language: en-US,en;q=0.5 // q = relative quality factor
Accept-Encoding: gzip, deflate //Compression methods
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,* //Msg Types
// left intentionally Blank, The line that follows contains the Body
```

- Cookies => passed from server to client and back again in the HTTP headers of requests and responses. Cookies can be used by a server to indicate session IDs, shopping cart contents, login credentials, user preferences.
- Stateless Cookies => stored & encrypted on the Client Side instead.
```java
Set-Cookie: user=elharo;
Path=/restricted;
Domain=.example.com;
Max-Age=3600; //One Hour
secure; //Only send over HTTPs
httponly; //prevents XRSF Attacks (Javascript)
```
