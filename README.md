# javascript-code-test

// Problem 1 - What is the answer
<br /> 
//var answer = 1 + 2 + '3'; <br />
// answer =>  3+ '3' = 33 <br/>
// console.log(answer);

------------------------------------
<br/>
// Problem 2 <br />
// var answer2 = 1 + 2 * '3'; <br/>
// Answer: <br/>
//first multiply the add answer => 1 + 6 = 7<br/>
// console.log(answer2);

 -----------------------------------

// Problem 3 <br/>
// sort members array by age and assign it to sortedMembers <br />
// var members = [ <br/>
//   {name: 'James Doe', age: 27}, <br/>
//   {name: '_Peter Test', age: 25}, <br/>
//   {name: 'Sara Tyler', age: 15}, <br/>
//   {name: 'Tom Bakers', age: 16}, <br />
//   {name: 'verylongnamesnotfit asdewoiasdf', age: 31} <br/>
// ]; <br/>

var sortedMembers = members.slice().sort((a, b) => a.age - b.age);
<br/>
// console.log(sortedMembers);

----------------------------------
<br/>
// Problem 4 <br/>
// deep copy the following array to copiedArray <br/>
// const source = [1,2,3,4]; <br>
<br>
//const copiedArray = source.map(element => {<br/>
    // If the element is an array or an object, perform a deep copy <br>
    //if (Array.isArray(element) || typeof element === 'object') { <br>
        //return JSON.parse(JSON.stringify(element)); <br>
    //} else {<br>
        // Otherwise, simply return the element<br>
       // return element;<br>
   // }<br>
});<br>
<br>
console.log(copiedArray); // Output: [1, 2, 3, 4] <br>
// console.log(copiedArray);<br>

----------------------------------

// Problem 5 <br/>
// // Add id filed for each record and assign the index + 1 <br/>
// // so the new array should be like the following: <br/>
// const newMembers = [ <br/>
//   {id: 1, name: 'James Doe', age: 27}, <br/>
//   {id: 2, name: '_Peter Test', age: 25}, <br/> 
//   {id: 3, name: 'Sara Tyler', age: 15}, <br/>
//   {id: 4, name: 'Tom Bakers', age: 16}, <br/>
//   {id: 5, name: 'verylongnamesnotfit asdewoiasdf', age: 31} <br/>
// ];<br/>
<br/>
const ourMembers = [ <br/>
  {name: 'James Doe', age: 27}, <br/>
  {name: '_Peter Test', age: 25}, <br/>
  {name: 'Sara Tyler', age: 15}, <br/>
  {name: 'Tom Bakers', age: 16}, <br/>
  {name: 'verylongnamesnotfit asdewoiasdf', age: 31} <br/>
]; <br/>

// const newMembers = <br/>
//console.log(newMembers); <br/>
 
-----------------------------------

// Problem 6 <br/>
// function mockServer(name) {
//     return new Promise(function (resolve, reject) {
//         if (name[0] === '_') {
//             reject('name is not correct');
//         } else {
//             resolve('hello world');
//         }
//     });
// }

// // Call mockServer for each name in members, then console.log the response
function getMessage(members) {
  if (name[0] === 'resolve' || age[0] === 'resolve') {
    resolve('name is correct');
  } else {
    rejec
  }
 
}
console.log(getMessage(ourMembers));

 
// Problem 7
// // Create ui using the sortedMembers in Angular and display "Student" if a member is younger than age 18.
// <ul>
//   <li>Name: Sara Tyler</li>
//   <li>Name: James Doe</li>
// </ul>


 

 
// Problem 8
// // Return two indexes of numbers that sum target

// Example 1:
// Input: nums = [2,7,10,9,5,4], target = 9
// Output: [[0,1],[4,5]]

// Example 2:
// Input: nums = [3,2,4], target = 6
// Output: [[1,2]] // not [[0,0],[1,2]]

// Example 3:
// Input: nums = [3,3], target = 6
// Output: [[0,1]]

// function find(arr, target) {
 

// }
