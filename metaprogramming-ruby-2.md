# Metaprogramming Ruby 2 - synopsis
by Maddie Campos(mailto:maddie@blubeta.com)
September/October 2016

## Concepts

* Objects and Classes
- An Object is a bunch of instance variables, linked to a class
- The methods live in the object's class (instance methods of the class)

- A Class is an object (an instance of Class) plus a list of instance methods and a link to a superclass. Class is a subclass of Module (so class is also a module) *** Classes are just objects!*** (instance methods of the Class class)

 * Namespacing
Namespacing is a great organizational tool, and prevents monkeypatching (changing already existing Ruby methods, either inadvertently or on purpose)

* Ancestor chain
Something cool: If you go up the ancestors chain, Kernel is actually a Module that has a lot of private methods that you can call from anywhere in your code (like `print`and the `awesome_print` gem!)

If you add a method to Kernel, this method will be available to all objects because of the ancestor chain!

* Self
Every line of Ruby code is executed inside an object. The current object is also known as `self` (you can access it with the self keyword). As soon as a method is explicitely called on another object, that object becomes `self`

* Private

* Scope - which variables and methods can be seen by which lines of code

* Method look-up goes one step to the right and then up the ancestors chain

* A method , specific to a single object, is called a Singleton Method

* ROM (Ruby Object Model): classes, singleton classes, and modules. There are also instance methods, class methods, and Singleton Methods.

* Best sentence in the book: "The superclass of the singleton class of an object is the object's class. The superclass of the singleton class of a class is the singleton class of the class's superclass" (p. 126)