#Getting Started With Redux
---

###What is the first principle of Redux?
Whether your app is simple or super complex, you need to represent whole state of your app as a **single** JavaScript object.

All mutations or change of state are explicit. So it is possible to keep track of all of them.

Note: for simple examples in the course, Dan represented state by a number/array instead of an object.

###What is the second principle of Redux?
State tree is **read only**. You cannot modify or write to it.

Anytime you want to change the state, you need to dispatch an action. An action is a plain JavaScript object describing the change.
 
###What is the third principle of Redux?
To describe state mutations, you have to write a function that takes previous state of the app, the action being dispatched and returns the next state of the app. And this function has to be pure. This function is called the **reducer**.

###What is an action?
An action is a plain JavaScript object describing the change. Just like the state is the minimal representation of data in your app, an action is minimal representation of the change to that data.

Structure of the action object is up to you. The only requirement is that it should have a `type` property (which is not undefined). Recommended format of `type` property is string because strings are serializable.

###What are pure functions?

- Pure functions are functions whose return value depends solely on the value of their arguments.
- Pure functions do not have any observable side effects such as network or database calls.
- If you pass in the same set of arguments, then you are going to get the same return value.
- Pure function do not modify the values passed to them.

###What happens when you pass an undefined state to the reducer?
It returns initial state of the application by convention.

###What are the three methods avilable on a Redux store?
- `getState`: to get the current state.
- `dispatch`: to dispatch an action to modify state.
- `subscribe`: it lets you register a callback that the redux will call anytime an action has been dispatched. 

```
// retucer function
const counter = (state = 0, action) => {
  switch(action.type) {
    case 'INCREMENT':
      return state + 1;
    case 'DECREMENT':
      return state - 1;
    default:
      return state;
  }
}

// below is equivalent to var createStore = Redux.createStore;
const { createStore } = Redux; // importing createStore function from Redux
const store = createStore(counter); // counter is the reducer function

console.log(store.getState());

store.dispatch({ type: 'INCREMENT'});
console.log(store.getState());

const render = () => {
  document.body.innerText = store.getState();
}

store.subscribe(render);
render();

document.addEventListener('click', () => {
  store.dispatch({type: 'INCREMENT'});
});
```

###What does `combineReducers` do?
It is a utility function that helps you combine different reducers and make a top level reducer out of them.

Only argument to `combineReducers` is an object that contains the mapping between state key names and the reducers managing them.

Convention is to keep name of reducers and state key names same.

###What is an easy way to pass store to child components?
Through `getChildContext`. It will pass store to children and grand-children components.

To make it work you need to define `childContextTypes` property on the component that defines `getChildContext`.

`context` is opt-in for the receiving components, so you need to specify special field called `contextTypes` to define which contexts we want to receive.

This feature is inbuilt in `react-redux`, which are React bindings for Redux library.

###What are action creators?
It is a function that takes some arguments about the action and it returns the action object.