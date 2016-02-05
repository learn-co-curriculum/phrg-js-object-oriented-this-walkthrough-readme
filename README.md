# Creating Objects

## Objectives
+ Create a constructor function
+ Use a constructor function to create an object
+ Explain what a constructor function is and how it works

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

You'll notice the name of the construction function `Sandwich` starts with a capital letter. This is important. Every constructor function starts with a capital letter, just like our class names in Ruby.

Next, we define the function to accept a whole bunch of parameters. When we create objects with this constructor function, we'll pass in the value of the properties we want our object to have.

You'll also notice inside the body of the constructor function we're using `this`. In this case, `this` will refer to the current object being created. You can equally compare the usage here to the use of `self` inside of an initialize method in a Ruby class.


## Creating Instance From Constructor

Let's go ahead and use this handy constructor function to create our sandwiches:

```js
var blt = new Sandwich("white", false, "bacon", "mayo", "lettuce", "none")

var turkeyClub = new Sandwich("sourdough", true, ["turkey", "bacon"], "mayo", ["lettuce", "tomato"], "cheddar")

var grilledCheese = new Sandwich("white", false, "none", "none", "none", "cheddar")
``` 

And just to prove that we're dealing with sandwiches:

```js
blt.constructor;
// returns the Sandwich constructor function
turkeyClub.constructor;
//returns the Sandwich constructor function
grilledCheese.constructor;
//returns the Sandwich constructor function

```

