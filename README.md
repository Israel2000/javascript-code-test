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
// var members = [ <br/>
//   {name: 'James Doe', age: 27}, <br/>
//   {name: '_Peter Test', age: 25}, <br/>
//   {name: 'Sara Tyler', age: 15}, <br/>
//   {name: 'Tom Bakers', age: 16}, <br />
//   {name: 'verylongnamesnotfit asdewoiasdf', age: 31} <br/>
// ]; <br/>

// // sort members array by age and assign it to sortedMembers <br />
<br /> // Answer: Sort members array by age and assign it to sortedMembers
var sortedMembers = members.slice().sort((a, b) => a.age - b.age);
// var sortedMembers = members : {age.sort(); <br />

// console.log(sortedMembers);

----------------------------------

// Problem 4
// deep copy the following array to copiedArray
// const source = [1,2,3,4];
// const copiedArray =
// console.log(copiedArray);


// Problem 5
// // Add id filed for each record and assign the index + 1
// // so the new array should be like the following:
// const newMembers = [
//   {id: 1, name: 'James Doe', age: 27},
//   {id: 2, name: '_Peter Test', age: 25},
//   {id: 3, name: 'Sara Tyler', age: 15},
//   {id: 4, name: 'Tom Bakers', age: 16},
//   {id: 5, name: 'verylongnamesnotfit asdewoiasdf', age: 31}
// ];

const ourMembers = [
  {name: 'James Doe', age: 27},
  {name: '_Peter Test', age: 25},
  {name: 'Sara Tyler', age: 15},
  {name: 'Tom Bakers', age: 16},
  {name: 'verylongnamesnotfit asdewoiasdf', age: 31}
];

// const newMembers = 
//console.log(newMembers);
 


// Problem 6
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
