Minimal example to reproduce an issue, which is that there is a Content-Security-Policy violation on inline styles, even though there are no inline styles.

There is an Elm web app served up by a Go server.

# To reproduce the issue

+ Install Go
+ Install Elm 0.19
+ Clone this repository and cd into it
+ Build the Elm code with: ```elm make Main.elm --output=main.js```
+ Set the $GOPATH to the 'go' directory in this repository: ```export $GOPATH `pwd`/go```
+ Install the Go http library: ```go get net/http```
+ Build the Go server with: ```go install server```
+ Start the server with: ```go/bin/server```
+ Visit http://localhost:3333 in a web browser
+ The server prints out this:
```
{"csp-report":{"blocked-uri":"inline","column-number":1,"document-uri":"http://localhost:3333/","line-number":1,"original-policy":"style-src 'self'; report-uri http://localhost:3333/cspreport","referrer":"","source-file":"http://localhost:3333/","violated-directive":"style-src"}}
{"csp-report":{"blocked-uri":"inline","column-number":1,"document-uri":"http://localhost:3333/","line-number":1,"original-policy":"style-src 'self'; report-uri http://localhost:3333/cspreport","referrer":"","source-file":"http://localhost:3333/","violated-directive":"style-src"}}
```
