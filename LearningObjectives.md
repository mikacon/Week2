I can explain the HTTP message format, including the common fields.


HTTP (Hypertext Transfer Protocol) messages are the basic connection between clinets and severs over the internet. There are 2 main times of HTTP messages: resquest messages and response messages.

HTTP Request Message

These messages have a varied number of lines depending on the information available. However the first line of a HTTP request message is always the request line. The request line has 3 parts.
1. The HTTP Method: It specifies the nature of the request. It can be something like GET, POST, DELETE, ....
2. The URL field: The URL that is being requested/accessed
3. HTTP Version field: The version of HTTP that is being used

The following lines are called header lines. There are full of information needed by web proxy caches and in general provides a greater description of the request. Some common header include:
1. Host: Provides the domain name of the server
2. User-Agent: Tells us what web client is requesting(Ex. Firefox)
3. Accept-Language: Tells us what version(langugae) the user wants to interact in
4. Connection: It tells the server if it should maintain a persistant connection with the host or not.

There is an option for a request body (optional). This is used primarily by POST and PUT requests and helps to send correct/more data to the server.

Response Messages

A response message is just a response to a HTTP request message. They also have a very similar stucture and contain the same 3 parts. The first line is called the Status Line. The Status line is the first line of the response.
1. HTTP Version: the version of HTTP being used
2. The status code: is a number repersentation of the Reason Phrase, basically repersenting the success of the connection
3. Success Phrase: Is an english description of the connection's success, (Ex. OK, Not Found).

Much like the HTTP request, the response message has Header Lines. Some common response headers are:
1. Server: The server software being used
2. Content type: The object type in the response body
3. Content Length: The number of bytes in th object being sent

The response message also has an body for the content that was requested by the host. Can be HTML or Images or ...


I can explain the difference between HTTP GET and POST requests and why you would use each.


HTTP GET is a commonly used HTTP method used to retrieve data from a server. It is used to read information of of a server and send that information back to the host through their connection. It cannot be used to modify data on the server side. This creates a "copy" of the data on your own machine and gives you the ability to change/edit on the client side without effecting it on the server side. Because the GET method gives you data visable within the URL, anyone can access this data as well by just using the same URL. This can be benifical by providing an easy way to share data, but also  potential security drawback because it is relatively easy to find the data that you requested. Because it only creates a "read only" copy of the data requested, a HTTP GET request can be done multiple times with the same result. 

HTTP POST is another commonly used HTTP method. Instead of retreiving data from a server, it instead submits a request for some data to be manipulated on the server side. Because it is manipuated on the server side, it is primarily used to modify existing server data, create new data, or have other effects on server data. Unlike the GET method, the POST method data is not visable in the URL making it less available for sharing, but safer to use confidentially. Also unlike the GET method, multiple POST requests will most likely result in differnt results. This is because each POST method can change the outcome of the next because POST methods chnage data server side. 

In all, GET and POST serve vastly different functions. GET is used to harmlessly get a "read only" copy of data from a server with minimal effects on the data within the server itself. The data from the GET method can be easily shared because it is visable within the URL, however it has poor confidentiality. It can be called multiple times without having any variation of results. POST is used to modify data residing within the server itself. The data is concealed from the URL so confidentiality is greater. And if a POST request is sent multiple times, it does not nessisarly have the same result due to previous changes done by POST methods.


I can explain what CONDITIONAL GET requests are, what they look like, and what problem they solve.


Conditional GET requests are HTTP requests made by a client to the server with specific conditions that have to be met before sending the requested resource back. They are typically used when requesting files that could be time dependant such as files or web pages. They look very similar to regular GET requests except they have special headers that include the specific conditions that must be met. Some of these are: if-modified-since, if-match, if-unmodified-since, .... Only if these conditions are met, then the server will send the desired resource back to the client. Conditional GET requests solve the problem of wasting banwidth and user-preceived response time (especially when the file/resource is large) based on the fact that they don't send data if it doesn't meet the specific conditions that are set. When accessing web pages, conditional GET requests dramatically speed up the loading process. Browsers can use the available cache resources and only request new data when something has been changed.


I can explain what an HTTP response code is, how they are used, and I can list common codes and their meanings.


HTTP response codes are 3 digit numerical codes that indicate the degree of success of a client's request. These codes are used to communicate between the server and client. If the server wants to tell the client that their request has been successful, there is a code for that. Likewise, if the server wants to tell the client that the request has been unsessesful, there is another code for that. Because specific codes mean different specific things, we can use the response codes for error handling. Error codes in the 300's usally have something for the client to attempt to solve the problem. The server can use specific codes to tell the clients to redirect to a different link, for example.

Some common response codes:
200, Ok
201, Created
301, Moved Permanently
400, Bad request
404, Not Found
503 Service Unavailable

It appears as though the higher the response code, the more unsuccessful the client's request was.


I can explain what cookies are used for and how they are implemented.


Cookies are small pieces of data that websites store on the user's web browser. Cookies impact how we search and daily life much more than we think. Small things like browser bookmarks or a personalized color are made availible through the use of cookies. Larger things such as personalized ads, browser prefrences, and authenication during the same session are made possible through cookies as well. Cookies are created by web servers using set-cookies headers on their requests. They have their own expiry dates that can range from when the browser closes to a set time and date in the future. They are usally accessed through javascript by web servers using the document.cookie API and also from HTTP request headers. Many cookies cannot be accessed by a different domain, except third-party cookies which are used mostly by advertizing and cross-site tracking.


I can explain the significance of HTTP pipelining.


HTTP pipelining is a technique that optimizes HTTP requests by allowing multiple HTTP requests to be send along a single connection at the same time. These requests can be executed together which saves time and resources when compared to HTTP 1.0 when a new connection when opened for ever HTTP request. Opening a new connection for every request creates a large latency overhead which negatively affects the functionality of the client's machine. HTTP piplining speeds this process up immensely, as we no longer have to either deal with the large latency of openning new connections with every HTTP request or exceedingly slow speeds if we wait for every HTTP request to finish before staring a new one on a single connection. HTTP pipelining on HTTP1.1 revolutionized this process of request optimization.


I can explain the significance of CDNs, and how they work.


CDNs, or Content Delievery Networks, enhance the performance, reliability and security of web content. They create copies of website content, particularly those that recieve the most internet traffic and store them on numerous servers worldwide located on the internet's edge. They then uses these copies as a cache and are able to send the data stored here with to clients reducing latency, internet core traffic and with a layer of security. Because CDNs create a copy of certain web resources, they are able to overlap and provide reduncency which reduces the efficiency of DDOS attacks and malicious attackers. They distribute the load from orgin servers to they CDN servers worldwide which reduces service distuptions< or overloading of a single server in particular.