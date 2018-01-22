# Introduction to XHR and AJAX
* XHR - this stands for **X**ML**H**ttp**R**equest, which is an API that allows for transferring data between client and server. This API is only available to scripting languages in the browser(JavaScript), so it can be used by server languages like Ruby, Python, Java etc. You use XHR object in Javascript to communicate with the server and send/retrieve data. 
	* It's important to understand that when XHR is used, the response from teh server can be receievd without refreshing the web page. 
* Asynchronous - When dealing with AJAX, you will be writing a lot of code that runs asynchronously. That means you can't guarantee taht you code will run line-by-line, when you make a request to another computer, you have no control over how long it will take to get a response back, in the meantime, your code will keep running. 
* XML - this stand for Extensible Markup language. In some ways XML looks similar to HTML, but XML is primarily used to store text data. While HTML has a small number of pre-defined tages, in XML you can create your own tags. 
* AJAX - this stands for Asynchronous Javascript and XML. It is a set of techonologies that allows for building a single page application (application that do not require full page refreshes to change data on the page). 

## AJAX with jQuery 
* **$.ajax**
 * jQuery has one major function called $.ajax which can be configured to make all type of HTTP requests. The .ajax function accepts an object and returns a promise. Inside of the object, you must use the keys like method, url, etc. 

```
	$.ajax({
	    // what HTTP verb?
	    method: "GET",
	    // where are we making a request to?
	    url: "https://omdbapi.com",
	    // what should we add to the query string?
	    data: {
	        // a key of t and a value of titanic which will look like ?t=titanic
	        t: 'titanic'
	    },  
	    // this will add an HTTP request header of  'Accept': 'application/json'
	    dataType: "json"
	    // you can think of this ".then" like this: after we get the response, then what do we do? 
		}).then(function(response){
	    // let's see what the response is from the OMDB API!
	    console.log(response);
		}).catch(function(error){
	    // something went wrong :(
	    console.log(error);
		}) 
```

* **$.get**	
	* Same as .ajax but wothout the dataType:json. 

	```
	$.get("https://omdbapi.com?t=titanic").then(function(response){
    console.log(response);
});

* **$.getJSON**
	* Same as .ajax but wothout the dataType:json. 
	
	```
	$.getJSON("https://omdbapi.com?t=titanic").then(function(response){
	    console.log(response);
	});
	
	```
* **$.post**
	* If we want to make a POST request to a server (e.g. if we want to send data to it), we can either change the method with .ajax or use .post. The second parameter is the data we want to send to a server.

	```
	$.post("https://someapi.com", {name: "new user"}).then(function(response){
	    console.log(response);
	});
	```
 

	
