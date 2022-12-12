# Core-Code

<--------- Ensure Questions -------->
const EnsureQuestion = (string) => {
  const stringSplited = string.split('')
  if (stringSplited.slice(-1) == '?'){
    return string
  }
  else{
    return string + '?'
  }
}

<--------- Reversed Words -------->
const reversedWords = (word) => {
  return word.split(' ').reverse())
}

<--------- Reversed Words -------->
const SmallerInteger = (array) =>{
  var n = array[0]
  for (i in array){
    if(array[i] < n){
      n = array[i]
    }
  }
  return n
}

<--------- Reversed Words -------->
const OddOrEven = (array) => {
  var sum = 0;
  if(!array){return 'even'}
  else{
    for (i in array){sum = sum + array[i]}
    if((sum % 2) == 0){return 'even'}
    else{return 'odd'}
  }
}

<--------- Is Palindrome Word? -------->
const IsPalindrome = (string) => {
  if (string.split('').reverse().join('') == string) {
    return true
  } else {
    return false
  }
}

<--------- Well of Ideas -------->
function well(x){
  var goodIdeas = 0;
  for (let i = 0; i < x.length ; i++){
    if (x[i] == "good"){
      goodIdeas = goodIdeas + 1
    }
  }
  if (goodIdeas <= 2){
    if (goodIdeas <= 0){
      return 'Fail!'
    }
    else{
      return 'Publish!'
    }
  }
  else{
    return 'I smell a series!'
  }
}

<--------- React Manage Events - Counter -------->
import React, {useState} from 'react'

const Counter = () => {
  const [counter, setCounter] = useState(0)

  const increment = () => {
    setCounter(counter + 1)
  }
  const decrement = () => {
    setCounter(counter - 1)   
  }
  return (
    <>
      <h1 id='counter'>{counter}</h1>
      <button id='increment' onClick={increment}>Add 1</button>
      <button id='decrement' onClick={decrement}>Rest 1</button>
    </>
  )
}

export default Counter

<--------- Build Search Filter In React -------->
import React, {useState} from 'react'

const SearchBar = () => {
  const fruits = [
    "Apple",
    "Orange",
    "Banana",
    "Cherry",
    "Milk",
    "Peanuts",
    "Butter",
    "Tomato"
  ];
  const [filter, setFilter] = useState(fruits)
  const handleChange = (e) => {
    const query = e.target.value;
    var updatedList = [...fruits];
    updatedList = updatedList.filter((item) => {
      return item.toLowerCase().indexOf(query.toLowerCase()) !== -1;
    });
    setFilter(updatedList);
  };
  return (
    <>
      <div>
        <label>Search: </label>
        <input type="text" placeholder='search...' id='searcher' onChange={handleChange}></input>
      </div>
      <div>
      <ol>
          {filter.map((item, index) => (
            <li key={index}>{item}</li>
          ))}
        </ol>
      </div>
    </>
  )
}

export default SearchBar

<--------- Fetch Random User Data -------->
import React, { useEffect, useState } from 'react'

const RanomUser = () => {

  //Generar un ID aleatorio
  const getRandomInt = (min, max) => {
    min = Math.ceil(min);
    max = Math.floor(max);
    return Math.floor(Math.random() * (max - min) + min);
  }

  //Estados
  const [id, setId] = useState(1)
  const [data, setData] = useState('')

  //Busqueda por ID
  const callList = async () => {
    const response = await fetch(`https://jsonplaceholder.typicode.com/users/${id}`)
    const responseJson = await response.json()
    setData(responseJson)
  }

  //UseEffect para el cambio de ID
  useEffect(() => {
    callList();
  }, [id])

  return (
    <>
      <button onClick={() => setId(getRandomInt(1,10))}>Reset</button>
      <h1>User Data</h1>
      <div>
        <a><strong>Name: </strong></a>
        <a>{data.name}</a>
      </div>
      <div>
        <a><strong>Website: </strong></a>
        <a>{data.website}</a>
      </div>
      <div>
        <a><strong>Email: </strong></a>
        <a>{data.email}</a>
      </div>
      <div>
        <a><strong>Phone: </strong></a>
        <a>{data.phone}</a>
      </div>
    </>
  )
}

export default RanomUser

<--------- React Router Blog -------->
import React from 'react'
import { BrowserRouter, Link, Route, Routes } from 'react-router-dom'

const ReactBlog = () => {
  return (
    <BrowserRouter>
      <div style={{ textAlign: 'center' }}>
        <h1>Daniel's most awesome blog</h1>
        <hr></hr>
        <Routes>
          <Route path='/' element={
            <div>
              <ol>
                <il>
                  <h2><Link to='/React'>React</Link></h2>
                </il>
                <p>Published by 👽 <b>Daniel</b> on 12/12/2022</p>
                <il>
                  <h2><Link to='/Core-Code'>Core Code</Link></h2>
                </il>
                <p>Published by 👽 <b>Daniel</b> on 12/12/2022</p>
                <il>
                  <h2><Link to='/Hello-world'>Hello world</Link></h2>
                </il>
                <p>Published by 👽 <b>Daniel</b> on 12/12/2022</p>
              </ol>
            </div>
          } />
          <Route path='/React' element={
            <div>
              <h2>React</h2>
              <p>Here you can learn to programming logic</p>
              <Link to='/'>👈 Back</Link>
            </div>
          }/>
          <Route path='/Core-Code' element={
            <div>
              <h2>Core Code</h2>
              <p>Core Code rock!!</p>
              <Link to='/'>👈 Back</Link>
            </div>
          }/>
          <Route path='/Hello-world' element={
            <div>
              <h2>Hello World</h2>
              <p>This one was my first post</p>
              <Link to='/'>👈 Back</Link>
            </div>
          }/>
        </Routes>
      </div>
    </BrowserRouter>
  )
}

export default ReactBlog

