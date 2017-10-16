## Intermediate Javascript I 

* Debugging Javascript
	* Common JavaScript Errors
		* ReferenceError - occurs when we try to access a variable that does not exist in scope. 
		* TypeError - occurs when you make incorrect use of certain types in javascript. 
		* RangeError - occurs when we have a function that calls itself (also known as a recursive function). If we have too many functions that have been called (before they are returned) we run out of memmory and cause a RangeError. 
* Catching and Throwing Errors in Javascript
	*  Try / Catch Statement 
		* We place code inside of the try block (a block is defined as code inside of a {}) and if an error is thrown, the code moves to the catch block. 
	* In our try/catch statements, we can add one more special keyword called finally. Inside of the finally block, code will execute regardless of an error being thrown. 
	
	``` 
	try {
	    // let's randomly try to throw an error
	    if(Math.random() >= .5){
	        // The following code will throw:
	        // Uncaught TypeError: undefined is not a function(…)
	        undefined();
	    }
	    console.log("Whew, we made it");
	} catch(e){
	   console.log("We didn't make it. The error message is", e.message);
	} finally {
	   console.log("No matter what we will see this statement");
	}
	```
* Nested Objects
	* Accessing and Setting values in nested objects 
	
	```
	var programmingLanguages = {
	    java: {
	        yearCreated: 1995,
	        creator: "James Gosling"
	    },
	    javaScript: {
	        yearCreated: 1995,
	        creator: "Brendan Eich"
	    }
	}

	function addProgrammingLanguage(nameOfLanguage, yearLanguageCreated, creatorOfLanguage){
	    // how can we access the programming languages object?
	    // We can't use dot notation, because we don't know the name of
	    // the key until the function is called.
	    // Instead we use bracket notation where the key is the
	    // nameOfLanguage that is being passed to the function.
	    programmingLanguages[nameOfLanguage] = {
	        // Creating the object which will be the value of the
	        // key.  We can directly assign the yearLanguageCreated
	        // and creatorOfLanguage to the appropriate keys here.
	        yearCreated: yearLanguageCreated,
	        creator: creatorOfLanguage
	    }
	}
	
	// Usage example: Adding a key of ruby to the programming language object,
	// with the value of 1995 for the key "yearCreated" and the value
	// "Yukihiro Matsumoto" for creatorOfLanguage
	addProgrammingLanguage("ruby", 1995, "Yukihiro Matsumoto");
    ```
* Nested Arrays
	* Multidimensional Arrays

	```var nestedArr = [[1,2], [3,4]];
	for(var i=0; i<nestedArr.length; i++){
	    for(var j=0; j<nestedArr[i].length; j++){
	        // notice that we are going inside the outer array
	        // and now inside of the inner array
	        console.log(nestedArr[i][j]);
	    }
	}
	
	// this will log out...
	// 1
	// 2
	// 3
	// 4
	```	
* Higher Order Functions 
	* Functions that accept functions as parameters are called "higher order functions". 
	* It is important to remember the difference between referencing a function here, and invoking a function. When you pass a function into a higher order, you must always pass in the function name, nit an invocation of the function. 
	
	```
	// sendMessage is a higher order function as it accepts a parameter called fn.
    // How do we know fn is a function? We can see the fn parameter is being invoked with ()
			function sendMessage(message, fn){
			    return fn(message);
			}
	```
* Anonymous Functions As Parameters

	```
	sendMessage("Hello World", function(message){
   		// message refers to the string "Hello World"
   		console.log(message + " from a callback function!");
	});  // Hello World from a callback function!
	```
		
	Is equivalent to: 
		
	```
	var myFunction = function(message){
	    // message refers to the string "Hello World"
	    console.log(message + " from a callback function!");
	};
	
	sendMessage("Hello World", myFunction);
	```
	* Instead of writing many different functions, we can just write one and pass another function to it! We call a function that is passed as an argument to a higher order function a **callback**. 
		
* Callback Functions
	* A callback function is the function that is being passed to a higher order function and the callback function will be invoked within the higher order function. 
	
		```
		function add(a,b){
		    return a+b;
		}
		
		function subtract(a,b){
		    return a-b;
		}
		
		function math(a,b,callback){
		    return callback(a,b);
		}
		
		math(1,4,add); // returns 5
		math(5,5,subtract); // returns 0
		
		/* 
		as we start making additional functions that perform operations on
		two numbers we can pass them to the math function. So if we make a
		divide or multiply function we can call all of them just using the
		math function.
		*/
		```	
* Timers 
	* setTimeout + setInterval 
		* It's quite common to write code that we want to be executed after a specfic amount of time. To do this, we use setTimeout and setInterval functions. Both functions accept a callback function and a time in milliseconds as parameters. 
		* The main difference is that the setTimeout function will only run the callback function to be executed once, whereas setInterval will run it an infinite amount of times(until the timer is cleared). 
		* If you want to stop the timer, setTimeout and setInterval return a special value called a timer id. If we pass this value into the clearTimeout or clearInterval method, we can stop our timer. 

* Asynchronous Code
	* Another reason why callbacks are such a powerful tool is that they enable us to manage asynchronous code, or code that will be executed at a later point.
	* JavaScript is **single threaded.** What this means is only one process will happen at a time. Unlike other languages where you can create your own threads, a process called multi-threading. 
	* We can write asynchronous code, which may give the *impression* that multiple things are happening at once, even though this is not the case. 
* How JS manages asynchronous code
	* call stack - where function calls are put (each one is called a "stack frame"). The call stack (sometimes simply referred to as the stack) is LIFO (last-in-first-out) data structure. Like a stack of cups (last one you put on the stack is the first one that comes off). What that means is that is there is a function on the stack and it's under another function, it can never execute until the function at the top has come off the stack (either by returning some value or by executing all the code in the function). 
	* event queue -  when an asynchronous event occurs, it gets put into what is called the "event queue". It is then moved to the stack  when the stack is clear (i.e. when there is no functions in the stack). The queue can also be described as a "list of messages to be processed". A function is associated with each message. 
	* heap - where objects are stored. The heap is an unstructed/unorganzied region of the memory. 

* Closures 
