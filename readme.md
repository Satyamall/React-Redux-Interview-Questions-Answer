
# Redux Interview Questions

# Explain redux to a 5 year old (ELI5)?
=> Since a 5-year old doesn’t have the time for technical jargon, I’ll keep this very simple but relevant to our purpose of learning Redux.

So, here we go!

Let’s consider an event you’re likely conversant with - going to the bank to withdraw cash. Even if you don’t do this often, you’re likely aware of what the process looks like.

You wake up one morning, and head to the bank as quickly as possible. While going to the bank there’s just one intention / action you’ve got in mind i.e WITHDRAW_MONEY. You want to withdraw money from the bank.

Here’s where things get interesting. When you get into the bank, you go straight to the Cashier to make your request known.

Wait, you went to the Cashier? Why didn’t you just go into the bank vault to get your money?

After all, it’s your hard earned money.
Well, like you already know, things don’t work that way. Yes, the bank has money in the vault, but you have to talk to the Cashier to help you follow a due process for withdrawing your own money.

The Cashier, from their computer, then enters some commands and delivers your cash to you. Easy-peasy.

# How is redux different from context API?
=> Comparing Redux & Context API:
**Context API:**
- Built-in tool that ships with React.	
- Requires minimal Setup.
- Specifically designed for static data, that is not often refreshed or updated.
- Adding new contexts requires creation from scratch.
- Debugging can be hard in highly nested React Component Structure even with Dev Tool.
- UI logic and State Management Logic are in the same component.

**Redux:**
 - Additional installation Required, driving up the final bundle size.
 - Requires extensive setup to integrate it with a React Application.
 - Works like a charm with both static and dynamic data
 - Easily extendible due to the ease of adding new data/actions after the initial setup.
 - Incredibly powerful Redux Dev Tools to ease debugging.
 - Better code organization with separate UI logic and State Management Logic.

From the above, you must be able to comprehend where the popular opinion Redux is for large projects & Context API for small ones come from.

# Redux: 
=> Redux is an Open Source Library which provides a central store, and actions to modify the store. It can be used with any project using JavaScript or TypeScript, but since we are comparing it to Context API, so we will stick to React-based Applications.

# Context-API: 
=> In a typical React application, data is passed top-down (parent to child) via props, but such usage can be cumbersome for certain types of props (e.g. locale preference, UI theme) that are required by many components within an application. Context provides a way to share values like these between components without having to explicitly pass a prop through every level of the tree.

# what does useSelector do?
=> useSelector() ​ Allows you to extract data from the Redux store state, using a selector function. 

**OR**

useSelector is a function that takes the current state as an argument and returns whatever data you want from it and it allows you to store the return values inside a variable within the scope of you functional components instead of passing down as props.

# What is immutability?
=> The main reason Redux is using immutability is that it doesn't have to traverse an object tree to check for the changes in every key value. Instead, it will only check the object's reference is changed or not in order to update DOM on state change.

**OR**

Immutability is a concept that React programmers need to understand. An immutable value or object cannot be changed, so every update creates new value, leaving the old one untouched.

# Why do we need to spread the state in redux?
=> state the idea is simple: Keep the old state and add or overwrite the DateSucess property. If you don't use spread the new value of state would be only DateSucess and you would lose the foo and zip value, using spread you are just overwriting DateSucess keeping the rest of the value untouched.

**OR**

The JavaScript spread operator ( ... ) allows us to quickly copy all or part of an existing array or object into another array or object.

# What does Object.freeze() do?
=> A frozen object can no longer be changed; freezing an object prevents new properties from being added to it, existing properties from being removed, prevents changing the enumerability, configurability, or writability of existing properties, and prevents the values of existing properties from being changed.

# Why is immutability required by Redux?
=> Immutability of redux state is necessary since it allows detecting redux state changes in an efficient manner. This implies that whenever we want to modify a redux state, we must create a new copy of it and do modifications to that copy - which then becomes the new redux state.

# How does Redux use shallow equality checking?
=> Redux uses shallow equality checking in its combineReducers function to return either a new mutated copy of the root state object, or, if no mutations have been made, the current root state object.

- creates a reference to the current state slice referred to by each key;
- calls the appropriate reducer and passes it the slice;
- creates a reference to the possibly-mutated state slice that's returned by the reducer.

# How well does Redux “scale” in terms of performance and architecture?
=> The work done by Redux generally falls into a few areas: processing actions in middleware and reducers (including object duplication for immutable updates), notifying subscribers after actions are dispatched, and updating UI components based on the state changes. While it's certainly possible for each of these to become a performance concern in sufficiently complex situations, there's nothing inherently slow or inefficient about how Redux is implemented. In fact, React Redux in particular is heavily optimized to cut down on unnecessary re-renders, and React-Redux v5 shows noticeable improvements over earlier versions.

Redux may not be as efficient out of the box when compared to other libraries. For maximum rendering performance in a React application, state should be stored in a normalized shape, many individual components should be connected to the store instead of just a few, and connected list components should pass item IDs to their connected child list items (allowing the list items to look up their own data by ID). This minimizes the overall amount of rendering to be done. Use of memoized selector functions is also an important performance consideration.

As for architecture, anecdotal evidence is that Redux works well for varying project and team sizes. Redux is currently used by hundreds of companies and thousands of developers, with several hundred thousand monthly installations from NPM. One developer reported:
```js
for scale, we have ~500 action types, ~400 reducer cases, ~150 components, 5 middlewares, ~200 actions, ~2300 tests
```

# How does Redux compare to the React Context API?
=> Both are excellent tools for their own specific niche, Redux is overkill just to pass data from parent to child & Context API truly shines in this case.

**[⬆ Back to Answer](#How is redux different from context API?)**

# FAQs of redux https://redux.js.org/faq/

# What is JSX?
=> It is called JSX, and it is a syntax extension to JavaScript. We recommend using it with React to describe what the UI should look like. JSX may remind you of a template language, but it comes with the full power of JavaScript.

JSX produces React “elements”. We will explore rendering them to the DOM in the next section. Below, you can find the basics of JSX necessary to get you started.

# What is Conditional Rendering?
=> Conditional rendering is a term to describe the ability to render different user interface (UI) markup if a condition is true or false. In React, it allows us to render different elements or components based on a condition. This concept is applied often in the following scenarios: 
- Rendering external data from an API.
- Showing or hiding elements.
- Toggling application functionality.
- Implementing permission levels.
- Handling authentication and authorization.

# What is tree-shaking ?
=> Tree shaking is a term commonly used within a JavaScript context to describe the removal of dead code.

It relies on the import and export statements in ES2015 to detect if code modules are exported and imported for use between JavaScript files.

In modern JavaScript applications, we use module bundlers (e.g., webpack or Rollup) to automatically remove dead code when bundling multiple JavaScript files into single files. This is important for preparing code that is production ready, for example with clean structures and minimal file size.

# What are some features of using webpack?
=> 4 Key Concepts of Webpack
- Entry. Webpack creates a graph of all of your application's dependencies. ...
- Output. Once you've bundled all of your assets together, we still need to tell Webpack where to bundle our application. 
- Loaders. The goal is to have all of the assets in your project to be Webpack's concern and not the browser's.
- Plugins. Since Loaders only execute transforms on a per-file basis, plugins are most commonly used (but not limited to) performing actions and custom functionality on "compilations" or "chunks" of your bundled modules (and so much more)

# What are Controlled and Uncontrolled components?
=> Controlled component is component that get the changed value from the callback function and uncontrolled component is component that have the one from the DOM. For example, When input value is changed,we can use onChange function in Controlled Component and also we can get the value using DOM like ref.

In React, an "<input type="file" />" is always an uncontrolled component because its value can only be set by a user, and not programmatically.

# What is flux architecture?
=> Flux is the application architecture that Facebook uses for building client-side web applications. It complements React's composable view components by utilizing a unidirectional data flow. It's more of a pattern rather than a formal framework, and you can start using Flux immediately without a lot of new code.
![download](https://user-images.githubusercontent.com/80479635/166887859-293879fa-a944-4624-a62a-57be733e9684.png)

# What does React.useCallback do?
=> 
```js
const memoizedCallback = useCallback(
  () => {
    doSomething(a, b);
  },
  [a, b],
);
```
Returns a memoized callback.

Pass an inline callback and an array of dependencies. useCallback will return a memoized version of the callback that only changes if one of the dependencies has changed. This is useful when passing callbacks to optimized child components that rely on reference equality to prevent unnecessary renders (e.g. shouldComponentUpdate).

useCallback(fn, deps) is equivalent to useMemo(() => fn, deps).

# What does React.memo mean?
=> React. memo is a higher order component. If your component renders the same result given the same props, you can wrap it in a call to React. memo for a performance boost in some cases by memoizing the result. This means that React will skip rendering the component, and reuse the last rendered result.

# What is Higher-order Components?
=> A higher-order component (HOC) is an advanced technique in React for reusing component logic. HOCs are not part of the React API, per se. They are a pattern that emerges from React's compositional nature. Concretely, a higher-order component is a function that takes a component and returns a new component.
```js
const EnhancedComponent = higherOrderComponent(WrappedComponent);
```
The examples of HOCs are Redux's connect and Relay's createContainer.

# What are keys in React? Why are keys important?
=> A “key” is a special string attribute you need to include when creating lists of elements in React. Keys are used to React to identify which items in the list are changed, updated, or deleted. In other words, we can say that keys are used to give an identity to the elements in the lists.

# What is reconciliation?
=> React provides a declarative API so that you don't have to worry about exactly what changes on every update. This makes writing applications a lot easier, but it might not be obvious how this is implemented within React.

# Explain life cycle diagram with hooks?
=> ![1_EnuAy1kb9nOcFuIzM49Srw](https://user-images.githubusercontent.com/80479635/166887880-c7143219-cc89-4dac-883b-0611693357c9.png)

# What does the cleanup function in useEffect do?
=> Just like the name implies, the useEffect cleanup is a function in the useEffect Hook that allows us to tidy up our code before our component unmounts. When our code runs and reruns for every render, useEffect also cleans up after itself using the cleanup function.

# What are the rules of hooks?
=> Hooks are a new addition in React 16.8. They let you use state and other React features without writing a class.
