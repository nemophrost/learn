---
layout: post
title:  "Intro to JavaScript Part 3"
date:   2015-11-11 9:00:00
---


Arrays are ordered lists
---

An `array` is another data type similar to objects in that they allow you to hold multiple values. Unlike objects which have names for each value, arrays are simply an ordered list of values.

	var pets = [
		"Sparky Bark",
		"Bob Marley",
		"Pebbles Beach"
	];

You use **square brackets** around the contents of your array and separate each value with a comma.

---

You use **bracket notation** for accessing and setting values in an array. (As opposed to dot notation with objects)

	console.log(pets[0]);
	// → Sparky Bark

	console.log(pets[1]);
	// → Bob Marley

	pets[1] = "Robert Marley";
	console.log(pets[1]);
	// → Robert Marley

You access items in an array by their **index**. Arrays have a **zero-based** index, meaning that the **first item in the list has the index of 0**, not 1. The second item has the index of 1, etc.

---



Some handy methods (and a property)
---

Arrays have a `.length` property like strings and they also have some commonly used methods for adding and removing items.

	pets.length
	// → 4

---

Add items to the end of the list with `.push()`

	pets.push("Fido Fedora");

---

Remove the last item in a list with `.pop()`. This also returns the removed item.

	pets.pop();
	// → Fido Fedora

---

Conversly, add items to the beginning of the list with `.unshift()`

	pets.unshift("Ramada Thistle");

---

Remove and return the first item in the list with `.shift()`

	pets.shift();
	// → Ramada Thistle

---



Loops
---

Loops allow you to do something repeatedly.

We are going to learn about two types of loops. `for` loops and `while` loops.

While loops
===

While loops start with the `while` keyword followed by parentheses containing a condition expression and curly braces.

<div><a class="code-link" data-prefix="var pets = ['Sparky Bark', 'Robert Marley', 'Pebbles Beach'];"><i class="fa fa-link"></i></a></div>

	// log each pet name in order
	var petIndex = 0;
	while (petIndex < pets.length) {
		console.log(pets[petIndex]);
		petIndex = petIndex + 1;
	}
	// → Sparky Bark
	// → Robert Marley
	// → Pebbles Beach

While loops are just like `if` statements except that the code within the curly braces will execute over and over as long as the expression in the parentheses is true.

---

Be careful with loops so that you do not end up with one that runs forever. This is an example of such an **infinite loop**.

	var petIndex = 0;
	while (petIndex < pets.length) {
		console.log(pets[petIndex]);
		// petIndex = petIndex + 1;
	}
	// → Sparky Bark
	// → Sparky Bark
	// → Sparky Bark ...

If we do not increase the value of `petIndex` then the expression `petIndex < pets.length` will always be true and the inner code of the loop will repeat forever and crash your browser.

---


For loops
===

For loops combine this common usage pattern of while loops into a more concise form.

Start with the `for` keyword followed by parentheses and curly brackets as before.

	for ([initialization]; [condition]; [final expression]) {
		// code
	}

The parentheses of a `for` loop contain three parts.

1. Initialization is where you can declare or assign variables you need to use within your loop
2. Condition is an expression to be evaluated before each loop iteration. If it is true, the iteration will run. (Like `while` condition)
3. Final expression is an expression (small bit of code) that runs at the end of each loop

---

Here is a `for` loop that reproduces the functionality of the while loop above:

<div><a class="code-link" data-prefix="var pets = ['Sparky Bark', 'Robert Marley', 'Pebbles Beach'];"><i class="fa fa-link"></i></a></div>

	for (var i = 0; i < pets.length; i++) {
		console.log(pets[i]);
	}
	// → Sparky Bark
	// → Robert Marley
	// → Pebbles Beach

Commonly the variable `i` is used for indexes in loops, so we use `i` here instead of `petIndex`.

`i++` is JavaScript shorthand for incrementing the variable. It does the same as `i = i + 1`


---



Looping methods
---

Arrays have some build in methods that allow you to do some of these same things without having to worry about remembering syntax or accidentally creating infinite loops.

forEach
===

`.forEach()` is a method that takes a function as a parameter. This function will be called for each item in the array, in order. The function is called each time with the following parameters:

	pets.forEach(function(item, index, array) {
		// do something
	});

1. The item from the array
2. The item's index in the array
3. The array itself

---

So to log our pets again using `.forEach()`, it would look something like:

<div><a class="code-link" data-prefix="var pets = ['Sparky Bark', 'Robert Marley', 'Pebbles Beach'];"><i class="fa fa-link"></i></a></div>

	pets.forEach(function(petName) {
		console.log(petName);
	});
	// → Sparky Bark
	// → Robert Marley
	// → Pebbles Beach

> Notice how you can change the name of the parameters to whatever you want.
>
> Use names that make sense for the array you are looping through. I also didn't include the second and third parameters. They are still being passed to the function, but since I don't need them, I don't need to give them a name.


map
===

Another incredibly useful method on arrays is called `.map()`. Similar to forEach, `.map()` takes a function as a parameter and the parameters passed to the function are the same. The difference is that `.map()` takes the returned values from the function and creates a new array with those returned values.

For example, if you want to get an array of your pets' initials, you could do something like:

<div><a class="code-link" data-prefix="var pets = ['Sparky Bark', 'Robert Marley', 'Pebbles Beach'];"><i class="fa fa-link"></i></a></div>

	var initials = pets.map(function(name) {
		var nameParts = name.split(" ");
		return nameParts[0].charAt(0) + nameParts[1].charAt(0);
	});
	console.log(initials);
	// → [ "SB", "RM", "PB" ]

> FYI, `.split()` is a method on all strings that will split the string up into an array of strings based on what you pass into it.
>
> `.charAt()` will give you the character at a specified index within a string.


filter
===

`.filter()` is similar to both forEach and map, except it returns a filtered array based on the original. In your parameter function, return true if you want the item in the filtered list and return false if you don't.

<div><a class="code-link" data-prefix="var pets = ['Sparky Bark', 'Robert Marley', 'Pebbles Beach'];"><i class="fa fa-link"></i></a></div>

	var longPetNames = pets.filter(function(name) {
		return name.length >= 12;
	});
	console.log(longPetNames);
	// → [ "Robert Marley", "Pebbles Beach" ]



---


<hr class="visible" />


Exercise 1
---

Let's reproduce the filter method using a for loop.

<div><a class="code-link" data-prefix="var pets = ['Sparky Bark', 'Robert Marley', 'Pebbles Beach'];"><i class="fa fa-link"></i></a></div>

	var longPetNames = [];
	for (var i = 0; i < pets.length; i++) {
		if (pets[i].length >= 12) {
			longPetNames.push(pets[i]);
		}
	}
	console.log(longPetNames);
	// → [ "Robert Marley", "Pebbles Beach" ]

<div class="code-cover"></div>

1. Create an empty array (looks like `[]`) as a variable to store your filtered items
2. Using a for loop, iterate over each pet and `.push()` the name into the filtered array when the name length is greater than or equal to 12 characters
3. Log the filtered array


---


<hr class="visible" />


Exercise 2
---

Create a function that takes a name and returns an array of initials using `.map()`

<div><a class="code-link" data-prefix="var pets = ['Sparky Bark', 'Robert Marley', 'Pebbles Beach'];"><i class="fa fa-link"></i></a></div>

	var getInitials = function(fullName) {
		var names = fullName.split(" ");
		return names.map(function(name) {
			return name.charAt(0);
		});
	};
	console.log(getInitials("Sparky Bark Johnson Elias Rigby"));
	// → [ "S", "B", "J", "E", "R" ]

<div class="code-cover"></div>

1. Create a function that takes a parameter named `fullName`
2. Split the name by spaces and store that as an array
3. Use `.map()` on the array of names to get an array of initials
4. Return the array of initials
5. Try it with a 6 part name like *Sparky Bark Johnson Elias Rigby*


---


More
===

Now we want to use our new `.getInitials()` function to get an array of all our pets' initials.

<div><a class="code-link" data-prefix="var pets = ['Sparky Bark', 'Robert Marley', 'Pebbles Beach'];"><i class="fa fa-link"></i></a></div>

	var getInitials = function(fullName) {
		var names = fullName.split(" ");
		return names.map(function(name) {
			return name.charAt(0);
		}).join("");
	};

	var petInitials = pets.map(getInitials);

	console.log(petInitials);
	// → [ "SB", "RM", "PB" ]

<div class="code-cover"></div>

1. Use `.map()` on `pets` with `getInitials` as the function.
2. We want each pet's initials to be a string instead of an array of letters, so use `.join("")` on the map being returned from `getInitials` to convert the array into a string (`.join()` does the opposite of `.split()`).
3. Log the results


---
