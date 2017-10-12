## Introduction

* ECMAScript vs Javascript
	* 	ECMAscript is a standard. Javascirpt is an implementation of that standard. The standard dictates certain features and sets of functionality, but there can be different implementations that follow the standard. 
* null vs undefined
	* *undefined* means a variable has been declared but has not been assigned a value
	* *null* is an assignment value and can be assigned to a variable as a repersentation of value. 
	* undefined is a type itself (undefined) while null is an object
	* One way to consider the notion of "undefined: in JavaScript is as a "higher level" null value
* == vs ===
	* Both operators check whether the two things being compared have the same values, but there's one important difference. == allows for coercion of the values, while === does not
* Ternary Operators
	* In general, a ternary operator has the form: 

		`expression ? pathIfTrue : pathIfFalse `
		
		equivalent to
			
		`if (expression) {
		    	pathIfTrue
		} else {
				pathIfFalse
		}`

* The splice method: Removing/Adding or both with splice
	* The splice menthod accepts at least two arguments. The first argument is starting index, indicating where values will be removed or added. The second parmameter is the number of values to remove. Optionally, you can pass in an unlimited number of additional arguements; these correspond to values you'd like to add to the array. 
* Array Methods
	* **Concat**
		* Concat joins two arrays together. In fact, you can pass multiple arrays into concat and it will still return a single array yo you. 
		* You don't even need to pass an array into concat! Any comma-seperated list of values can be concatentated with the orginal array. 

			```
			var moreOpeningWords = 
			openingWords.concat("dark","and","stormy","night");
			moreOpeningWords; // ["It", "was", "a", "dark", "and", "stormy", "night"]
			```
	* **lastIndexOf**
		* lastIndexOf works just like indexOf, but searching from the end of the array rather than the beginning
	* **Reference vs Value**
		* Javascript is *always* pass by value, but when a variable refers to an object(including arrays), the "value" is a reference to the object
		* Changing the value of a variable never changes the underlying primitive or obejct, it just points the variable to a new primitive or object 
		* However, changing a *property* of an object referenced by a variable does change the underlying object 

			```
			var instructor = "Elie";
			var anotherInstructor = instructor; 
			anotherInstructor // "Elie"
			
			// Let's assign a new value to anotherInstructor: 
			anotherInstructor = "Matt"; 
			
			instrcutor; // "Elie"
			anotherInstructor; "Matt"
			```
* Array Iteration 
	* while vs do...while
		* The main difference between while loop and do...while loop is that the code inside of a do...while loop is guaranteed to execute at least once. 
	* Using split to turn a string into an array 
		* If you pass a delimiter into the split method, the delimiting values will be removed from the array

			```
			var dashedString = "lots-of-dashes-here";
			var removedDashes = dashedString.split("-")
			removedDashes; // ["lots", "of", "dashes", "here"]
			var removedDashes = dashedString.split("-").join(" ")
			removedDashes; // ["lots of dashes here"]
			```
	* Mutability
		* Strings are immutable, as you cannot change the characters within them in the same way that you do with arrays. 
		* In fact, any operation which changes characters in a string actually produces a new string, rather than mutating the original string. 
* Objects
	* Bracket vs Dot Notation 
		* Use the bracket notation when you need to evaluate some expression or pass in a variable to get the name of the key and it is not a variable or expression, always use the dot notation. 
		* Every key in a JavaScript object is a string.
* Function 
	* Function Scope - The context in which values and expressions are 'visible' or can be referenced. There are only 2 kinds of scope: *global scope* and *function scope*. 
		* All variables that are defined outside of functions (and inside of functions without the var keyword) are declared in the global scope. 
		* All variables defined inside of functions can only be  accessed by those functions (and any inner functions)
		* Global scope is your best friend and your worst nightmare, learning to control your scopes is easy and in doing so, you'll run into no issues with global scope problems (usually namespace clashes)
	* Closures
		* Whenever you see a function within another function, the inner function has access to the scope in the outer function, this is called Lexical Scope or Closure. 
	
		```
			// Scope A
			var myFunction = function () {
			// Scope B 
			var name = 'Todd' //defined in Scope B
			var myOtherFunction = function () {
			// Scope C: 'name' is accessible here!
				}
			}	

		```
		
	
		* Closures can return a function reference. Inside our scope, we can return things so that they're available in the parent scope: 
			
			```
		var sayHello = function (name) {
				var text = 'Hello, ' + name; 
				return function () {
					console.log(text)
				};
		};
		```
		
			The closure concept we've used here makes our scope inside sayHello inaccessible to the public scope. 
			
			```
			var helloTodd = sayHello('Todd'); 
			helloTodd(): // will call closure and log 'Hello, Todd'
		```
	* Function declaration vs. Function expression 
		* One difference is that when we use a function expression, we do not assign a "name" to the function. A function without a name is called an **anonymous function.**
	* IIFE: Immediately Invoked Function Expressions
		* An immediately invoked function expression (IIFE) is a function which immediately gets called after it is written. To create an IIFE, simply wrap your anonymous function in parentheses. 
		* One common use case of IIFE is to return an object.
	
		```
			var personObject = (function() {
				return {
					name: "Tim",
					age: 32, 
					occupation: "developer", 
					hobbies: "sailing"
				};
			})();
		```
		 After the code is executed, the personObject is equal to the object that was returned from the anonymous function. We can now ise the object: 
		 
	 	```
	 	personObject.name; // returns "Tim"
		personObject.age; // returns 32
		personObject.occupation; // returns "developer"
		personObject.hobbies; // returns "sailing"
		
		```
			
		This time the object will have functions for the values of the keys: 
		
		```
		var personObject = (function invokeRightAway(){ 
			var person = "Elie"; 
			return {
				getName: function(){
					return person;
				}, 
				setName: function(newName){
					person = newName;
				}
			};
		})();
		
		personObject.getName(); // "Elie"
		personObject.setName("Mary"); //
		personObject.getName(); // "Mary"
		person; // ReferenceError: person is not defined
		```
		

	* Hoisting 
		* Because variable declarations (and declarations in general) are processed before any code is executed, declaring a variable anywhere in the code is equivalent to dclaring it at the top. This also means that a variable can appear to be used before it's declared. This behavior is called "hoisting", as it appears that the variable declaration is moved to the top of the function or global code. 
		* Hoisting and Inside of Functions 
			* If you have a variable delclared anywhere within a function scope it's going to brough to the very top. But just the declaration not the initalization. Initialization is when a value it applied and declarartion is when the variable is declared. It's best practice to declare all the variables at the top because it's happening behind the scenes anyways. 
		* Hoisting in Function Declarations vs Function Expressions 
			* Function declarations are fully defined before the code is run. Since a function expression assignes an anonymous function to a variable, hoisting applies to that variable name as well. 
			* Javascripy always starts from the in (the closet function) and works its way out (to other functions and eventually the global scope)
		

		
		
		
		
		