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

	To fetch data from network, following are the steps::
	  1. Create a NSURL object 
	  2. Create a NSURLSession object (shared or private) and call its relevant method (with a completion handler) to perform the network request. e.g: dataTaskWithURL 
	  3. In the method's closure, we write the block where we grab the NSData object by checking the NSError status(if nil, data is available). 
	  4. But in order to start this network request, we need to resume the task. 
	  5. To update the UI inside the completion handler of a network task, do not forget to use performUIUpdatesOnMain()
	  6. In order to enable the HTTP requests, edit the settings in the info.plist. Add a string 'App Transport Security Settings' and Set the boolean value to YES for the key 'Allow Arbitrary Loads'.


*****************SECTION 2: Using web services and APIs******************

In order to build the URL from method parameters:
	* Build a Constants dictionary where entire URL is broken into various parts with its relevant values:
		- APIScheme(protocol), 
		- APIHost(e.g: www.flickr.com),
		- APIpath(e.g: services/rest),
		- The query parameters with a combination of key=value 
	* Create a NSQueryItem[] to append the query items from the entire query string
	* Use NSURLComponents to build entire url and parse it and return as NSURL object
	* NSURLRequest — represents a configurable URL that can specify properties such as the HTTP method type. Built on top of it is NSMutableURLRequest to modify the http method for the request specified. Use this class to create a request object and pass it as a parameter in the method dataTaskWithRequest(instead of dataTaskWithURL). 
	
