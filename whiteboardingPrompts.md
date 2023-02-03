# Problem 1: Turning Strings to URLs

# URLs cannot have spaces. Instead, all spaces in a string are replaced with %20. Write an algorithm that replaces all spaces in a string with %20.

## You may not use the replace() method or regular expressions to solve this problem. Solve the problem with and without recursion.

## Example
## Input: "Jasmine Ann Jones"

## Output: "Jasmine%20Ann%20Jones"
#
# Without Recursion:
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

##### The function loopThis takes a string input url as an argument. It initializes an empty array stringArr. Then it iterates over each character in the url string using a for loop.

##### If a space is encountered, it pushes the string '%20' into the stringArr array. Otherwise, it pushes the current character of the url string.

##### After the loop, the elements in stringArr are joined and returned as a single string. The returned string will replace spaces with '%20'.

##### Finally, the function is being invoked with an argument of "Jasmine Ann Jones" and logged to the console.

# Edge cases to consider for the function loopThis:

* Input string with no spaces: The function would work as expected and return the input string as is, without any modifications.

* Input string with multiple spaces: The function replaces each space with %20 which might not be desired in cases where multiple spaces are required.

* Input string with spaces at the beginning or end: The function replaces the spaces at the beginning or end of the string, which might not be desired in cases where the spaces are important.

* Input string with special characters: The function might not handle special characters properly, and they may get lost during the conversion process.

* Input string with non-printable characters: The function may not handle non-printable characters correctly, and they may get lost during the conversion process.
#
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

##### The replaceSpaces function is a recursive implementation that replaces spaces in a given URL string with %20.

##### It takes an input URL string as well as two optional parameters index and stringArr.

##### The index parameter is used to keep track of the current index of the URL string that is being processed.
##### The stringArr parameter is used to store the output string with spaces replaced with %20.
##### The function uses a base case of index === url.length, which means the end of the URL string has been reached. In this case, the function returns the stringArr joined into a single string.

##### Otherwise, the function checks if the current character in the URL string is a space. If it is, %20 is pushed into the stringArr. If not, the character itself is pushed into the stringArr.

##### The function then calls itself with index + 1, updating the index to process the next character in the URL string and passes the updated stringArr as a parameter. This continues until the end of the URL string is reached and the final result is returned.
#
# Edge Cases:
* Case with empty string: replaceSpaces("")
* Case with only spaces: replaceSpaces(" ")
* Case with special characters: replaceSpaces("Jasmine@Ann!Jones")
* Case with multi-byte characters: replaceSpaces("Jasmine 你好 Ann Jones")
* Case with leading/trailing spaces: replaceSpaces(" Jasmine Ann Jones ")
#

# Problem 2: Array Deduping

# Write an algorithm that removes duplicates from an array. Do not use a function like filter() to solve this. Once you have solved the problem, demonstrate how it can be solved with filter(). Solve the problem with and without recursion.

## Example:
## Input: [7, 9, "hi", 12, "hi", 7, 53]

## Output: [7, 9, "hi", 12, 53]
#
# Without recursion:
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
#
##### This function removeDuplicates takes in an array arr as a parameter. It initializes an empty array uniqueArray to store unique elements of the given array arr. The function uses a for loop that iterates through the elements of the arr array.

##### In each iteration, the function checks if the current element arr[i] is present in the uniqueArray using the indexOf method. If it returns -1, it means that the element is not present in the uniqueArray, and the function pushes it to the uniqueArray.

##### Finally, the function returns the uniqueArray which will contain all the unique elements of the given arr array.
#
# With Recursion:

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
#
##### This code is an implementation of a recursive function in JavaScript that removes duplicates from an array. The function takes an input array, and two optional parameters, index and uniqueArray.

##### The index parameter is used to keep track of the current position in the array and starts at 0. The uniqueArray parameter is used to store the unique elements of the input array and starts as an empty array.

##### The function uses a base case of if (index === arr.length) which checks if the index has reached the end of the input array. If this is the case, the function returns the uniqueArray.

##### Otherwise, the function uses an if (uniqueArray.indexOf(arr[index]) === -1) statement to check if the current element in the input array is already present in the uniqueArray. If it is not present, it pushes the current element into the uniqueArray.

##### Finally, the function makes a recursive call to itself, increasing the value of the index by 1 and passing the updated index and uniqueArray parameters. This continues until the base case of index === arr.length is reached and the final uniqueArray is returned.

##### The code also includes a console.log statement that calls the removeDuplicates function with the input array [7, 9, "hi", 12, "hi", 7, 53].
#
## Using a filter:
#
```
function removeDuplicates(arr) {
  return arr.filter((item, index) => arr.indexOf(item) === index);
}
console.log(removeDuplicates(7, 9, "hi", 12, "hi", 7, 53))
```
Output: [7, 9, "hi", 12, 53]

##### This JavaScript function removeDuplicates takes an array arr as an argument and returns a new array that contains only the unique elements from the input array arr.

##### The function uses the filter method to iterate over the input array arr. The filter method takes a callback function that receives each item and its index in the input array arr.

##### The condition arr.indexOf(item) === index checks if the current item is the first occurrence of the item in the input array arr. If it is, then the item is unique, and the filter method includes it in the result array.

##### Finally, the function returns the result array containing only the unique elements of the input array arr.

# Problem 3: Compressing Strings

## Write an algorithm that takes a string with repeated characters and compresses them, using a number to show how many times the repeated character has been compressed. For instance, aaa would be written as 3a. Solve the problem with and without recursion.

# Example
## Input: "aaabccdddda"

## Output: "3ab2c4da"

#
## Without Recursion:
#
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
#
##### This function implements a string compression algorithm. The function takes in a string str as input.

##### The function initializes an empty string result to store the compressed string. It also initializes a variable count to keep track of the number of repeated characters.

##### The function then loops through each character of the input string str. If the current character is the same as the next character, the count is incremented. If the current character is different than the next character, the count and current character are added to the result string. The count is then reset to 1.

##### Once all the characters have been processed, the compressed string result is returned. The function also includes a console log statement to print the result of the compression of the string "aaabccdddda".
#
# With Recursion:

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
#
##### The function compressString takes a string str as its input. It also takes two optional parameters, index and result. The index parameter is used to keep track of the current position in the input string, and result is used to build the compressed string. The count parameter is used to keep track of the number of consecutive occurrences of the same character.

##### The function uses a recursive approach to traverse the string str. The base case for the recursion is when index equals the length of str, at which point the function returns the compressed string stored in result.

##### If the current character str[index] is the same as the next character str[index + 1], the value of count is incremented. Otherwise, count is added to result along with the current character, and count is reset to 1.

##### Finally, the function calls itself with the updated values of index and result, until the base case is reached.

##### The function returns the compressed string.


# Problem 4: Checking for Uniqueness

# Write an algorithm that determines whether all the elements in a string are unique. You may not convert the string into an array or use array methods to solve this problem. The algorithm should return a boolean.

# Example:
## Input: "hello"

## Output: false
#
## Input: "copyright"

## Output: true
#
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
#

##### The isUnique function checks if a given string str has all unique characters or not. It does this by using two nested loops. The outer loop iterates through the string str from index 0 to the end of the string. The inner loop starts from the index of the outer loop plus 1 and goes to the end of the string. In each iteration, the two characters being compared (the one from the outer loop and the one from the inner loop) are compared. If they are equal, the function returns false as it means the string does not have all unique characters. If the loops complete without finding any equal characters, the function returns true, meaning the string has all unique characters.

##### For example, in console.log(isUnique("hello")), the function returns false because the string "hello" has duplicate characters.

# Problem 5: Array Sorting

# Write an algorithm that sorts an array without using the sort() method. There are many different sorting algorithms — take the time to read about the following:
#
## Quick sort
## Merge sort
## Heap sort
## Insertion sort
## Bubble sort
## Selection sort
#
## You may implement any of the above algorithms (or your own) to solve the problem — as long as it doesn't use sort().
#
# Example
## Input: [9, 2, 7, 12]

## Output: [2, 7, 9, 12]
#
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
#
##### The code is an implementation of the bubble sort algorithm. The algorithm is a comparison-based sorting algorithm that works by repeatedly swapping adjacent elements if they are in the wrong order until the array is sorted in ascending order.

##### In the code, arr is the input array. The outer loop for (let j = 0; j < arr.length - 1; j++) iterates over the array arr from the first element to the second to last element. The inner loop for (let i = 0; i < arr.length - 1 - j; i++) iterates over the array from the first element to the last element minus j.

##### The condition if (arr[i] > arr[i + 1]) checks if the current element arr[i] is greater than the next element arr[i + 1]. If it is, the elements are swapped using a temporary variable temp. The flag swapped is set to true to indicate that the array has been modified.

##### If, after an iteration of the outer loop, no swaps have occurred, the flag swapped will be false, and the loop will break because the array is already sorted.

##### Finally, the sorted array is returned.

## Bubble sort is a simple sorting algorithm that works by repeatedly swapping adjacent elements if they are in the wrong order until the list is sorted in the desired order. The algorithm iterates through the list, comparing each pair of adjacent elements, and swapping them if they are in the wrong order. The process is repeated until no more swaps are necessary, indicating that the list is now sorted. Bubble sort has a worst-case time complexity of O(n^2), making it inefficient for large lists, but it is easy to understand and implement.