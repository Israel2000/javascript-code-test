# Full-Stack Interview Q&A

### Angular FAQs

### 1. **What are directives?**
   Directives add behavior to an existing DOM element or component instance. There are mainly three kinds of directives:
   
   - **Components**: Directives with a template.
   - **Structural directives**: Change the DOM layout by adding or removing elements. (eg. ngIf, ngFor...)
   - **Attribute directives**: Change the appearance or behavior of an element, component, or another directive. (eg. ngClass, ngStyle...)
**Control Flow Template** - build-in control flow for the template in angular 17.
   - this is the replacement of structural directive.
   - Syntax @if, @else, @for, and @switch
     
### 2. **What are lifecycle hooks available in Angular?**
   Angular components have a lifecycle, with various hooks available:

   - `ngOnChanges`: Called when data-bound properties change.
   - `ngOnInit`: Called after the first display of data-bound properties.
   - `ngDoCheck`: Detects and acts on changes not detected automatically.
   - `ngAfterContentInit`: Triggered after Angular projects external content.
   - `ngAfterContentChecked`: Called after checking projected content.
   - `ngAfterViewInit`: Triggered after initializing the component’s views and child views.
   - `ngAfterViewChecked`: Called after checking the component’s views and child views.
   - `ngOnDestroy`: Used for cleanup before Angular destroys a component.

### 3. **What is data binding?**
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
      **Passing Data from one component to another**    
      - @Input - Parent to Child.
      - @output - Child to Parent via @output decorator and EventEmmiter
      - @ViewChild - Child to Parent
      - Parent components can access child components' methods or properties directly using @ViewChild.
      - For communication between a parent and its projected content (child elements projected using <ng-content>).
      **Complex State Management or Data Sharing**
       you can use **NGRX Store** or **BehaviorSubject** to maintain a shared state across components.

      **Example Using `BehaviorSubject`**

         ```typescript
         import { Injectable } from '@angular/core';
         import { BehaviorSubject } from 'rxjs';
         
         @Injectable({ providedIn: 'root' })
         export class StateService {
           private stateSource = new BehaviorSubject<string>('Initial State');
           currentState$ = this.stateSource.asObservable();
         
           updateState(newState: string) {
             this.stateSource.next(newState);
           }
         }
     ```

### 4. **What is Angular CLI?**
   Angular CLI (Command Line Interface) helps scaffold and build Angular apps efficiently. Install it via:

  

### 5. **Difference between constructor and ngOnInit:**

   - **Constructor**: Initializes class members and sets up dependency injection. Avoid performing heavy tasks here.
   - **ngOnInit**: Called after Angular initializes the component. Suitable for logic initialization and binding resolution.

### 6. **What is a service?**
   -is a class that provides reusable logic, data sharing, or functions that can be used across multiple components, directives,
   or other services. Services help encapsulate business logic and improve the modularity and maintainability of the application.

      ```typescript
      @Injectable({
        providedIn: 'root',
      })
      export class MyService {}
      ```
   When to Use a Service?
   To fetch or manipulate **data** (e.g., HTTP API calls).
   To **share data** between components.
   To perform **utility functions** (e.g., logging, validation).
   To manage **state**.
   To separate business logic from the component.

### 7. **What is dependency injection?**
   - Dependency Injection (DI) is a design pattern where a class receives its dependencies externally instead of creating them itself.
   - Angular’s DI framework resolves services and other objects throughout the application.
      I.   Dependencies: Services, objects, or values that a class requires to function.
      II.  Injector: The mechanism in Angular that knows how to create and provide these dependencies.
      III. Provider: A configuration that tells the injector how to create a service.
      IV.  Constructor Injection: Dependencies are injected into the constructor of a class.
     **Key Terms:**
      @Injectable: Decorator used to mark a class as available for DI.
      providers: Register a service to make it injectable.
      root injector: Default injector that registers services globally.
      constructor injection: Dependencies are passed to the class constructor.
### 8. **What are pipes?**
    Pipes transform data in templates. Example:

    ```typescript
    @Component({
      template: `<p>Birthday is {{ birthday | date }}</p>`
    })
    export class BirthdayComponent {
      birthday = new Date(1987, 6, 18);
    }
    ```
    
      **Difference between pure and impure pipes:**
   
    - **Pure pipes**: Triggered only when input values or references change.
    - **Impure pipes**: Called on every change detection cycle, even if inputs remain unchanged.
Here’s a list of commonly used **Angular pipes** along with their definitions and usage:

### **Summary**

| **Pipe**         | **Description**                                                |
|-------------------|----------------------------------------------------------------|
| `uppercase`       | Converts text to uppercase.                                   |
| `lowercase`       | Converts text to lowercase.                                   |
| `titlecase`       | Capitalizes the first letter of each word.                    |
| `currency`        | Formats numbers as currency.                                  |
| `date`            | Formats dates and times.                                      |
| `percent`         | Displays numbers as percentages.                              |
| `decimal`         | Formats numbers with decimal points.                          |
| `slice`           | Extracts a part of a string or array.                         |
| `json`            | Converts an object to JSON format.                            |
| `keyvalue`        | Converts an object into key-value pairs.                      |
| `async`           | Resolves Observables or Promises.                             |
| `i18nPlural`      | Displays strings based on numeric values (internationalized). |
| `i18nSelect`      | Displays strings based on key-value mappings (internationalized). |
| `default` (custom)| Provides a default value for undefined inputs.                |
| `reverse` (custom)| Reverses a string (custom implementation).                    |

---
### 9.  **What is routing?**
- routing is a URL pattern matching.
- routing used to handle the navigation from one view to the next
     - routes- this is the class used to map the component & path.
     - router-outlet- this is the place to load the active component.
     - routerLink- this is the directive to navigate different routes.
-Routing Gurards - guards are interfaces already available natively in angular that let us control access to routes based on conditions we provide in the class of the interface.

### 10. **What are observables?**
    Observables provide a mechanism for asynchronous programming and event handling, supporting multiple values over time. They are declarative and require a subscription.
   - An Observer is an object that listens to an Observable and reacts to its emitted values, errors, or completion.

    Example:

    ```typescript
    import { Observable } from 'rxjs';

    const observable = new Observable(subscriber => {
      subscriber.next('Hello');
      subscriber.complete();
    });

    observable.subscribe(console.log);
    **Diff b/n Subject and Behavior subject -
     - BehaviorSubject holds one value. when it is subscribed it emits the value immediately.
     - A subject doesnt hold a value.?
     - A Subject is both an Observable and an Observer. It allows multicasting (sharing the same Observable execution among multiple subscribers).
     - **How to Handle Errors in RxJS?** Use `catchError` to handle errors in the Observable chain.
 
    ```

### 11. **What is RxJS?**
    RxJS is a library for reactive programming with Observables, supporting operators for composing asynchronous streams. Example usage with `HttpClient`:
    - An Operator is a function that transforms, filters or combines Observables.
    - **What is the `async` Pipe?**
      The `async` pipe in Angular automatically subscribes to and unsubscribes from Observables in templates.
    ```typescript
    import { catchError, retry } from 'rxjs/operators';
    
    ```
     **When to Use RxJS in Angular?**
      - Handling asynchronous events.
      - Managing HTTP requests and responses.
      - Creating reusable streams for user interactions.
      - Implementing real-time data updates.
      **Summary of RxJS Operators**

| **Operator**    | **When to Use**                                                                                  |
|------------------|-------------------------------------------------------------------------------------------------|
| **forkJoin**     | Combine multiple Observables and wait for all to complete. Results are emitted as an array/object. |
| **combineLatest**| Combine latest values from multiple Observables; updates when any Observable emits a value.     |
| **zip**          | Combine values in order from multiple Observables; waits for all to emit a value.              |
| **merge**        | Run Observables in parallel and emit values as they arrive.                                    |
| **switchMap**    | Use for sequential or dependent API calls; cancels previous calls if a new one is triggered.   |


| Type             | Description                                                                                      |
|------------------|--------------------------------------------------------------------------------------------------|
| `Subject`        | Emits values to all subscribers starting from the time they subscribe.                          |
| `BehaviorSubject`| Stores the last emitted value and immediately sends it to new subscribers.                       |
| `ReplaySubject`  | Emits a specified number of previously emitted values to new subscribers.                        |



### 6. **What is an Operator in RxJS?**

#### Common Operators:
| **Operator**     | **Description**                                                                 |
|------------------|-------------------------------------------------------------------------------|
| `map`            | Transforms each emitted value.                                               |
| `filter`         | Emits values that pass a condition.                                          |
| `merge`          | Combines multiple Observables into one.                                      |
| `concat`         | Concatenates Observables sequentially.                                       |
| `switchMap`      | Cancels the previous Observable and switches to the latest one.             |
| `catchError`     | Handles errors in the Observable chain.                                      |
| `debounceTime`   | Waits for a specified time before emitting a value.                         |



#### Example with HTTP:
```typescript
import { HttpClient } from '@angular/common/http';
import { Component } from '@angular/core';

@Component({
  selector: 'app-http-example',
  template: `<ul><li *ngFor="let post of posts$ | async">{{ post.title }}</li></ul>`
})
export class HttpExampleComponent {
  posts$ = this.http.get<{ title: string }[]>('https://jsonplaceholder.typicode.com/posts');

  constructor(private http: HttpClient) {}
}
```
14. **How to Upgrade Angualar application?**
      - follow the link step by step for a higher version: https://update.angular.io/


16. **Difference between promise and observable:**

| Feature           | Observable                | Promise              |
|-------------------|---------------------------|----------------------|
| Execution         | Lazy (starts on subscribe)| Eager (executes immediately)|
| Values            | Emits multiple values     | Emits a single value |
| Error Handling    | Uses `subscribe`          | Uses `.catch()`      |
| Chaining          | Rich operators            | Limited `.then()`    |

## NGRX Q&A Cheat Sheet

### 1. **What is NgRx?**
NgRx (Angular Reactive Extensions) is a framework for building reactive applications in Angular. It is based on Redux and RxJS for state management.

---

### 2. **What are the Core Concepts of NgRx?**
- **Store**: Centralized state container for the application.
- **Actions**: Events that describe unique changes to the state.
- **Reducers**: Pure functions that specify how the state changes in response to actions.
- **Selectors**: Functions to query data from the store.
- **Effects**: Side effects that handle external interactions like HTTP calls.

---

### 3. **What is a Store?**
The Store is a centralized container that holds the application state. It is immutable and acts as the single source of truth for the app.

#### Example:
```typescript
import { Store } from '@ngrx/store';

constructor(private store: Store<{ count: number }>) {}

this.store.select('count').subscribe(value => console.log(value));
```

---

### 4. **What is an Action?**
Actions are plain objects that describe an event or change in the application.

#### Example:
```typescript
import { createAction } from '@ngrx/store';

export const increment = createAction('[Counter] Increment');
export const decrement = createAction('[Counter] Decrement');
```

---

### 5. **What is a Reducer?**
Reducers are pure functions that specify how the state changes in response to an action.

#### Example:
```typescript
import { createReducer, on } from '@ngrx/store';
import { increment, decrement } from './counter.actions';

export const initialState = 0;

export const counterReducer = createReducer(
  initialState,
  on(increment, state => state + 1),
  on(decrement, state => state - 1)
);
```

---

### 6. **What is a Selector?**
Selectors are functions used to retrieve specific pieces of state from the store.

#### Example:
```typescript
import { createSelector } from '@ngrx/store';

export const selectFeature = (state: AppState) => state.feature;
export const selectFeatureCount = createSelector(
  selectFeature,
  feature => feature.count
);
```

---

### 7. **What are Effects?**
Effects handle side effects in an NgRx application, such as HTTP requests or logging. They listen for actions and return new actions.

#### Example:
```typescript
import { Actions, createEffect, ofType } from '@ngrx/effects';
import { map, mergeMap } from 'rxjs/operators';
import { loadItemsSuccess } from './actions';
import { HttpClient } from '@angular/common/http';

export class ItemsEffects {
  loadItems$ = createEffect(() =>
    this.actions$.pipe(
      ofType('[Items] Load Items'),
      mergeMap(() =>
        this.http.get('/api/items').pipe(
          map(items => loadItemsSuccess({ items }))
        )
      )
    )
  );

  constructor(private actions$: Actions, private http: HttpClient) {}
}
```

---

### 8. **What is Entity State?**
NgRx Entity simplifies state management for collections of data by providing utilities like selectors and reducers.

#### Example:
```typescript
import { createEntityAdapter } from '@ngrx/entity';

export interface Item {
  id: string;
  name: string;
}

const adapter = createEntityAdapter<Item>();

export const initialState = adapter.getInitialState();
```

---

### 9. **What is Store DevTools?**
Store DevTools is an NgRx extension that integrates with Redux DevTools to debug the store and actions.

#### Installation:
```bash
npm install @ngrx/store-devtools
```

#### Example:
```typescript
import { StoreDevtoolsModule } from '@ngrx/store-devtools';
@NgModule({
  imports: [
    StoreDevtoolsModule.instrument({ maxAge: 25 })
  ]
})
export class AppModule {}
```

---

### 10. **What is the Role of `createFeature`?**
`createFeature` simplifies feature state setup by combining reducers and selectors for modularity.

#### Example:
```typescript
import { createFeature, createReducer, on } from '@ngrx/store';

const feature = createFeature({
  name: 'counter',
  reducer: createReducer(
    0,
    on(increment, state => state + 1),
    on(decrement, state => state - 1)
  )
});

export const {
  name,
  reducer,
  selectCounterState,
  selectCounter,
} = feature;
```

---

### 11. **What are NgRx Data and NgRx ComponentStore?**
- **NgRx Data**: Provides a higher-level abstraction for managing entity collections.
- **NgRx ComponentStore**: Manages local state for a specific component or a small group of components.

#### Example (ComponentStore):
```typescript
import { ComponentStore } from '@ngrx/component-store';

interface State {
  count: number;
}

export class CounterStore extends ComponentStore<State> {
  constructor() {
    super({ count: 0 });
  }

  readonly increment = this.updater(state => ({ count: state.count + 1 }));
}
```

---

### 12. **What are Common NgRx Use Cases?**
- Managing global state like user authentication or settings.
- Tracking asynchronous data from APIs.
- Centralizing and debugging application events.



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
   - a technique that allows users to defer the loading of certain parts of an application.
   - it reduces the initial load time.
    Lazy loading loads feature modules asynchronously when required, improving performance. Example:

    ```typescript
    {
      path: 'orders',
      loadChildren: () => import('./orders/orders.module').then(m => m.OrdersModule)
    }
    ```
- **Deferable views, also known as @defer blocks, are a powerful tool that is used to reduce the initial bndle size of application intro in Angular 17.
     - using this feature we can lazy loading for any html content.
19. **What is TestBed in Angular?**
    TestBed is an API for unit testing Angular components and services. It simplifies injection, asynchronous behavior, and DOM interactions during tests.

20. **What are reactive and template-driven forms?**
Reactive Forms - provide access to information about giving control through properties and methods provided in each instance.
   - also known as model-driven forms.
   - reactive principles and allow you to manage form state and validation programmatically.
Template-Driven Forms - is the simplest way to build a form in angular.
   - used in Angular two-way data-binding directive (ngModel) to create and manage the underlying form instance.
     
| Feature              | Reactive Forms           | Template-Driven Forms |
|----------------------|--------------------------|------------------------|
| Model Setup          | Explicitly defined       | Defined in template   |
| Data Updates         | Synchronous             | Asynchronous          |
| Validation           | Defined in component    | Defined in template   |
| Scalability          | Highly scalable         | Suitable for simple forms |

Form Builder - provides syntactic sugar that shortens creating instances of formControl, FormFroup, or FormArray.
   - it reduces the amount of boilerplate needed to build complex forms.
FormGroup - provides its model value as an object reduced from the values of each control in the group.
FormControl - classes that hold both data and values and validation information of any form element.
Form Array - manage dynamic forms in angular application.

20. **What is the difference between ngOnChanges and ngDoCheck?**

    - `ngOnChanges`: Detects changes in input-bound properties.
    - `ngDoCheck`: Custom change detection logic for detecting changes not tracked by Angular.

21. **What is the purpose of the common module?**
    The `@angular/common` module provides essential pipes, directives, and services like `ngIf`, `ngFor`, and `HttpClientModule`. It is a foundational module in Angular projects.

22. **What is a standalone component?**
A standalone component is a type of component that is not part of any Angular module. It provides a simplified way to build Angular applications.
23. **What are Angular Signals?**
A signal is a wrapper around a value that can notify interested consumers when that value changes.
Signals can contain any value, from simple primitives to complex data structures.
- similar to obeservale& also used state management.
- Converting Signal to Observale - use the "toObservale" method to turn it into observable. The "toSignal" fiction creates a signal which tracks the value of an observable.
25. **ViewChildren** - Purpose: Allows you to access multiple child components, directives, or DOM elements within a view.
Usage: Use it when querying for a collection of elements or components.
26. **ViewChild**
27. **HTTPCalls** are used to interact with REST APIs or other HTTP services. The HttpClient module, provided by Angular, makes it easy to perform GET, POST, PUT, DELETE, and other HTTP requests.
    - HTTP Interceptor - used to perform various tasks related to HTTP requests and responses.
         - such as adding headers, handling errors, modifying the request or res data, logging, authentication, etc.
28. **ng-template** - The <ng-template> directive in Angular defines a template that is not rendered by default but can be programmatically inserted into the DOM. It is typically used for structural directives and dynamic content.
29. **ng-content** - The <ng-content> directive is used to project content from a parent component into a child component. This is part of Angular's Content Projection mechanism.
Key Features: Facilitates reusable components that accept dynamic content.
Supports multiple content projections with selectors.
30. **The @HostListener decorator** in Angular is used to listen to and handle events on the host element of a directive or component. It's part of Angular's host binding capabilities, enabling you to respond to user interactions or browser events directly on the host element.

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
