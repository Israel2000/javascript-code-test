# Full-Stack Interview Q&A

## Angular

## React

## JavaScript Coding

### Problem 1 - What is the answer
```javascript
var answer = 1 + 2 + '3'; 
// answer => 3 + '3' = 33
console.log(answer);
```

---

### Problem 2
```javascript
var answer2 = 1 + 2 * '3'; 
// Answer:
// First multiply, then add
// 1 + 6 = 7
console.log(answer2);
```

---

### Problem 3
Sort `members` array by age and assign it to `sortedMembers`:
```javascript
var members = [
  {name: 'James Doe', age: 27},
  {name: '_Peter Test', age: 25},
  {name: 'Sara Tyler', age: 15},
  {name: 'Tom Bakers', age: 16},
  {name: 'verylongnamesnotfit asdewoiasdf', age: 31}
];

var sortedMembers = members.slice().sort((a, b) => a.age - b.age);
console.log(sortedMembers);
```

---

### Problem 4
Deep copy the following array to `copiedArray`:
```javascript
const source = [1, 2, 3, 4];

const copiedArray = source.map(element => {
  // If the element is an array or an object, perform a deep copy
  if (Array.isArray(element) || typeof element === 'object') {
    return JSON.parse(JSON.stringify(element));
  } else {
    // Otherwise, simply return the element
    return element;
  }
});

console.log(copiedArray); // Output: [1, 2, 3, 4]
```

---

### Problem 5
Add `id` field for each record and assign the index + 1:
```javascript
const ourMembers = [
  {name: 'James Doe', age: 27},
  {name: '_Peter Test', age: 25},
  {name: 'Sara Tyler', age: 15},
  {name: 'Tom Bakers', age: 16},
  {name: 'verylongnamesnotfit asdewoiasdf', age: 31}
];

const newMembers = ourMembers.map((member, index) => ({
  id: index + 1,
  ...member
}));

console.log(newMembers);
```

---

### Problem 6
Mock server example and handling errors:
```javascript
function mockServer(name) {
  return new Promise(function (resolve, reject) {
    if (name[0] === '_') {
      reject('name is not correct');
    } else {
      resolve('hello world');
    }
  });
}

// Call mockServer for each name in members, then console.log the response
function getMessage(members) {
  members.forEach(member => {
    mockServer(member.name)
      .then(response => console.log(response))
      .catch(error => console.log(error));
  });
}

getMessage(ourMembers);
```

---

### Problem 7
Create UI using `sortedMembers` in Angular and display "Student" if a member is younger than age 18:
```html
<ul>
  <li *ngFor="let member of sortedMembers">
    Name: {{ member.name }}
    <span *ngIf="member.age < 18"> - Student</span>
  </li>
</ul>
```

---

### Problem 8
Return two indexes of numbers that sum to the target:
```javascript
function findIndexes(nums, target) {
  const result = [];
  const map = new Map();

  nums.forEach((num, index) => {
    const complement = target - num;
    if (map.has(complement)) {
      result.push([map.get(complement), index]);
    }
    map.set(num, index);
  });

  return result;
}

// Example Usage
console.log(findIndexes([2, 7, 10, 9, 5, 4], 9)); // Output: [[0, 1], [4, 5]]
console.log(findIndexes([3, 2, 4], 6));          // Output: [[1, 2]]
console.log(findIndexes([3, 3], 6));             // Output: [[0, 1]]
