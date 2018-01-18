# Introduction to XHR and AJAX
* XHR - this stands for **X**ML**H**ttp**R**equest, which is an API that allows for transferring data between client and server. This API is only available to scripting languages in the browser(JavaScript), so it can be used by server languages like Ruby, Python, Java etc. You use XHR object in Javascript to communicate with the server and send/retrieve data. 
	* It's important to understand that when XHR is used, the response from teh server can be receievd without refreshing the web page. 
* Asynchronous - When dealing with AJAX, you will be writing a lot of code that runs asynchronously. That means you can't guarantee taht you code will run line-by-line, when you make a request to another computer, you have no control over how long it will take to get a response back, in the meantime, your code will keep running. 
* XML - this stand for Extensible Markup language. In some ways XML looks similar to HTML, but XML is primarily used to store text data. While HTML has a small number of pre-defined tages, in XML you can create your own tags. 
* AJAX - this stands for Asynchronous Javascript and XML. It is a set of techonologies that allows for building a single page application (application that do not require full page refreshes to change data on the page). 
* AJAX without jQuery
	 * Using the XHR object 
	 	* The code starts by creating an object from the XMLHTTPRequest object. 