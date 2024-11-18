# React
### Displaying Data
```react
function App() {
  const name = 'Durga';
  const x = 10;
  const y = 1;
  return (
    <div>
      <h1>Hello {name} </h1>
      <h2>Sum is : {x+y}</h2>
    </div>
  );
}

export default App;
```
- we declare a variable or a value above the return statement and use by the {} this bracket it also do the arithmetic operation like x+y.
```react
function App() {
  const names = ['Durga','Devi','DD','elan','Prakatheesh'];
  return (
    <div className='bg-primary text-customGray p-18 w-custom h-custom'>
      <h1 className='text-5xl'>Hello</h1>
      <ul>
        {names.map((name)=>(
          <li>{name}</li>
        ))}
      </ul>
    </div>
  );
}

export default App;
```
- We use to print the list of elements then using the js map of function we return the li tag to the unordered list.
### Conditional Rendering
In React, there is no special syntax for writing conditions. Instead, you’ll use the same techniques as you use when writing regular JavaScript code. For example, you can use an if statement to conditionally include JSX:
```jsx
import TrueComponent from "./Components/TrueComponent";
import FalseComponent from "./Components/FalseComponent";
function App() {
  
  let content;
  let loggedIn = false;
  
  if(loggedIn)
  {
    content = <TrueComponent />
  }
  else
  {
    content = <FalseComponent />
  }
  return (
    <div>{ content }</div>
  );
}

export default App;
```
- In this code we use the conditional statement We import two components to App.jsx file
- And fixed the loggedIn by false so check the loggedIn value if it is true content will store the truecomponent otherwise it will store the false component.
- Finally we return the content with {} because it is dynamic value.
- in this case content will store the component.
We Also Use the single Line
```jsx
 <div>
    { loggedIn ?(<TrueComponent />) : (<FalseComponent />) }
</div>
```
Dont Need of else part
```jsx
<div>
  { LoggedIn && <AdminPanel />}
</div>
```
### Rendering List
```jsx
function App() {
  const list = ['Durga','Devi','Devi Devi'];

  const list_li = list.map((ele)=>
    <button>{ele}</button>
  )
  return (
    <div>
      <ul> {list_li} </ul>
    </div>
  );
}
export default App;
```
- In this code list of element
- We return the unordered list. So using the map function we create a array of list and return it to the unordered list.
```jsx
function App()
{
  const products = ["Durga","Devi","DD","ES","esdurga"];
  const ListItems = products.map(product=>
     <li>{product}</li>
  )
  return(
    <ul>{ListItems}</ul>
  )

}

export default App;
```
- In this code we render the list of element.
- So how we acheive is to declare a list of elements named products.
- Then in the return statement we return the unorderd list that unordered list will have the list of elements.
- That list will get from the list of elements we already declare.
- So create the the element called ListItems that will get the each product from the products list that product will convert it into list using <li></li>
We also form like the below one
```jsx

function App()
{
  const products = [
    {id:1,head:"Durga"},
    {id:2,head:"Devi"},
    {id:3,head:"Dd"},
    {id:4,head:"esDurga"},
    {id:5,head:"ES"},
  ];
  const ListItems = products.map(product=>
     <li>{product.head}{product.id}</li>
  )
  return(
    <ul>{ListItems}</ul>
  )

}

export default App;
```
### UseState
```jsx
import React from "react";
import { useState } from 'react'
function App()
{
  const [name , setName] = useState('Durga');
  function change()
  {
     setName('Devi');
  }
  return(
    <div>
      <h1>Hello.....{name} !</h1>
      <button onClick = {change}>Click me</button>
    </div>
  )
}

export default App;
```
- In this code we use use state to handle the event.
- First we declare a usestate variable that is const [name , setName] = usestate('durga') the durga is the initial usestate value.
- If we click the button that button will call the function change() that function will set the name as devi.
- We coutn the button click also.
- Whenever we click the button the comopnent will re-render with the new name value that is setName of value.
