# Creating Objects

## Objectives
+ Create a constructor function
+ Use a constructor function to create an object
+ Explain what a constructor function is and how it works
+ Explain what `this` is in the context of an object

## Intro

We know how to make objects in JavaScript. So let's make a few sandwiches:

```js

var blt = {
  breadType: "white",
  crust: false,
  meat: "bacon",
  condiments: "mayo",
  veggies: "lettuce",
  cheese: "none"
}

var turkeyClub = {
  breadType: "sourdough",
  crust: true,
  meat: ["turkey", "bacon"],
  condiments: "mayo",
  veggies: ["lettuce", "tomato"],
  cheese: "cheddar"
}

var grilledCheese = {
  breadType: "white",
  crust: false,
  meat: "none",
  condiments: "none",
  veggies: "none",
  cheese: "cheddar"
}

```

Ok but suddenly this got tedious and I only made three sandwiches. You notice that we're copying and pasting a lot of code. Wouldn't it be nice to have one central place to scaffold out what we're building? Using a class in Ruby makes things so much more easy. JavaScript better have something similar...

## Constructor Function

And they do! JavaScript uses a constructor function instead of building out a full class. But the constructor function conceptually does the same thing as Ruby. We basically build a prototype for what an object will look like, including all the properties. 

Let's go ahead and build our constructor function for our sandwich objects:


```js
function Sandwich (bread, crust, meat, condiments, veggies, cheese ){
  this.breadType = bread
  this.crust = crust
  this.meat = meat
  this.condiments = condiments
  this.veggies = veggies
  this.cheese = cheese
}
```

You'll notice the name of the construction function `Sandwich` starts with a capital letter. This is important. While the capitalization of a function does not affect how it behaves, it serves as an important signal to our fellow programmers that this function should ONLY be used as a constructor.

Next, we define the function to accept a whole bunch of parameters. When we create objects with this constructor function, we'll pass in the value of the properties we want our object to have.

You'll also notice inside the body of the constructor function we're using `this`. In this case, `this` will refer to the current object being created. For now it's ok to think about `this` being similar to Ruby's self.  In this context, `this` refers to the object itself just like `self` does in Ruby.  


## Creating Instance From Constructor

Let's go ahead and use this handy constructor function to create our sandwiches:

```js
var blt = new Sandwich("white", false, "bacon", "mayo", "lettuce", "none")

var turkeyClub = new Sandwich("sourdough", true, ["turkey", "bacon"], "mayo", ["lettuce", "tomato"], "cheddar")

var grilledCheese = new Sandwich("white", false, "none", "none", "none", "cheddar")
``` 
Notice that when we call these functions we always call them with the `new` keyword.  In Ruby you're used to calling `MyClass.new` and in JavaScript we're going to do something very similar.  All functions in JavaScript can be invoked with the new keyword but we only want to do it with functions that are intended to be used as constructor functions.  The way we let ourselves and others know when to use the new keyword is by making constructor functions start with capital letters!  If we forget the new keyword we'll run into all sorts of problems.

How do we know that these are objects and that they were all created using the same constructor function?  We can look at the constructor property which gets set during the initialization of the object for us!
```js
blt.constructor;
// returns the Sandwich constructor function
turkeyClub.constructor;
//returns the Sandwich constructor function
grilledCheese.constructor;
//returns the Sandwich constructor function
```

## Reading Property Values

So now that we used the constructor function, how do we read the properties of an object?

You can access the properties just like you did when we were treating objects as hashes:

```js
blt["breadType"];
//returns white
turkeyClub["meat"]
// returns ["turkey", "bacon"]
grilledCheese["crust"]
//returns false
```

Or, you can use the dot-notation you're familiar with from Ruby:

```js
blt.breadType;
//returns white
turkeyClub.meat
// returns ["turkey", "bacon"]
grilledCheese.crust
//returns false
```

## Reassigning Properties

Let's say you actually like to eat your grilled cheese with a slice of bacon and tomato, we would need to change the values of the `meat` and `veggies` properties:

```js
grilledCheese["meat"] = "bacon"
grilledCheese.veggies = "tomato"
```


<p data-visibility='hidden'>View <a href='https://learn.co/lessons/js-create-objects-readme'>Creating Objects in JS</a> on Learn.co and start learning to code for free.</p>
