# React
### Values:
```react
function App() {
  const name = 'Durga';
  const x = 10;
  const y = 1;
  return (
    <div className='bg-primary text-customGray p-18 w-custom h-custom'>
      <h1 className='text-5xl'>Hello {name} </h1>
      <h2>Sum is : {x+y}</h2>
    </div>
  );
}

export default App;
```
- we declare a variable or a value above the return statement and use by the {} this bracket it also do the arithmetic operation like x+y.
### List of Names:
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
### Ternary operator
```react
function App() {
  const names = ['Durga','Devi','DD','elan','Prakatheesh'];
  const log = false;
  return (
    <div className='bg-primary text-customGray p-18 w-custom h-custom'>
      <h1 className='text-5xl'>Hello</h1>
      <ul>
        {names.map((name)=>(
          <li>{name}</li>
        ))}
      </ul>
      { log ? <h1>Hello</h1> : <h1>Welcome</h1> }
    </div>
  );
}

export default App;
```
-  { log && <h1>Hello</h1> } without else part (:)
-  We add css property in inline inside the tag style = {{}} inside of the double bracket add the css like color font size.
- Example : <ul style = {{color:'burlywood', fontSize:'50px', fontWeight:'1000', fontStyle:'revert-layer'}}>
