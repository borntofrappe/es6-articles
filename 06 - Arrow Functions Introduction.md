ES6 has introduced arrow functions which have three main benefits. First, they have a _concise syntax_. Secondly, they have _implicit returns_, which allows us to write nifty one-liners.

Thirdly, _they don't rebind the value of **this**_ when you use a arrow function inside of another function, which is really helpful for when you're doing things like click handlers and whatnot.
 
We're going to take a look at a whole bunch of examples, and we're going to be using arrow functions all over the place in the [ES6.io course](https://ES6.io).

I've got an array of names:

```js
const names = ['Wes', 'Kait', 'Lux'];
```

I want to add `'Bos'` to the end of all three of these. 

Normally, you'd do something like this:

```js
const fullNames = names.map(function(name){
  return `${name} Bos`;
});

console.log(fullNames); // Wes Bos, Kait Bos, Lux Bos
```

We're going to use **backticks** here, which is our template strings. Don't worry exactly about what that is, if you're not sure just yet. We have a whole chapter on that coming up.

Anyway, It's going to give me Wes Bos, Kait Bos, Lux Bos in the entire array. It took this array, transformed it into whatever the item was, and added the name "Bos" on the end.

That makes sense to me, but this isn't an arrow function. Let's take a look at how we could rewrite that. 

### Turn it into an Arrow Function

The first thing you do to create an arrow function is simply deleting the keyword `function` and add in its place what's called a _fat arrow_. It looks like this: `=>`

```js
const fullNames2 = names.map((name) => {
 return `${name} Bos`;
});

console.log(fullNames2); // Wes Bos, Kait Bos, Lux Bos
```

If you've come from other programming languages, you might have seen that before, but in JavaScript it's the first time we're seeing a fat arrow.

It'll do exactly the same thing as `function`. If you `console.log` it, there should be no surprises there. We get the exact same thing. 

### Removing Parens With Single Params

We can go even further with it where, if you only have _one parameter_ you can take out the parentheses:

```js
const fullNames3 = names.map(name => {
 return `${name} Bos`;
});

console.log(fullNames3); // Wes Bos, Kait Bos, Lux Bos
```

That's a bit of a stylistic choice. Some prefer the parenthesis regardless if you have one or more. In many callback functions (like our map function) it's nice to leave them out for a very clean syntax.
 
### Arrow Function Implicit Return

What else could I do with this? I can use what's called an **implicit return**.

Hold on — what's a _explicit_ `return`? 

That's when you explicitly write `return` for what you want to `return`. But a lot of these callback functions that we write in JavaScript are just one-liners, where we just return something _immediately_ in one line. We don't need a whole bunch of lines. 

So, **if the only purpose of your arrow function is to return something**, there is no need for the `return` keyword.

Our three line function with an explicit return is now a single line function with an **implicit return**.

```js
const fullNames4 = names.map(name => `${name} Bos`);

console.log(fullNames4);  // Wes Bos, Kait Bos, Lux Bos
```

We did three things here:

1. delete the return
2. put it all up on one line
3. delete the curly brackets

When you delete your curly brackets, it's going to be an implicit return, which means we do not need to specify that we are returning `${name} Bos`. 

It will just assume that we're doing so, and you can `console.log` it to see the same thing again.

### No Arguments with Arrow Functions

Then finally, if you have no arguments at all, you need to pass some empty parenthesis there. This was not the case in our above examples, where we needed an argument for the map function.

Maybe we'll just return `Cool Bos`, and they'll all be Cool Bos at the end. 

```js
const fullNames5 = names.map(() => `Cool Bos`);

console.log(fullNames5); // Cool Bos, Cool Bos, Cool Bos
```

Another pattern you may see is developers using an underscore `_` in place of `()`:

```js
names.map(_ => `Cool Bos`);
```

We call this a _throwaway variable_ because we're actually creating a variable called `_` but not using it. It's important to note that the `_` **does not have any significance at all**. I could use any variable name here, we just throw it away. 

```js
names.map(x => `Cool Bos`);
names.map(WESBOS => `Cool Bos`);
names.map(_ya___Yayayayay => `Cool Bos`);
names.map(do_yaget_the_point => `Cool Bos`);
```

Personally I prefer to use `() =>` over `_ =>` when there are no params but I'll let you make that decision on your own. 

### Arrow Functions are Always Anonymous Functions

Another thing we need to know about arrow functions, at least right now, is that arrow functions are always anonymous functions. 

What is an anonymous function? Actually what's a named function?

A named function is something like this: 

```js
function sayMyName(name) {
  alert(`Hello ${name}`);
}
```

The benefit to using a named function is that if you have a stack trace, which means if you have an error and you want to figure out, where did this go wrong, sometimes a line number as to where it happened isn't very helpful, so you need to know actually the name of the function that it got called in. 

If you use an arrow function, **you cannot name them**. None of our arrow functions have a name. 

You can, however, put them in a variable, storing the arrow function in a variable which can be then called including arguments.
 
```js
const sayMyName = (name) => {alert(`Hello ${name}!`)}

sayMyName('Wes');
```

The thing we need to know about that is that it is an anonymous function and it will not give us very good stack traces. However, if you're not too concerned with that, then you can absolutely go ahead.
