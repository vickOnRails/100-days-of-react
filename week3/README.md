## Day 15

### What I worked on

Continued to make [one-million-africa](https://one-million-africa.netlify.com) responsive on mobile.

### A few challenges

I came across a typescript bug today, but I didn't get enough time to fix it. I hope to do so tomorrow.

### What I learned

While working with React Router, I needed to push the top `Route's` props to another `Route` component. Something like this...

```js
<Route to="/" component={Home} prop={props} />
```

But this didn't work. After a few minutes of googling, I found this detailed [article](https://tylermcginnis.com/react-router-pass-props-to-components/) on how to correctly pass props to `Route` componenets by Tyler Mcginnis.

According to the article, we could pass props to a `Route's` child by replacing the `component` attrubute with a `render` attribute like so...

```js
    <Route to="/" render={}/>
```

The `render` attribute will have to return a component that carries the props.

```js
    <Route to="/" render={(props)=><Component {...props} attr={value}>}/>
```

This way, we can pass data to `Route` children without losing our souls.

Have a great day and checkout [day 14](https://github.com/vickOnRails/100-days-of-react/tree/master/week2#day-14).

## Day 16

### What I worked on

I read some part of the Advanced React Docs.

### A few challenges

No challenge today. Except still struggling to find time for the exercise.

### What I learned

Learned more about forwarding `refs` today. See more at [link](https://reactjs.org/docs/forwarding-refs.html)

Have a great day and checkout [day 15](https://github.com/vickOnRails/100-days-of-react/tree/master/week3#day-15).

## Day 17

Was too tired after work, missed today😁

## Day 18

### what I worked on

I read some part of the official React Docs

### A few challenges

None really

### What I learned

I learned about Code Splitting in React.

Modern JavaScript programs normally bundle `.js` code into a single file. This kind of bundling is great for ensuring fewer http requests.

But there's a downside. If all `.js` files are bundled into one large file, then that large file will always be downloaded.
Even when the user visits a page that doesn't need some part of the bundled file.

It gets crazier when a user visits the site for the first time and downloads this very huge `bundle.js` file upfront. This would ruin user experience metrics like Time To Interactive,First Meaningful Paint and e.t.c.

Plus, a huge percent of the .js code will not be needed in the first 1 minute of loading the site.

That's where Code Splitting comes in. Since we can bundle `.js` files, we want to be smart about how we do so.
Think about the lovely sweet spot between reducing htttp requests and serving the most important `.js` functionality first.

You see where this is going right?

Code splitting helps us bundle and lazy load just the things that are currently needed by the user.

One way to do this with React is to use the `React.lazy` funtion wrapped by a `Suspence` component.

Before

```js
import SomeComponent from "./SomeComponent";
```

With Code Splitting

```js
import SomeComponent = React.lazy(()=> import('./SomeComponent'))
```

`React.lazy()` takes a function that calls a dynamic import statement. It returns a promise which resolves to a module with a default export returning a React component. We can then use the component like so.

```js
const Home = () => (
  <div>
    <Suspense fallback={<div>Loading...</div>}>
       </SomeComponent>
    </Suspense>
  </div>
);
```

The `fallback` props to the `Suspense` component specifies the component to be rendered while we're waiting for the lazy loading component to load.

I did a demo that you can see here.

### Another impressive usecase I learned about was the Route-based code splitting

It's a great idea because routes/pages are sensible chunks of functionality. A user loads a page and everything they need to interact on that page is downloaded, another set is downloaded when they get to another page.

Here's how we could possibly do that with React Router

```js
import { BrowserRouter as Router, Route, Switch } from "react-router-dom";
import React, { Suspense, lazy } from "react";

const Home = lazy(() => import("./routes/Home"));
const Users = lazy(() => import("./routes/Users"));

const App = () => (
  <Router>
    <Suspense fallback={<div>Loading</div>}>
      <Route exact path="/" component={Home} />
      <Route exact path="/user" component={User} />
    </Suspense>
  </Router>
);
```

NB: `React.lazy` only works with default exports.

Have a great day and checkout [day 16](https://github.com/vickOnRails/100-days-of-react/tree/master/week3#day-16).

---

## Day 19

### What I worked on

I completed the [one million Africa site](https://one-million-africa.netlify.com)

### A few challenges

I tried converting an `uncontrolled` components to `controlled` one. Since I had lots of input fields in [one-million-africa](https://one-million-africa.netlify.com), I wanted to house `state` for them all in one object. Like this

```js
state = {
  inputValues: {
    inputOne: "",
    inputTwo: "",
    inputThree: ""
  }
};
```

This would change the way I `setState`

```js
this.setState(inputValue: { inputOne: ''})
```

This is taking too much time to resolve. I'll share how I got over it tomorrow.

### What I learned

I learned about events in [SyntheticEvents](https://reactjs.org/docs/events.html) in React. They are React's implementation of native browser events; essential a cross browser wrapper that exposed all the properties and functions of the original browser events. So you can pretty much do stuff like `e.preventDefault()` and `e.stopPropagation()`.

I also learned about event pooling and how ReactJs makes use of the `SyntheticEvents` to ensure performance gains. I guess more on that tomorrow (or maybe I'll just learn something new).

Have a great day and checkout [day 18](https://github.com/vickOnRails/100-days-of-react/tree/master/week3#day-18).

---

## Day 20

### What I worked on

Today, I wanted to learn about React Hooks so I made a little todo list with `useState`. Demo [here](https://todo-react-hooks.netlify.com) and source code [here](https://github.com/vickOnRails/todo-react-hooks)

### A few challenges

None that wasn't easy to fix.

### What I learned

React hooks let you hook (😁) into React's state and component lifecycles without using classes.

`useState` is a react hook. It takes the initial state as an argument and returns the current state and a function to update the state. Here's how we would use `useState`

```js
//useState must be imported first
import React, { useState } from "react";

const [text, updateText] = useState("");

// To update the text state
updateText(newValue);
```

The parameter `useState` receives must not be a `string`. It could be a string, number etc.

```js
const [oranges, updateOranges] = setState([]);
```

It turns out React hooks weren't that difficult after all. Read more about them [here](https://reactjs.org/docs/hooks-intro.html).

Have a great day and checkout [day 19](https://github.com/vickOnRails/100-days-of-react/tree/master/week3#day-19).

---

## Day 21

Today, I spent the whole of my waking time travelling. Absolutely didn't touch React.

## Day 22

### What I worked on

I built a note taking app to learn about styled-components. Github gist of WIP [here](https://gist.github.com/vickOnRails/326b4c13aece41b692acc84554bb7d45).

### A few challenges

I felt like I was doing things the wrong way. Maybe everything will seem normal after a few trys. (Or I could just go back to peaceful CSS land)

### What I learned

I learned to declare my functions in a more type-safe way. I would previously declare them like

```js
const doSomething: Function = (arg: any) => {};
```

Typescript wouldn't shout at me because it's progressive. Plus a huge part of my previous Typescript code were just `any` typings🤣.

But here's how I'll do stuff like that now

```js
const doSomething: (arg1: string) => void = () => {};
```

Declaring `functions` like this ensures more type safety. From the function arguments down to the return value.

I think that's cool.

Have a great day and checkout [day 20](https://github.com/vickOnRails/100-days-of-react/tree/master/week3#day-20).
