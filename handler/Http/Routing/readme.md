####Routing
Currently supported options.

+ Match the URL path via REQUEST_URI, obviously.
+ REQUEST_METHOD [GET,POST,PUT]options
+ HTTP_X_REQUESTED_WITH (Ajax request) option.

#### Why is this router and not already an existing one?
+ This router uses an hash key to match a route.  
The hash is the index of a plain PHP array.  
With this it is significant faster than most routes provided by frameworks.

+ Direct forwarding to a file.  
Front-end development becomes easier without overhead from back-end.  



#### Type of routes
+ Forward route    
Directly the defined filename as destination opened.    
Fits better Front-end web/http development.   
 ```$route``` array with ```indexKey``` will be available. 

+ Regular route
Route instantiates a controller.  
Fits better Back-end web/http development.
 ```Http\Stream\InptHandler()``` will be available.


#### Adding route by example
1. With the following snippet, generate a route.

```
$routeContext = new Http\Routing\RouteContext('GET', '/', '../web/home.php');
```

```
$routeContext = new Http\Routing\RouteContext('POST', '/', 'RootPath@post');
```

```
$routeContext = new Http\Routing\RouteContext('GET', '/test', 'Test@getXhr');
$routeContext->setXRequestedWith(true);
```
```
$routeContext = new Http\Routing\RouteContext('POST', '/admin', 'Admin@postXhr');
$routeContext->setXRequestedWith(true);
```

View the result like this
```
var_export($routeContext->buildRoute());
```

2. Copy and Paste the result into RoutesCollection.php  
   2a. pasted result will not have index key, type '' => before the array() 
   and fill the '' with indexKey
   
Now it can be tested via the webserver. 
Accessing via the browser is most convenient way.



    

