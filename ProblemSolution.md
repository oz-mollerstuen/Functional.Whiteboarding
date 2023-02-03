
problem 1:

input Jasmine Ann Jones
output "Jasmine%20Ann%20Jones"

function loopThis(url) {
	let stringArr = []
  for(let i = 0; i < url.length; i++)
  {
  if(url[i] === " "){
  	stringArr.push('%20');
  }
  else
  {
  stringArr.push(url[i]);
  }
  }
  return(stringArr.join(''))
}
const doThis = loopThis('Jasmine Ann Jones');
console.log(doThis("Jasmine Ann Jones"));

Output: "Jasmine%20Ann%20Jones"


function replaceSpaces(url, index = 0, stringArr = []) {
	if(index === url.length) {
  return stringArr.join('')
  }
  	if(url[index] === ' ') {
  	stringArr.push('%20');
    } else {
    stringArr.push(url[index]);
    }
    return replaceSpaces(url, index +1, stringArr);
  }
const result = replaceSpaces('Jasmine Ann Jones');
console.log(result);

output: "Jasmine%20Ann%20Jones"