## Unit 14 Homework: Web Development

### Instructions

In this homework, we will review the many of the concepts and tools covered in the web development unit. If needed, refer to the [HTTP](./HTTP_Reference.md) and [curl](./cURL_Reference.md) reference sheets provided to you.

For submission, create a new file containing the answers to the question.

#### HTTP Requests and Responses

Answer the following questions about the HTTP request and response process.

1. What type of architecture does the HTTP request and response process occur in?

    HTTP request and response occurs in the Client-Server Architecture. 

2. What parts make up an `HTTP request`?

    An HTTP request anatomy:

    - A request line contains the request method, the name of the requested resource, and the version of the HTTP in use. 

    - Headers contain additional detials about the requested resource. They are used to implement many actions with security implications, such as authentication and remembering user resources.


3. What is the optional part of an HTTP request?

    The request line also contain query parameters, which the client can use to send data to the server. This is an optional chunk of data. 

4. What three parts make up an HTTP response?

    Anatomy of the HTTP Response:
    
    - A status line contains the response status code and translation, such as "OK" or "Conflict"

    - Headers contain additional information about the reponse, similar to response headers.

    - A response body contains the resource requested by the client, all of the web code and styling that your 
      browser uses to  format the page. 

5. Which number class of status codes represent errors?

    400 Codes represent 'client errors'.

6. What are the two most common request methods that a security professional will come across?

    GET request
    POST request

7. Which type of HTTP request method is used for sending data?

    The PUT request is similar to POST, in that it sends information to a server.

8. Which part of an `HTTP request` contains the data being sent to the server?

    The "Cookie" contains stored HTTP cokkies previously sent by the server with the Set-Cookie response header.

9. In which part of an HTTP response would the browser receive the web code to generate and style a web page?

    Th Response Body 

    

#### Using cURL

Answer the following questions about `curl`:

10. What are the advantages of using curl over the browser?

    cURL is a tool to transfer data from or to a server, using one of the supported protocols without user interaction.


11. Which curl option is used to change the request method?

    -X option specifies that we are changing the request method.

12. Which curl option is used to set request headers?

    # Setting a request type and URL
     curl --request GET --url example.com

     This explicitly sets a request type and URL with the --request and --url options

13. Which curl option is used to view the response header?

    # View the response headers
     curl -I example.com

     This uses the -I  flag to view the response headers only.


14. Which request method might an attacker use to scope out usable HTTP requests that an HTTP server will accept?

# Send a GET request with parameters and show both request and response headers
curl -v --request https://example.com/get?name=rodric&location=atlanta

This sends a GET request to the /get endpoint with the following parameters: name, location but also prints out both request and response headers


-v: Show more detailed info like both request and response header.

--request: set the request type

name: your name

location: your current city




#### Sessions and Cookies

Recall that HTTP servers need ways to recognize clients from one another. These are implemented through sessions and cookies.

Answer the following questions about sessions and cookies.

15. Which response header sends a cookie to the client?

    ```HTTP
    HTTP/1.1 200 OK
    Content-type: text/html
    Set-Cookie: cart=Bob
    ```

    This section: 'Content-type: text/html'

16. Which request header sets a cookie in the client?

    ```HTTP
    GET /cart HTTP/1.1
    Host: www.example.org
    Cookie: cart=Bob
    ```

    This section: 'Cookie: cart=Bob'

#### Example HTTP Requests and Responses

Look through the following example HTTP request and response and answer the following questions.

#### HTTP Request Example

```HTTP
POST /login.php HTTP/1.1
Host: example.com
Accept-Encoding: gzip, deflate, br
Connection: keep-alive
Content-Type: application/x-www-form-urlencoded
Content-Length: 34
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Linux; Android 6.0; Nexus 5 Build/MRA58N) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/80.0.3987.132 Mobile Safari/537.36

username=Barbara&password=password
```

17. What was the request method?

    POST Request.

18. Was the request encrypted or unencrypted?

    The request was "Unencrypted". 

19. Does the request have a user session associated to it?

    Yes.

20. What kind of data is being sent from this request body.

    Request body contains login credentials.

#### HTTP Response Example

```HTTP
HTTP/1.1 200 OK
Date: Mon, 16 Mar 2020 17:05:43 GMT
Last-Modified: Sat, 01 Feb 2020 00:00:00 GMT
Content-Encoding: gzip
Expires: Fri, 01 May 2020 00:00:00 GMT
Server: Apache
Set-Cookie: SessionID=5
Content-Type: text/html; charset=UTF-8
Strict-Transport-Security: max-age=31536000; includeSubDomains
X-Content-Type: NoSniff
X-Frame-Options: DENY
X-XSS-Protection: 1; mode=block

[page content]
```

21. What was the response status code?

    The response was accepted.

22. Was the response encrypted or unencrypted?

    The response was encrypted.

23. Does this response have a user session associated to it?

    No.

24. What kind of content is likely to be in the [page content] response body?

    Date: Contains a timestamp of when the response was generated.
    Server: Apache - Indicates the server is running Apache
    Set-Cookie: SessionID=5 Tells the client to create a cookie called SESSID with a value
    of 5.
        X-Content-Type: NoSniff header is used to protect against MIME

    X-Frame-Options: DENY forbids a page from being displayed in a frame.
    X-XSS-Protection: 1; mode=block Enables XSS filtering. Rather than sanitizing the page, the
    browser will prevent rendering of the page if an attack is detected


25. If your class covered security headers, what security request headers have been included?

    The class has covered impotant information on Microservices and Monoliths.

#### Monoliths and Microservices

Answer the following questions about monoliths and microservices:

26. What are the individual components of microservices called?

    Clients - Identity Providers - API Gateway - Messaging - Formats - Databases - Static

27. What is a service that writes to a database and communicates to other services?

    MySQL database: known to write a service to database of customers, and their information and purchases.

28. What type of underlying technology allows for `microservices` to become scalable and have redundancy?

    Container Vulnerability Filtering

#### Container Vulnerability Filtering

Answer the following questions about vulnerability filtering `Trivy` scans with `jq`:

29. Do `microservices` share the same kind of vulnerabilities as regular operating systems?

    Microservices require lightweight environments to run on because:

    Live services need to be deployed quickly.
    Multiple copies of a service can be replicated as needed to meet demand.
    Developers and maintainers can deploy their own copies of these services locally for their own testing purposes.
    Full-sized VMs for each service requires more resources and costs more.

30. Would an organization be more concerned with `Low` severity vulnerabilities as much as `Critical`?

    The vulnerability would be same. Using Trivy is simple, but the most important part is filtering through the results for the most critical security risks.


31. Would the bash tool `jq` be useful in finding certain kinds of vulnerabilities within a vulnerability report?

    jq is like sed, but for JSON data. It is used to filter through JSON files and has the same text editing functionalities that are built into sed, awk, and grep. A security engineer will often have to filter through JSON logs in order to find the most relevant information for an organization.

#### Deploying and Testing a Container Set

Answer the following questions about multi-container deployment:

32. What is a tool that can be used to deploy multiple containers at once?

Docker

33. What kind of file format was required for us to deploy a container set?

docker-compose.yml file format 

#### Container Runtime Intrusion Detection Systems

34. What is a tool used to actively detects intrusion behavior within containers?

    Falco is an open-source CIDS that alerts security professionals of potential intrusion attempts, much like a normal network intrusion detection system.


35. What high-value system file might an intruder view that would trigger a `sensitive file opening` alert?

    When sensitive files, such as /etc/shadow, are read. At no point during a container deployment should the contents of /etc/shadow be read. This is a clear sign that an attacker is retrieving the hashed passwords of accounts within the system.

36. What kind of intruder action might trigger an alert from a container IDS that says `shell configuration file has been modified`?

    File creations at /root or /. At no point during a container's runtime should new files be created in the / or /root directories. Files created in these directories indicate compromise.

---

© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.

