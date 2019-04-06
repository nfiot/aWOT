<h3 id='app.header'>void header(const char* name, char* buffer, int bufferLength);</h3>

When request gets to the first middleware all headers have been already processed. To make header lookup available inside a Middleware with the Request::get method we need to specify the headers we are interested in advance. 

The header name matching is case-insensitive and the buffer needs to have space for null termination. If the header value does not fit the buffer the server will automatically send a `431 Request Header Fields Too Large` response.

##### Example
```arduino
char contentType[100];

void headers(Request &req, Response &res) {
  char * type = req.get("Content-Type");
}

app.header("Content-Type", contentType, 100);
app.use(&headers);
```