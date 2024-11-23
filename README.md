# React
### Displaying Data
```jsx
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
```jsx
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
### UseEffect
- Use effect is a react Hook.
- Use Effect function will call every rendering.
```jsx
  useEffect(() => {
        console.log('UseEffect1');
    },[]);
```
- In the above function we will inspect the page the useeffect1 will print the first time that is the initial time the component will render so whenever the component is render the useffect function will run.
- When we make any changes in the component that is delete the blog like that did not show any thing the first render only show.
### useEffect Dependies
```jsx
  useEffect(() => {
        console.log('UseEffect1');
    },[console.log('UseEffect2')]);
```
- In this code whenever we delete the blog or we make any changes in the componenet that time useEffect2 will run.
- Whenever the component run the dependency will print then the useeffect2 will print when we delete the blog that time useeffect2 will run.
- The conclusion is **Inside the useEffect function runs only ones that is the initial rendering of the component but the outside the dependencies run every component change**
### UseEffect:
#### asynchronus operation:
-An asynchronous operation in computing refers to a process that occurs independently of the main program flow. Rather than waiting for the operation to complete before moving on to the next task, the main program continues to run and handles the results when the operation is finished. This is particularly useful for tasks that take some time to complete, such as fetching data from the internet, reading from a file, or interacting with a database.
**Key Features of Asynchronous Operations:**
- Non-Blocking: The main program doesn't stop or wait for the asynchronous operation to complete. Instead, it can continue executing other tasks, which makes the program more efficient and responsive.
- Concurrency: Allows multiple operations to be executed simultaneously, improving performance, especially in applications that involve I/O-bound tasks.
- Callbacks, Promises, and Async/Await: Common mechanisms to handle asynchronous operations in JavaScript and other languages.
Example
```jsx
// Asynchronous function using async/await
async function fetchData() {
  try {
    const response = await fetch('https://api.example.com/data'); // Asynchronous operation
    const data = await response.json(); // Waits for response to be parsed
    console.log(data);
  } catch (error) {
    console.error('Error fetching data:', error);
  }
}

fetchData(); // Function call
```
**Our Program**
```jsx
useEffect(() => {
        fetch('http://localhost:8000/blogs')
        .then(res =>{
            return res.json();
        })
        .then((data) => {
            console.log(data);
        })
    },[]);
```
First when the swebsite run behind the scene it will fetch the data from the json server that is our local json server that will give the response so we get the response and then print the data. In this [] array is a dependency so that will run only once.
- Inside the then function using the setBlogs method data will assigned but we blindly do that the error will occur because in the initialization of the use state we pass the null value
```jsx
const [blogs , setBlogs] = useState(null);
```
So after that it will immediatly try to map the blogs using map function beacuse we pass the blogs data as a props so it will try to map like the below code
```jsx
function BlogList(props)
{
    const blogs = props.blogs;
    const title = props.title;
    return(
    <div className="blog-list">
      <h1>{ title }</h1>
      {blogs.map((blog) => (
        <div className="blog-preview" key={blog.id}>
          <h2>{ blog.title }</h2>
          <p> Written By {blog.author} </p>
          <h4> { blog.body } </h4>
          <button onClick = {()=>props.Delete(blog.id)}>Delete Blog</button>
        </div>
      ))}
    </div>
    )
}
```
- So it will produce a error we prevent this we load the data only if the blogs have not the null value using the below code
```jsx
 {blogs && <BlogList blogs={blogs} title={"All Blogs!"} Delete={Delete} />}
```
- This line error freely run it will check and then run. This is called conditional template. the && will evaluate the lett that is true then do the right side.
One Important Note:
- If we use setTimeout function that will not stop the entire program that will stop inside of the block the after blocks are continously run.
Example:
```jsx
const [blogs , setBlogs] = useState(null);
    useEffect(() => {
        fetch('http://localhost:8000/blogs')
        .then(res =>{
            return res.json();
        })
        .then((data) =>{
            setTimeout(() => { setPending(false); }, 3000);
            setBlogs(data);
        })
    },[]);
    return(
        <div>
            {pending && <h1>loading...</h1>}
            {blogs && <BlogList blogs={blogs} title={"All Blogs!"} Delete={Delete} />}
        </div>
    )
```
- In the above code inside the use effect function we fetch the data and store the data after the setTimeout function so that the function will wait for 3 seconds.
- But the becoming function not wait for any one it will continously run and assign the data value using the setBlogs function in the return function loading message will shown untill the pending will false but the pending will stop after 3 seconds.
- And the blog will show when the data to be initialized that is not null.
- so in the web page both are shown load will gone after the 3 seconds.
![image](https://github.com/user-attachments/assets/6d8fd4a0-d3a3-479a-a93b-ace103a5cc77)
- But incase of we use the conditional rendering that is when the pending is true that is load will gone that time blog will display like 3 seconds loading and then blogs.
```jsx
{pending ? ( <p>Loading...</p> ) : ( <BlogList blogs={blogs} title={"All Blogs!"} Delete={Delete} />)}
```
[![Watch the video](https://img.youtube.com/vi/VIDEO_ID/hqdefault.jpg)](https://github.com/user-attachments/assets/3a7e5edc-0509-45ed-b201-a5dbc7454a0b)
- Other wise we fetch the data inside the setTimeout function.
### Eroor Handling
- We handle the error like if the data is not availbale or else the data base or the server is not availbale that time we found an error
- So what we do is catch the error and print the error message

