## Day 1

### What I worked on
I worked on the exercises from Transvesary's introduction to TypeScript as the project I'm working on requires I use TypeScript in my React code.

See TypeScript tutorial [here](https://www.youtube.com/watch?v=rAy_3SIqT-E)

### A few challenges
I used `let` to declare variables in TypeScript, but it kept on giving me errors about block scope. The transpiled `.js` file converted those declarations to `var`. I had no idea why. 

While working on a little todo app, I had serious issues with deciding which components were supposed to be stateful and functional. I guess this will improve over time

### What I learned

These are some jottings from the tutorial. 

TypeScript gives us Strings, Number, Boolean, Array, Any, Void, Null, Tuple, Enum, Generics.

Any: Can be any type
Void: No type returned
Tuple: Array with fixed number of elements
Enum: Enumerated values
Generics: Constraints for some types

Typescript gives us class based objects, properties, methods, Encapsulation, Inheritance, access modifiers.

Typescript files need to be transpiled into .js files. We need TSC to transpile .ts to .js.

We need Nodejs to run typescript.
To create a variable with type, we do 

```let myString: string;```

We can also declare arrays too like this

```var strArray: string[];```

Another way to decalre array is 

```var strArray: Array<string>;```

Tuples are arrays with multiple types. We declare tuples as
```mytup: [string, number];```

When giving values to the arrays, the format must match the declared one. In the above case, the first value must be a string and the second must be a number. 

The null type can be assigned to `null`, or `undefined`. If assigned to something else, it trows an error.

#### Functions
Typescript can be used to put limits on types that functions work with. Here's how it works

```function getSum(num1: number, num2: number): number {}```

The `:number` at the end of the function arguments ensures the function returns a number. If is doesn't we get an error.

We can also declare array arguments as optional by adding `?` like so

```function getName(firstname: string, lastname?: string) {}```

This tells the parser that argument 2 is optional.

We can make a function return void. It will return nothing and the parser will raise an error if it returns any value. 

Interfaces can be used to create custom types

#### Classes in TypeScript

Classes can have a constructor that runs everytime an instance of that class is made. 

We can also make use of access modifiers. `Private`, `Public`, `Protected` etc.

`Private` means the variable cannot be accessed outside the class definition.

`Public` means we can access the variable from any where in the program.

`Protected` means we can only access the class from the definition and other classes that inherit the class.
We can also have methods that perform certain operations on the class properties. Methods are can also be controlled by access modifiers. 

#### Class inheritance

If a class inherits another, the constructor will take the original arguments of the new class alongside the arguments of the extended class. Classes that extend other classes must call the super() method with the arguments of the extended class.

To call a method of the extended class, we use `super.methodName()`.

Classes can also implement Interfaces. This means the interface is declared as a custom type for the class.

interface UserInterface {
    name: string;
    email: string;
    register();
    payInvoice();
    }


Class User implements UserInterface {}

Methods of classes can also be defined in interfaces.