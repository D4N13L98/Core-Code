# Core-Code

<--------- Ensure Questions -------->
const EnsureQuestion = (string) => {
  const stringSplited = string.split('')
  if (stringSplited.slice(-1) == '?'){
    console.log(string)
  }
  else{
    console.log(string + '?')
  }
}

<--------- Reversed Words -------->
const reversedWords = (word) => {
  console.log(word.split(' ').reverse())
}

<--------- Reversed Words -------->
const SmallerInteger = (array) =>{
  var n = array[0]
  for (i in array){
    if(array[i] < n){
      n = array[i]
    }
  }
  console.log(n)
}

<--------- Reversed Words -------->
const OddOrEven = (array) => {
  var sum = 0;
  if(!array){console.log('even null')}
  else{
    for (i in array){sum = sum + array[i]}
    if((sum % 2) == 0){console.log('even')}
    else{console.log('odd')}
  }
}
