## Intermediate Javascript II
* Introduction to jQuery 
	* Instead of using the native DOM API interaction with elements on the page, we can use jQuery instead. 
	* All of the jQuery selectors and many functions begin with a **$**. The expresssion jQuery === $ will always be true. 
	* Loading the DOM can be done three ways: 
		
		```
		$(document).ready(function(){
		    // the DOM has now loaded
		});
		
		$(function() {
		    // a shorter way to wait for the DOM to load
		});
		
		document.addEventListener("DOMContentLoaded", function() {
		    // a longer way to wait for the DOM to load, without jQuery.
		    // jQuery's syntax is much shorter!
		}); 
		
		```
* jQuery objects/ get / selectors 
	* jQuery selects items via CSS selectors, just like querySelctor and querySelectorAll in vanilla JavaScript. One major difference between jQuery and JavaScript methods is what they return to you. jQuery returns an (array-like) object called jQuery object. 

* Common jQuery Methods 
	* Manipulating and modifying elements and attributes 
	* **html/text/var**
		* To grab the innerHTML of selected elements we can use the html function. To grab the innerText of a selected element(s) we can use the text function. For the input elements, we can get the values inside of them with the val function. 
		
			```
			$(document).ready(function(){
		    $("article").html(); // innerHTML
		    $("article").text(); // innerText
		    $("input").val(); // value
			}); 
			```
		* If you pass a string into these methods they'll work as setters instead of getters. They will set the text inside of the element to the string that is passed in. 
		
			```
			$(document).readt(function({
				$("article").html("<h1>Here's some large text</h1>");
				$("li").text("hi!"); // innerText
	    		$("input").val("new value"); // value = new value
			});

	*  **addClass/removeClass/toggleClass**
		
			$(document).ready(function(){
			    $("article").addClass("hidden"); // add a class
			    $("article").removeClass("hidden"); // remove a class
			    $("article").toggleClass("hidden"); // toggle the class (if on -> off, if off -> on)
			});
	
	* **css/data/attr**
		* To access the styles of an element we can use the css function. To access the attributes of an element we can use the attr function. To access the data-attributes of an element we can use the data function. As with text, html, and val, these methods can be used as getters or setters. Pass in a single argument to use them as getters, pass in two to use them as setters. 
		
			$(document).ready(function(){
			    $("article").css("background-color", "red");
			    $("article").css("background-color"); // "red"
			    $("article").attr("style", "display:flex;");
			    $("article").data("id", "1");
			});
			
	* Transvering the DOM with jQuery - **find/parent/childern/prev/next**
		* For DOM tranversal we can iuse find, which accepts a CSS selector to find elements inside a selected element. To access the childern of a selected element we can use childern and to access a child's parent element we can use parent. To find the next elemnt in a list of siblings we can use next and to find the previous sibling we can use prev. 
		
		
			```
			$(document).ready(function(){
				var $childDivsInsideArticle = $("article").find("div").childern();
			})
			
	* filtering with jQuery
		* jQuery has quite a few helpful methods to select elements based on certain filters. These methods include is, has, not, eq, and many more. 
		* The eq method is particularly important when accessing elements inside of a jQuery object. We can use it in place of bracket notation to access elements inside of a jQuery object. 
		
			```		
			var $firstLi = $("li").eq(0);
			var $secondLi = $("li").eq(1);
			$firstLi.text(); // "Item 1"
			$secondLi.text(); // "Item 2"	
			
	* Adding and removing elements from the DOM - **after/before/append/prepend**
		* To add elements to the DOM after a selected element or before a selected element. We can also append them to a selected element (nested at the end an element) or prepend them to a selected element (nested at the beginning). 
		
			```
			$(document).ready(function(){
			    var $newParagraph = $("<p>");
			    $newParagraph.text("Another article");
			    $newParagraph.css("color","red");
			
			    var $anotherParagraph = $("<p>", {
			        text:"Another approach",
			        css: {
			            color: "purple",
			            // we have to use quotes because of the '-'
			            "font-size": "2em"
			        }
			    });
			    $("article").append($newParagraph);
			    $("article").prepend($anotherParagraph);
			});
			
	* Adding and removing events with jQuery   
		* Just like addEventListener, the first parameter to on or off is the name of the event followed by a callback function. The second parameter is the callback, which specified what we want to do when the event is fired. Also similar to addEventListener, the callback has access to an event object as its first parameter. 
		
			```	
			$(document).ready(function(){
		   		$("article").on("click", function(e){
		        	console.log($(e.target).val()); // This works great.
		        	console.log(e.target.val()); // TypeError! e.target isn't a jQuery object, so doesn't have a .val method.
		    	});
			});