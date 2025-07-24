
# web services

* it is not a service delivered over the web.
* it is a system software designed to support interoperable machine-to-machine
  interaction over a network.
* a web service must be consumable by other applications.
* the web layer of a web application cannot be consumed by other apps and hence
  it is not a web service.
* packaging business and data layer into a jar file also does not help as it
  needs to be constantly regenerated if there are any changes to the code. Also,
  it is platform dependent (cannot be used by Python, JS apps).
  

* A web service must:
    * support machine-to-machine interaction
    * be interoperable (platform independent)
    * allow communication over a network.
    

* Making a webservice platform indpendent requires communication to be platform
  independent.
* Communication -> Requests and Responses
* Input to a webservice is a Request and output from a webservice is
  a Response.
* 2 common platform independent communication formats are JSON and XML

```
Consumer -----------------------------------> Web Service
         input: JSON/XML (Request)

         <-----------------------------------
         output: JSON/XML (Response)
```

* Web Service Provider (Server) -> Entity that provides the web service.
* Web Service Consumer -> Entity that consumes a web service.


## Web Service Categories
* SOAP Web Services
    * Request and Response message format is SOAP-XML, a specific type of XML.

* REST/RESTful Web Services or REST API
    * Built on top of HTTP. Uses HTTP methods (GET, POST, etc) for operations.

