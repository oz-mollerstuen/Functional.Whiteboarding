# Problem 1: Turning Strings to URLs

## Without Recursion:
```
function loopThis(url) {
  let stringArr = [];
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
```
Output: "Jasmine%20Ann%20Jones"
## With Recursion:
```
function replaceSpaces(url, index = 0, stringArr = []) {
  if (index === url.length) {
    return stringArr.join('');
  }
  if (url[index] === ' ') {
    stringArr.push('%20');
  } else {
    stringArr.push(url[index]);
  }
  return replaceSpaces(url, index + 1, stringArr);
}

const result = replaceSpaces('Jasmine Ann Jones');
console.log(result);
```
Output: "Jasmine%20Ann%20Jones"

# Problem 2: Array Deduping

## Without recursion:
```
function removeDuplicates(arr) {
  let uniqueArray = [];
  for (let i = 0; i < arr.length; i++) {
    if (uniqueArray.indexOf(arr[i]) === -1) {
      uniqueArray.push(arr[i]);
    }
  }
  return uniqueArray;
}
console.log(removeDuplicates(7, 9, "hi", 12, "hi", 7, 53))
```

Output: [7, 9, "hi", 12, 53]

#### The -1 in uniqueArray.indexOf(arr[index]) === -1 is used to check if the current element in the input array arr at index index does not exist in the uniqueArray.

#### The indexOf() method returns the first index at which the specified element can be found in the array, or -1 if it is not present. So, if uniqueArray.indexOf(arr[index]) returns -1, it means that the current element arr[index] is not in the uniqueArray, and it can be added to uniqueArray by uniqueArray.push(arr[index]).

## With Recursion:

```
function removeDuplicates(arr, index = 0, uniqueArray = []) {
  if (index === arr.length) {
    return uniqueArray;
  }
  if (uniqueArray.indexOf(arr[index]) === -1) {
    uniqueArray.push(arr[index]);
  }
  return removeDuplicates(arr, index + 1, uniqueArray);
}
console.log(removeDuplicates(7, 9, "hi", 12, "hi", 7, 53))
```
Output: [7, 9, "hi", 12, 53]

## Using a filter:
```
function removeDuplicates(arr) {
  return arr.filter((item, index) => arr.indexOf(item) === index);
}
console.log(removeDuplicates(7, 9, "hi", 12, "hi", 7, 53))
```
Output: [7, 9, "hi", 12, 53]

# Problem 3: Compressing Strings

## Without Recursion:

```
function compressString(str) {
  let result = "";
  let count = 1;
  for (let i = 0; i < str.length; i++) {
    if (str[i] === str[i + 1]) {
      count++;
    } else {
      result += count + str[i];
      count = 1;
    }
  }
  return result;
  console.log(compressString("aaabccdddda"));
}
```

Output: "3ab2c4da"

## With Recursion

```
function compressString(str, index = 0, result = "", count = 1) {
  if (index === str.length) {
    return result;
  }
  if (str[index] === str[index + 1]) {
    count++;
  } else {
    result += count + str[index];
    count = 1;
  }
  return compressString(str, index + 1, result, count);
  console.log(compressString("aaabccdddda"));
}
```

Output: "3ab2c4da"

# Problem 4: Checking for Uniqueness

```
function isUnique(str) {
  for (let i = 0; i < str.length; i++) {
    for (let j = i + 1; j < str.length; j++) {
      if (str[i] === str[j]) {
        return false;
      }
    }
  }
  return true;
}
console.log(isUnique("hello"))
```

Output: false

# Problem 5: Array Sorting

```
function bubbleSort(arr) {
  let swapped;
  for (let j = 0; j < arr.length - 1; j++) {
    swapped = false;
    for (let i = 0; i < arr.length - 1 - j; i++) {
      if (arr[i] > arr[i + 1]) {
        let temp = arr[i];
        arr[i] = arr[i + 1];
        arr[i + 1] = temp;
        swapped = true;
      }
    }
    if (!swapped) break;
  }
  return arr;
}
console.log(bubbleSort(9, 2, 7, 12));
```

Output: [2, 7, 9, 12]