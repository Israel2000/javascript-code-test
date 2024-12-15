# Full-Stack Interview Q&A

### Angular FAQs

1. **What are directives?**
   Directives add behavior to an existing DOM element or component instance. There are mainly three kinds of directives:
   
   - **Components**: Directives with a template.
   - **Structural directives**: Change the DOM layout by adding or removing elements.
   - **Attribute directives**: Change the appearance or behavior of an element, component, or another directive.

2. **What is the purpose of the *ngFor directive?**
   The Angular *ngFor directive iterates over a list of items and displays them in the template. Example:

   ```html
   <li *ngFor="let user of users">
     {{ user }}
   </li>
   ```
   Here, `user` is a template input variable used for each iteration.

3. **What is the purpose of the *ngIf directive?**
   The *ngIf directive conditionally includes or excludes elements in the DOM based on a truthy/falsy condition. Example:

   ```html
   <p *ngIf="user.age > 18">You are not eligible for a student pass!</p>
   ```
   Angular adds or removes the paragraph element from the DOM for improved performance.

4. **What are lifecycle hooks available in Angular?**
   Angular components have a lifecycle, with various hooks available:

   - `ngOnChanges`: Called when data-bound properties change.
   - `ngOnInit`: Called after the first display of data-bound properties.
   - `ngDoCheck`: Detects and acts on changes not detected automatically.
   - `ngAfterContentInit`: Triggered after Angular projects external content.
   - `ngAfterContentChecked`: Called after checking projected content.
   - `ngAfterViewInit`: Triggered after initializing the component’s views and child views.
   - `ngAfterViewChecked`: Called after checking the component’s views and child views.
   - `ngOnDestroy`: Used for cleanup before Angular destroys a component.

5. **What is data binding?**
   Data binding facilitates communication between a component and the DOM. Angular supports four forms:

   - **Interpolation**: Adds property values from the component using `{{ value }}`.
     ```html
     <li>Name: {{ user.name }}</li>
     ```
   - **Property Binding**: Passes values from the component to HTML attributes.
     ```html
     <input type="email" [value]="user.email">
     ```
   - **Event Binding**: Listens to DOM events and calls component methods.
     ```html
     <button (click)="logout()">Logout</button>
     ```
   - **Two-Way Binding**: Synchronizes data between the DOM and the component.
     ```html
     <input type="email" [(ngModel)]="user.email">
     ```

6. **What is Angular CLI?**
   Angular CLI (Command Line Interface) helps scaffold and build Angular apps efficiently. Install it via:

   ```bash
   npm install -g @angular/cli
   ```

7. **Difference between constructor and ngOnInit:**

   - **Constructor**: Initializes class members and sets up dependency injection. Avoid performing heavy tasks here.
   - **ngOnInit**: Called after Angular initializes the component. Suitable for logic initialization and binding resolution.

8. **What is a service?**
   A service encapsulates common functionality and promotes reusability across modules. Example:

   ```typescript
   @Injectable({
     providedIn: 'root',
   })
   export class MyService {}
   ```

9. **What is dependency injection in Angular?**
   Dependency Injection (DI) is a design pattern where a class receives its dependencies externally instead of creating them itself. Angular’s DI framework resolves services and other objects throughout the application.

10. **What are pipes?**
    Pipes transform data in templates. Example:

    ```typescript
    @Component({
      template: `<p>Birthday is {{ birthday | date }}</p>`
    })
    export class BirthdayComponent {
      birthday = new Date(1987, 6, 18);
    }
    ```

11. **Difference between pure and impure pipes:**

    - **Pure pipes**: Triggered only when input values or references change.
    - **Impure pipes**: Called on every change detection cycle, even if inputs remain unchanged.

12. **What are observables?**
    Observables provide a mechanism for asynchronous programming and event handling, supporting multiple values over time. They are declarative and require subscription.

    Example:

    ```typescript
    import { Observable } from 'rxjs';

    const observable = new Observable(subscriber => {
      subscriber.next('Hello');
      subscriber.complete();
    });

    observable.subscribe(console.log);
    ```

13. **What is RxJS?**
    RxJS is a library for reactive programming with Observables, supporting operators for composing asynchronous streams. Example usage with `HttpClient`:

    ```typescript
    import { catchError, retry } from 'rxjs/operators';
    ```

14. **Difference between promise and observable:**

| Feature           | Observable                | Promise              |
|-------------------|---------------------------|----------------------|
| Execution         | Lazy (starts on subscribe)| Eager (executes immediately)|
| Values            | Emits multiple values     | Emits a single value |
| Error Handling    | Uses `subscribe`          | Uses `.catch()`      |
| Chaining          | Rich operators            | Limited `.then()`    |

15. **What is Angular Router?**
    Angular Router facilitates navigation between views in single-page applications (SPAs). Example of lazy loading:

    ```typescript
    const routes: Routes = [
      {
        path: 'customers',
        loadChildren: () => import('./customers/customers.module').then(m => m.CustomersModule)
      },
    ];
    ```

16. **What are the different types of compilation in Angular?**

    - **JIT (Just-in-Time)**: Compiles in the browser at runtime.
    - **AOT (Ahead-of-Time)**: Compiles during the build process for improved performance and smaller bundle sizes.

17. **What is lazy loading?**
    Lazy loading loads feature modules asynchronously when required, improving performance. Example:

    ```typescript
    {
      path: 'orders',
      loadChildren: () => import('./orders/orders.module').then(m => m.OrdersModule)
    }
    ```

18. **What is TestBed in Angular?**
    TestBed is an API for unit testing Angular components and services. It simplifies injection, asynchronous behavior, and DOM interactions during tests.

19. **What are reactive and template-driven forms?**

| Feature              | Reactive Forms           | Template-Driven Forms |
|----------------------|--------------------------|------------------------|
| Model Setup          | Explicitly defined       | Defined in template   |
| Data Updates         | Synchronous             | Asynchronous          |
| Validation           | Defined in component    | Defined in template   |
| Scalability          | Highly scalable         | Suitable for simple forms |

20. **What is the difference between ngOnChanges and ngDoCheck?**

    - `ngOnChanges`: Detects changes in input-bound properties.
    - `ngDoCheck`: Custom change detection logic for detecting changes not tracked by Angular.

21. **What is the purpose of the common module?**
    The `@angular/common` module provides essential pipes, directives, and services like `ngIf`, `ngFor`, and `HttpClientModule`. It is a foundational module in Angular projects.


22. **What is a standalone component?**
A standalone component is a type of component that is not part of any Angular module. It provides a simplified way to build Angular applications.
23. **What are Angular Signals?**
A signal is a wrapper around a value that can notify interested consumers when that value changes. Signals can contain any value, from simple primitives to complex data structures.
24. **ViewChildren** - Purpose: Allows you to access multiple child components, directives, or DOM elements within a view.
Usage:Use it when querying for a collection of elements or components.
25. **ViewChild**
26. **HTTPCalls** are used to interact with REST APIs or other HTTP services. The HttpClient module, provided by Angular, makes it easy to perform GET, POST, PUT, DELETE, and other HTTP requests.
27. **ng-template** - The <ng-template> directive in Angular defines a template that is not rendered by default but can be programmatically inserted into the DOM. It is typically used for structural directives and dynamic content.
28. **ng-content** - The <ng-content> directive is used to project content from a parent component into a child component. This is part of Angular's Content Projection mechanism.
Key Features: Facilitates reusable components that accept dynamic content.
Supports multiple content projection with selectors.
29. **The @HostListener decorator** in Angular is used to listen to and handle events on the host element of a directive or component. It's part of Angular's host binding capabilities, enabling you to respond to user interactions or browser events directly on the host element.

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
