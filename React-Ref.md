# React Reference

## Functional Component:
Example:
```
import React from 'react';

export default function App() {
  return (
    <div>
      <h1>My functional code goes here!</h1>
    </div>
  );
}
```

## Class Component:
Example:
```
import React, { Component } from 'react';

class App extends Component {
  
  render() {
    return(
      <div>
        <h1>My Class code goes here!</h1>
      </div>
    )}}

export default App;
```

## Hook Example:
```
// Syntax: const [varName, setVarName] = useState(initialValue)
// create hook (varName) with variable whose state you want to track. You are basically creating a getter
// method.  Use the (setVarName) parameter/method to update the state of varName.  The useState() sets 
// the initial value of varName

const [counter, setCounter] = useState(0)
setCounter(counter + 1)  
```