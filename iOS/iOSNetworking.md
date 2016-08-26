#iOS Networking with Swift

This referencer logs all my learnings of iOS Networking with Swift. 

Course referred: Udacity iOS Nanodegree https://www.udacity.com/course/ios-developer-nanodegree--nd003

This course is divided into various sections. 

*****************SECTION 1: Making a network request*****************

* NSURL => An object that contains a URL.
* NSURLSession => Creates a session (private or shared) object that coordinates a group of data transfer related tasks. Network requests are referred as tasks by this class. So, any task used by NSURLSession is a subclass of NSURLSessionTask
* NSURLSessionTask => handles following tasks:
	1. NSURLSessionDataTask => returns data from network directly into memory as NSObjects
	2. NSURLSessionDownloadTask => returns data from network into a temporary file to work with
	3. NSURLSessionUploadTask => Uploads content

* To fetch data from network, following are the steps::
	1. Create a NSURL object 
	2. Create a NSURLSession object (shared or private) and call its relevant method (with a completion handler) to perform the network request. e.g: dataTaskWithURL 
	3. In the method's closure, we write the block where we grab the NSData object by checking the NSError status(if nil, data is available). 
    4. But in order to start this network request, we need to resume the task. 
	5. To update the UI inside the completion handler of a network task, do not forget to use performUIUpdatesOnMain()
	6. In order to enable the HTTP requests, edit the settings in the info.plist. Add a string 'App Transport Security Settings' and Set the boolean value to YES for the key 'Allow Arbitrary Loads'.


*****************SECTION 2: Using web services and APIs******************

To build the URL from method parameters, make a request and get the response:

This above process consists of 3 phases majorly:

1. Building a URL from scratch 
2. Making a request
3. Getting the response

---------------------------------------------------
Build a Constants dictionary where entire URL is broken into various parts:
	* Parameter Keys 
	* Parameter Values
	* Response Keys
	* Response Values

1. The type of this dictionary is: [String: AnyObject]
2. Pass this dictionary as a method parameter to the function that converts the characters into ASCII safe 
3. The string value can be made ASCII safe using the method: 'stringByAddingPercentEncodingWithAllowedCharacters'

---------------------------------------------------
Making a request:
* Create a NSURLRequest object with NSURL string. With this request object, we can call the API with any of the HTTP methods like: GET, POST, PUT, DELETE, etc.
	1. NSMutableURLRequest helps to modify the http method for specified request.
* Create a NSURLSession object (shared or private) and call its relevant method (with a completion handler) to perform the network request. e.g: dataTaskWithRequest

---------------------------------------------------
Get the response:
* Get the result/data in its raw JSON format. 
* Parse this data into a Foundational object such as NSDictionary or NSArray
* Grab the data from this foundational object.





	
