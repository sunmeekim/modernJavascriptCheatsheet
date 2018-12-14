# Modern JavaScript Cheatsheet

![Modern JavaScript cheatsheet](https://i.imgur.com/aexPxMb.png)
<small>Image Credits: [Ahmad Awais ⚡️](https://github.com/ahmadawais)</small>

## Introduction

### Motivation

이 문서는  당신이 요즘 프로젝트나 샘플 코드에서 빈번하게 보고있는 자바스크립트를 위한 컨닝페이퍼 같은 것 입니다.

이 가이드는 당신에게 자바스크립트의 밑바닥부터 가르치거나 할 의도는 없습니다. 그러나 기본 지식을 가진 개발자들을 돕기 위해 왜냐하면 그들이 자바스크립트의 컨셉을 사용하는 최근 코드(예를 들어 리액트를 배우라고 해봅시다.)와 친해질 수 있게 노력할 것입니다.

게다가, 때때로 논쟁의 여지가 있고, 그걸 쓸 때 개인적으로 추천하는 방법을 언급하며 팁을 제공 할 것 입니다  

> **Note:** 여기에서 소개된 컨셉들은 ES6 업데이트된 자바스크립트 입니다. 여러분들은 여기에서 새로 추가된 내용들을 잘 찾아볼 수 있습니다.

### Complementary Resources

당신이 개념을 이해하려고 노력할때 , 자료들 보며 답을 찾으라고 제안합니다.

- [MDN (Mozilla Developer Network)](https://developer.mozilla.org/en-US/search?q=)
- [You don't know JS (book)](https://github.com/getify/You-Dont-Know-JS)
- [ES6 Features with examples](http://es6-features.org)
- [WesBos blog (ES6)](http://wesbos.com/category/es6/)
- [Javascript Basics for Beginners](https://www.udacity.com/course/javascript-basics--ud804) - a free Udacity course
- [Reddit (JavaScript)](https://www.reddit.com/r/javascript/)
- [Google](https://www.google.com/) to find specific blog and resources
- [StackOverflow](https://stackoverflow.com/questions/tagged/javascript)

## Table of Contents

- [Modern JavaScript cheatsheet](#modern-javascript-cheatsheet)
  * [Introduction](#introduction)
    + [Motivation](#motivation)
    + [Complementary resources](#complementary-resources)
  * [Table of contents](#table-of-contents)
  * [Notions](#notions)
    + [Variable declaration: var, const, let](#variable-declaration-var-const-let)
      - [Short explanation](#short-explanation)
      - [Sample code](#sample-code)
      - [Detailed explanation](#detailed-explanation)
      - [External resource](#external-resource)
    + [Arrow function](#-arrow-function)
      - [Sample code](#sample-code-1)
      - [Detailed explanation](#detailed-explanation-1)
        * [Concision](#concision)
        * [*this* reference](#this-reference)
      - [Useful resources](#useful-resources)
    + [Function default parameter value](#function-default-parameter-value)
      - [External resource](#external-resource-1)
    + [Destructuring objects and arrays](#destructuring-objects-and-arrays)
      - [Explanation with sample code](#explanation-with-sample-code)
      - [Useful resources](#useful-resources-1)
    + [Array methods - map / filter / reduce](#array-methods---map--filter--reduce)
      - [Sample code](#sample-code-2)
      - [Explanation](#explanation)
        * [Array.prototype.map()](#arrayprototypemap)
        * [Array.prototype.filter()](#arrayprototypefilter)
        * [Array.prototype.reduce()](#arrayprototypereduce)
      - [External Resource](#external-resource-2)
    + [Spread operator "..."](#spread-operator-)
      - [Sample code](#sample-code-3)
      - [Explanation](#explanation-1)
        * [In iterables (like arrays)](#in-iterables-like-arrays)
        * [Function rest parameter](#function-rest-parameter)
        * [Object properties spreading](#object-properties-spreading)
      - [External resources](#external-resources)
    + [Object property shorthand](#object-property-shorthand)
      - [Explanation](#explanation-2)
      - [External resources](#external-resources-1)
    + [Promises](#promises)
      - [Sample code](#sample-code-4)
      - [Explanation](#explanation-3)
        * [Create the promise](#create-the-promise)
        * [Promise handlers usage](#promise-handlers-usage)
      - [External Resources](#external-resources-2)
    + [Template literals](#template-literals)
      - [Sample code](#sample-code-5)
      - [External resources](#external-resources-3)
    + [Tagged Template Literals](#tagged-template-literals)
      - [External resources](#external-resources-4)
    + [Imports / Exports](#imports--exports)
      - [Explanation with sample code](#explanation-with-sample-code-1)
        * [Named exports](#named-exports)
        * [Default import / export](#default-import--export)
      - [External resources](#external-resources-5)
    + [JavaScript *this*](#-javascript-this)
      - [External resources](#external-resources-6)
    + [Class](#class)
      - [Samples](#samples)
      - [External resources](#external-resources-7)
    + [Extends and super keywords](#extends-and-super-keywords)
      - [Sample Code](#sample-code-6)
      - [External Resources](#external-resources-8)
    + [Async Await](#async-await)
      - [Sample code](#sample-code-7)
      - [Explanation with sample code](#explanation-with-sample-code-2)
      - [Error handling](#error-handling)
      - [External resources](#external-resources-9)
    + [Truthy / Falsy](#truthy--falsy)
      - [External resources](#external-resources-10)
    + [Anamorphisms / Catamporphisms](#anamorphisms-and-catamorphisms)
      - [Anamorphisms](#anamorphisms)
      - [Catamorphisms](#catamorphisms)
      - [External resources](#external-resources-11)
    + [Generators](#generators)
      - [External resources](#external-resources-12)
    + [Static Methods](#static-methods)
      - [Short Explanation](#short-explanation-1)
      - [Sample Code](#sample-code-8)
      - [Detailed Explanation](#detailed-explanation-2)
        * [Calling other static methods from a static method](#calling-other-static-methods-from-a-static-method)
        * [Calling static methods from non-static methods](#calling-static-methods-from-non-static-methods)
      - [External resources](#external-resources-13)
  * [Glossary](#glossary)
    + [Scope](#-scope)
    + [Variable mutation](#-variable-mutation)

## Notions

### Variable declaration: var, const, let 
### (변수선언)

자바스크립트에는 변수를 선언 할 수 있는 3개의 키워드가 있고 각각은 차이점이 있습니다.
그것은  ```var```, ```let``` ,```const``` 입니다. 

#### Short explanation

```const```로 변수들을 선언하면 재 선언을 할 수 없고,  ```let``` 과 ```var```는 할 수 있습니다.

나는 항상 기본적으로 변수들은 ```const```로 선언하고, 만약 변수에 *변화*가 필요하거나 뒤에서 재 선언해야 할 때는 ```let```을 추천했습니다.

<table>
  <tr>
    <th></th>
    <th>Scope</th>
    <th>Reassignable</th>
    <th>Mutable</th>
   <th><a href="#tdz_sample">Temporal Dead Zone</a></th>
  </tr>
  <tr>
    <th>const</th>
    <td>Block</td>
    <td>No</td>
    <td><a href="#const_mutable_sample">Yes</a></td>
    <td>Yes</td>
  </tr>
  <tr>
    <th>let</th>
    <td>Block</td>
    <td>Yes</td>
    <td>Yes</td>
    <td>Yes</td>
  </tr>
   <tr>
    <th>var</th>
    <td>Function</td>
    <td>Yes</td>
    <td>Yes</td>
    <td>No</td>
  </tr>
</table>

#### Sample code

```javascript
const person = "Nick";
person = "John" // Will raise an error, person can't be reassigned
```

```javascript
let person = "Nick";
person = "John";
console.log(person) // "John", reassignment is allowed with let
```

#### Detailed explanation

변수의 [*scope*](#scope_def)는 대충  “이 변수를 어느 코드안에서 사용할 수 있는지.”를 의미합니다.

##### var

```var```로 선언된 변수들은 함수 범위 안에 있습니다. 그 의미는 함수 안에서 변수를 만들었다는 것이며, 이 변수는 함수 안에서 어디든 접근이 가능합니다. 
게다가 이 함수 안에서 변수를 만들었으면, 이 함수 밖에서는 접근할 수 없습니다. 

나는 당신에게 그것이 마치 x라는 변수가 의미를 가지는 범위 안에 있다면, x변수가 가진 값이 나오는 걸 만들어보라고 추천하겠습니다.

```javascript
function myFunction() {
  var myVar = "Nick";
  console.log(myVar); // "Nick" - myVar is accessible inside the function
}
console.log(myVar); // Throws a ReferenceError, myVar is not accessible outside the function.
```

변수의 범위에 집중하고 여기 좀 더 구체적인 예시 : 

```javascript
function myFunction() {
  var myVar = "Nick";
  if (true) {
    var myVar = "John";
    console.log(myVar); // "John"
    // actually, myVar being function scoped, we just erased the previous myVar value "Nick" for "John"
  }
  console.log(myVar); // "John" - see how the instructions in the if block affected this value
}
console.log(myVar); // Throws a ReferenceError, myVar is not accessible outside the function.
```
게다가 *var*로 선언된 변수들은 실행 시 맨 위에 선언된 변수한테 값이 움직여집니다.(맨위에 선언된 변수에 값이 할당되는 것을 의미함) 
이것을 우리는 [var hoisting](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var#var_hoisting)이라고 부릅니다.  

일부 예시코드 :

```js
console.log(myVar) // undefined -- no error raised
var myVar = 2;
```

다음 코드랑 같게 이해됨 :

```js
var myVar;
console.log(myVar) // undefined -- no error raised
myVar = 2;
```

##### let

```var``` 와 ```let ``` 은 같은 종류입니다. 
그러나 ```let```으로 변수를 선언했다는것은

- *블록 범위* 에 있다는 것이다.
- 그것들을 선언하기 전엔 접근 *할 수 없다*.
- 같은 범위 안에서는 다시 선언할 수 없다. 
것 입니다.

블록범위를 강조한 예시를 보면:

```javascript
function myFunction() {
  let myVar = "Nick";
  if (true) {
    let myVar = "John";
    console.log(myVar); // "John"
    // actually, myVar being block scoped, we just created a new variable myVar.
    // this variable is not accessible outside this block and totally independent
    // from the first myVar created !
  }
  console.log(myVar); // "Nick", see how the instructions in the if block DID NOT affect this value
}
console.log(myVar); // Throws a ReferenceError, myVar is not accessible outside the function.
```

<a name="tdz_sample"></a> 이제, 그것의 의미는 let(과 const) 변수들은 값을 할당 되기 전에 접근할 수 없다는 것을 의미합니다:

```js
console.log(myVar) // raises a ReferenceError !
let myVar = 2;
```
*var* 변수와 대조적으로, 만약 당신이 *let* 또는 *const* 변수를 읽거나 쓴다고 한다면, 에러를 보여줬습니다. 
이런 현상은 종종 [*임시적 죽은공간*](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let#Temporal_Dead_Zone_and_errors_with_let) *TDZ*라고 불렀다.

> **Note:** 기술적으로, *let*과 *const* 변수 선언은 호이스팅 되지만 할당만 하지는 않습니다. 그것들은 값을 만들어서 선언하기 전엔 사용할 수 없습니다 이것은 마치 호이스팅 되지 않는 것 처럼 보이지만 그렇진 않습니다. 더 알길 원한다면 [자세한 설명](http://jsrocks.org/2015/01/temporal-dead-zone-tdz-demystified)을 찾아보세요. 

게다가  *let* 변수는 재 선언 할 수 없습니다:

```js
let myVar = 2;
let myVar = 3; // Raises a SyntaxError
```

##### const

```const``` 로 변수를 선언하는 것은 *let* 선언 변수들처럼 재 선언 할 수 없습니다.

*const* 변수들은 다음 내용들을 다 합친것과 같습니다:

- *블록범위* 입니다.
- 그것들이 선언되기 전엔 접근할 수가 없습니다.
- 같은 범위에서는 재 선언할 수 없습니다.
- 재 할당할 수 없습니다.

```js
const myVar = "Nick";
myVar = "John" // raises an error, reassignment is not allowed
```

```js
const myVar = "Nick";
const myVar = "John" // raises an error, re-declaration is not allowed
```

<a name="const_mutable_sample"></a> 그러나 거기엔 미묘한 차이가 있습니다 : ```const```변수들은 [**불변의 것**](#mutation_def) 이 아닙니다!
구체적으로 *object*와 *array*를 ```const```변수로 선언해 변하게 **할 수** 있습니다.

객체(object) :
```js
const person = {
  name: 'Nick'
};
person.name = 'John' // this will work ! person variable is not completely reassigned, but mutated
console.log(person.name) // "John"
person = "Sandra" // raises an error, because reassignment is not allowed with const declared variables
```

배열(array) :
```js
const person = [];
person.push('John'); // this will work ! person variable is not completely reassigned, but mutated
console.log(person[0]) // "John"
person = ["Nick"] // raises an error, because reassignment is not allowed with const declared variables
```

#### External resource

- [How let and const are scoped in JavaScript - WesBos](http://wesbos.com/javascript-scoping/)
- [Temporal Dead Zone (TDZ) Demystified](http://jsrocks.org/2015/01/temporal-dead-zone-tdz-demystified)

### <a name="arrow_func_concept"></a> Arrow function
### (화살표 함수)

ES6 자바스크립트로 업데이트 되면서 화살표 함수가 소개되었습니다. 이것은 우리가 함수를 선언할 수 있는 또다른 방식입니다. 이 방식이 가져다 주는 이점을 보면.
- 간결성
- *this*는 주변의 상태를 보고 가져다 씀
- return 생략 가능

#### Sample code

- 간결성과 강력한 return

```js
function double(x) { return x * 2; } // Traditional way
console.log(double(2)) // 4
```

```js
const double = x => x * 2; // Same function written as an arrow function with implicit return
console.log(double(2)) // 4
```

- *this* 참고자료

화살표 함수 안에서 =은 실행 함수를 감싼 것과 같습니다. 기본적으로 화살표 함수와 그 안에 다른 함수들에서도 "that = this" 로 부르거나 하지 않습니다.  

```js
function myFunc() {
  this.myVar = 0;
  setTimeout(() => {
    this.myVar++;
    console.log(this.myVar) // 1
  }, 0);
}
```

#### Detailed explanation

##### Concision 
##### 간결성

화살표 함수는 기존 함수의 많은 방법들을 좀 더 간결하게 합니다. 가능한 모든 경우를 살펴보면:
- 암시적 VS 명시적 return법

**명시적 return** 은 함수 안에서 return이라는 키워드로 돌려주며 사용하는 것입니다. 

```js
  function double(x) {
    return x * 2; // this function explicitly returns x * 2, *return* keyword is used
  }
```

전통적인 방식으로 함수를 쓰면 항상 **명시적 return**으로 표현합니다. 
그러나 화살표 함수에서는 return을 위한 키워드는 생략할 수 있습니다.

```js
  const double = (x) => {
    return x * 2; // Explicit return here
  }
```

이 함수를 쓰면, 우리는 **암시적 return**으로 있는 딱 그것만 return을 할 수 있습니다.

```js
  const double = (x) => x * 2; // Correct, returns x*2
```

이렇게 하려고 우리는 괄호와 return을 제거 했을 뿐입니다.
저런걸 **암시적 return** 이기 때문에 그 return 이라는 단어는 없지만 ```x * 2```를 반환하게 됩니다.

> **Note:** 만약 당신의 함수가 return 값이 없거나(사이드 이펙트중), 그것이 명확하지 않거나 암시적 return 값이 없으면 작동하지 않는다.

또, 만약 당신이 원하는 암시적 return 값이 *object* 라면, 당신은 그것을 **꼭 괄호로 감싸주셔야 합니다.**  또 그것과 함께 안쪽은 블록 괄호도 함께 써주셔야 합니다:

```js
const getPerson = () => ({ name: "Nick", age: 24 })
console.log(getPerson()) // { name: "Nick", age: 24 } -- object implicitly returned by arrow function
```

- 인자가 딱 하나 일 때

만약 당신의 함수에 파라미터가 딱 하나라면, 당신은 그것 주변의 괄호를 생략할 수 있습니다. 뒤에 두개의 코드를 보면 : 

```js
  const double = (x) => x * 2; // this arrow function only takes one parameter
```

파라미터주변에 괄호들을 생략할 수 있습니다 : 

```js
  const double = x => x * 2; // this arrow function only takes one parameter
```

- 인자가 없을 떄

화살표 함수에서 인자가 없을때는 괄호가 필요한데, 안 쓰면 syntax 오류가 납니다.

```js
  () => { // parentheses are provided, everything is fine
    const x = 2;
    return x;
  }
```

```js
  => { // No parentheses, this won't work!
    const x = 2;
    return x;
  }
```

##### *this* reference

화살표 함수에서 소개된 [this](#this_def)를 이해하려면, 당신은 자바스크립트가 어떻게 동작하는지 알아야만 합니다.

화살표 함수에서 *this* 는 실행 구문 안쪽의 값과 같습니다. 그것은 화살표 함수 안에서는 새로운 *this* 를 만들 수 없다는 것을 의미합니다. 대신 그건 그 주변에 정의된 그 값이 딱 그 함수의 *this* 라는걸 알려주는 역할을 합니다.

화살표가 없는 함수에서는 만약 당신의 함수 안쪽에서 *this*에 접근하길 원한다면, 당신은 that= this 또는 self = this를 사용해 접근할 수 있습니다.

예를 들어, myFunc 함수 안에서 setTimeout함수를 사용할 때 :

```js
function myFunc() {
  this.myVar = 0;
  var that = this; // that = this trick
  setTimeout(
    function() { // A new *this* is created in this function scope
      that.myVar++;
      console.log(that.myVar) // 1

      console.log(this.myVar) // undefined -- see function declaration above
    },
    0
  );
}
```
그러나 화살표 함수에서 *this* 는 그 주변에서 가져 온 값입니다. 

```js
function myFunc() {
  this.myVar = 0;
  setTimeout(
    () => { // this taken from surrounding, meaning myFunc here
      this.myVar++;
      console.log(this.myVar) // 1
    },
    0
  );
}
```

#### Useful resources

- [Arrow functions introduction - WesBos](http://wesbos.com/arrow-functions/)
- [JavaScript arrow function - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)
- [Arrow function and lexical *this*](https://hackernoon.com/javascript-es6-arrow-functions-and-lexical-this-f2a3e2a5e8c4)

### Function default parameter value
### (함수의 기본값)

ES2015 자바스크립트로 업그레이드되면서, 당신은 함수의 파라미터를 사용해 default값을 세팅할 수 있습니다:

```js
function myFunc(x = 10) {
  return x;
}
console.log(myFunc()) // 10 -- no value is provided so x default value 10 is assigned to x in myFunc
console.log(myFunc(5)) // 5 -- a value is provided so x is equal to 5 in myFunc

console.log(myFunc(undefined)) // 10 -- undefined value is provided so default value is assigned to x
console.log(myFunc(null)) // null -- a value (null) is provided, see below for more details
```
기본 파라미터는 두가지 경우에만 지원됩니다:

- 파라미터 없을때
- *undefined* 파라미터로 제공 될 때

다른말로, 만약 당신이 *null* 을 기본 파라미터로 가졌다면, **그건 지원하지 않습니다.**

> **Note:**  기본 값 할당을 형식없이 파리미터로 잘 사용할 수 있습니다. (다음에 개념을 보고 예시를 보세요)

#### External resource
#### (외부 리소스)

- [Default parameter value - ES6 Features](http://es6-features.org/#DefaultParameterValues)
- [Default parameters - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Default_parameters)

### Destructuring objects and arrays
### (형식없는 객체와 배열)

*Destructuring* 라는 것은 배열이나 객체에서 값을 추출해 새로운 변수들을 만드는 편리한 방법입니다. 

이름으로 사용하는 몇가지 경우, *destructuring* 형식을 파괴한 함수 또는 리액트에서  *this.props*의 예처럼 사용할 수 있습니다.

#### Explanation with sample code
#### (설명을 위한 짧은 코드)

- 객체

모든 샘플에 대해 다음 객체를 고려해 보자 : 

```js
const person = {
  firstName: "Nick",
  lastName: "Anderson",
  age: 35,
  sex: "M"
}
```
destructuring 없이

```js
const first = person.firstName;
const age = person.age;
const city = person.city || "Paris";
```
destructuring 해서 한줄에 모두 넣었을때 : 

```js
const { firstName: first, age, city = "Paris" } = person; // That's it !

console.log(age) // 35 -- A new variable age is created and is equal to person.age
console.log(first) // "Nick" -- A new variable first is created and is equal to person.firstName
console.log(firstName) // ReferenceError -- person.firstName exists BUT the new variable created is named first
console.log(city) // "Paris" -- A new variable city is created and since person.city is undefined, city is equal to the default value provided "Paris".
```

**Note :** ```const { age } = person;```상에, *const* 다음에 괄호로 객체또는 블록을 선언하지 않지만, *destructuring* 문법에서는 씁니다.

- 함수의 파라미터들

*Destructuring* 는 종종 함수안에 객체파라미터로 사용합니다.

destructuring 없이

```js
function joinFirstLastName(person) {
  const firstName = person.firstName;
  const lastName = person.lastName;
  return firstName + '-' + lastName;
}

joinFirstLastName(person); // "Nick-Anderson"
```
*person* 객체의 파라미터를 destructuring으로 쓰면, 우리는 더 간결한 함수를 얻을 수 있습니다:

```js
function joinFirstLastName({ firstName, lastName }) { // we create firstName and lastName variables by destructuring person parameter
  return firstName + '-' + lastName;
}

joinFirstLastName(person); // "Nick-Anderson"
```

Destructuring는 심지어 [화살표 함수](#arrow_func_concept) 에서 더 잘 사용합니다:

```js
const joinFirstLastName = ({ firstName, lastName }) => firstName + '-' + lastName;

joinFirstLastName(person); // "Nick-Anderson"
```

- 배열

배열을 고려해보면:

```js
const myArray = ["a", "b", "c"];
```

destructuring 없이

```js
const x = myArray[0];
const y = myArray[1];
```

destructuring 로 

```js
const [x, y] = myArray; // That's it !

console.log(x) // "a"
console.log(y) // "b"
```

#### Useful resources
#### 유용한 리소스들

- [ES6 Features - Destructuring Assignment](http://es6-features.org/#ArrayMatching)
- [Destructuring Objects - WesBos](http://wesbos.com/destructuring-objects/)
- [ExploringJS - Destructuring](http://exploringjs.com/es6/ch_destructuring.html)

### Array methods - map / filter / reduce
### 배열 메소드들 - map / filter / reduce

*Map*, *filter*, *reduce*는 함수형 프로그래밍에서 온 배열 메소드들입니다.[*functional programming*](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-functional-programming-7f218c68b3a0).

요약 해 보면:

- **Array.prototype.map()** 배열에서, 그것의 요소와 반환값을 바꿔줄 때 쓰세요.
- **Array.prototype.filter()** 배열에서, 요소로서 만약 그것을 지키고 싶고 단지 리턴된 요소 값만 가지고 싶다고 결정 했을때
- **Array.prototype.reduce()** 배열에서, 요소들을 한 대 모아 하나의 값으로 만들때 (뭔가 값을 리턴할 때)

나는 그것들을 함수형 프로그래밍을 사용하는 곳에서는 가능한 많이 사용하길 추천드립니다. 
왜냐하면 그것들은 간결하고 멋지게 구성이 가능하기 때문입니다.

이 세가지 방법들과 함께 하면, 당신은 대부분의 for와 forEach 사용을 피할 수 있습니다. 
당신이 for loop를 사용하고 싶을때 map, filter, reduce구성을 사용해 보세요.
저걸 사용하는 노력을 한다면, 한번에 loop를 돈 것처럼 만들고 지우고 하는 방법을 새로 쉽게 배울 수 있습니다.

#### Sample code
#### 샘플코드

```js
const numbers = [0, 1, 2, 3, 4, 5, 6];
const doubledNumbers = numbers.map(n => n * 2); // [0, 2, 4, 6, 8, 10, 12]
const evenNumbers = numbers.filter(n => n % 2 === 0); // [0, 2, 4, 6]
const sum = numbers.reduce((prev, next) => prev + next, 0); // 21
```
학생들의 등급 중 10등급 이상인 학생들의 등급들의 합들을 map, filter,reduce의 조합으로 계산해 보세요:

```js
const students = [
  { name: "Nick", grade: 10 },
  { name: "John", grade: 15 },
  { name: "Julia", grade: 19 },
  { name: "Nathalie", grade: 9 },
];

const aboveTenSum = students
  .map(student => student.grade) // we map the students array to an array of their grades
  .filter(grade => grade >= 10) // we filter the grades array to keep those 10 or above
  .reduce((prev, next) => prev + next, 0); // we sum all the grades 10 or above one by one

console.log(aboveTenSum) // 44 -- 10 (Nick) + 15 (John) + 19 (Julia), Nathalie below 10 is ignored
```

#### Explanation
#### 설명

숫자로 된 배열의 예시를 고려해 보면 : 

```js
const numbers = [0, 1, 2, 3, 4, 5, 6];
```

##### Array.prototype.map()

```js
const doubledNumbers = numbers.map(function(n) {
  return n * 2;
});
console.log(doubledNumbers); // [0, 2, 4, 6, 8, 10, 12]
```
여기에서 무슨일이 벌어질까? *numbers* 배열에 .map을 사용하면, 그 map은 배열의 각 요소들을 함수에 넣어줍니다. 그 함수의 목적은 map지나 온 값으로 새로운 값을 반환하는 것입니다.

이 함수로 그것을 좀 더 깔끔하게 추출해보자 한번만 써서 : 

```js
const doubleN = function(n) { return n * 2; };
const doubledNumbers = numbers.map(doubleN);
console.log(doubledNumbers); // [0, 2, 4, 6, 8, 10, 12]
```

**Note** : 우리는 자주 이 메소드와 [화살표 함수](#-arrow-function)를 같이 사용하게 될 것입니다.

```js
const doubledNumbers = numbers.map(n => n * 2);
console.log(doubledNumbers); // [0, 2, 4, 6, 8, 10, 12]
```

```numbers.map(doubleN)``` 는 이런 식으로```[doubleN(0), doubleN(1), doubleN(2), doubleN(3), doubleN(4), doubleN(5), doubleN(6)]``` ```[0, 2, 4, 6, 8, 10, 12]```  이 값과 같은 것을 만듭니다.

> **Note:** 만약에 당신이 새로운 배열을 return할 필요도 없고, 반복 실행만 원한다면, map대신 for나 forEach를 사용하면 됩니다.

##### Array.prototype.filter()

```js
const evenNumbers = numbers.filter(function(n) {
  return n % 2 === 0; // true if "n" is par, false if "n" isn't
});
console.log(evenNumbers); // [0, 2, 4, 6]
```

**Note** : 우리는 자주 이 메소드와 [화살표 함수](#-arrow-function)를 같이 사용하게 될 것입니다.

```js
const evenNumbers = numbers.filter(n => n % 2 === 0);
console.log(evenNumbers); // [0, 2, 4, 6]
```

우리가 *numbers* 배열 상에 .filter를 사용합니다. filter는 우리의 함수를 거치는 작업을 반복합니다. 그 함수의 목적은 참 거짓을 결정해 남길 것인지 버릴 것인지를 합니다. 
Filter는 남겨진 값을 배열로 반환합니다.

##### Array.prototype.reduce()

The reduce method goal is to *reduce* all elements of the array it iterates on into a single value. How it aggregates those elements is up to you.
*reduce* 메소드의 목적은 배열의 모든 요소들을 반복해 하나의 값으로 만들어 주는 것이다. 어떻게 합칠 것 인가만 당신이 결정하면 된다.

```js
const sum = numbers.reduce(
  function(acc, n) {
    return acc + n;
  },
  0 // accumulator variable value at first iteration step
);

console.log(sum) // 21
```

**Note** : 우리는 자주 이 메소드와 [화살표 함수](#-arrow-function)를 같이 사용하게 될 것입니다.

```js
const sum = numbers.reduce((acc, n) => acc + n, 0);
console.log(sum) // 21
```

찾는 값에 따라서 .map .filter .reduce는 그 메소드 안에 파라미터로 쓴 함수에 의해 배열을 적용합니다.

이걸 통해 바꿔보면 :

- .reduce 는 2개의 파라미터를 가진 것 이다.

첫번째 파라미터는 각 스텝을 반복하는 함수이다.

두번째 파라미터는 처음 반복문을 지난 값(read next point to understand)을 압축한 값(*acc* here) 입니다.


- 함수 파라미터들

The function you pass as the first parameter of .reduce takes two parameters. The first one (*acc* here) is the accumulator variable, whereas the second parameter (*n*) is the current element.
함수는 당신이 첫번째 파라미터로 .reduce가 가진 2개의 파라미터를 지난다. 처음엔 값을 합치고, 두번째엔 그걸 n번하는 것이다.
The accumulator variable is equal to the return value of your function at the **previous** iteration step. At the first step of the iteration, *acc* is equal to the value you passed as .reduce second parameter.
합쳐진 값은 당신의 기존 반복문을 통해 반환된 값과 같다. 처음 쓰는 반복문은 *acc* .reduce 두번째 파라미터를 돈 값과 같다.

###### At first iteration step
###### 첫번째 반복문

```acc = 0``` 우리가 reduce의 두번째 파라미터를 지나 0이기 때문에,

```n = 0```  *number*배열의 첫번쨰 요소와 

Function returns *acc* + *n* --> 0 + 0 --> 0 (함수의 값을 리턴하면 0이 된다.)

###### At second iteration step
###### 두번째 반복문

```acc = 0``` 이전 반복문에서 반환한 값이 0이기 때문에

```n = 1```  *number* 배열의 두번째 요소와 

Function returns *acc* + *n* --> 0 + 1 --> 1 (함수의 값을 리턴하면 1이 된다.)

###### At third iteration step
###### 세번째 반복문

```acc = 1``` 이전 반복문에서 반환한 값이 1이기 때문에

```n = 2``` *number* 배열의 세번째 요소와 

Function returns *acc* + *n* --> 1 + 2 --> 3 (함수의 값을 리턴하면 3이 된다.)

###### At fourth iteration step
###### 네번째 반복문

```acc = 3``` 이전 반복문에서 반환한 값이 3이기 때문에

```n = 3``` *number* 배열의 네번째 요소와 

Function returns *acc* + *n* --> 3 + 3 --> 6(함수의 값을 리턴하면 6이 된다.)

###### [...] At last iteration step
###### 나머지 반복문

```acc = 15``` 이전 반복문에서 반환한 값이 15이기 때문에

```n = 6``` *number* 배열의 마지막 요소와 

Function returns *acc* + *n* --> 15 + 6 --> 21 함수의 값을 리턴하면 21이 된다.)

As it is the last iteration step, **.reduce** returns 21. 
마지막까지 반복해서 **.reduce** 는 21을 반환한다.

#### External Resource
#### 외부리소스

- [Understanding map / filter / reduce in JS](https://hackernoon.com/understanding-map-filter-and-reduce-in-javascript-5df1c7eee464)

### Spread operator "..." 
### "..." 스프레드 문법

The spread operator ```...``` has been introduced with ES2015 and is used to expand elements of an iterable (like an array) into places where multiple elements can fit.
"..." 스프레드 문법은 ES2015에서 소개되었고, 반복적인(배열같은) 여러개의 요소로 확장된 요소들을 어딘가에 최적화 해서 표현할 때 사용한다. 

#### Sample code

```js
const arr1 = ["a", "b", "c"];
const arr2 = [...arr1, "d", "e", "f"]; // ["a", "b", "c", "d", "e", "f"]
```

```js
function myFunc(x, y, ...params) {
  console.log(x);
  console.log(y);
  console.log(params)
}

myFunc("a", "b", "c", "d", "e", "f")
// "a"
// "b"
// ["c", "d", "e", "f"]
```

```js
const { x, y, ...z } = { x: 1, y: 2, a: 3, b: 4 };
console.log(x); // 1
console.log(y); // 2
console.log(z); // { a: 3, b: 4 }

const n = { x, y, ...z };
console.log(n); // { x: 1, y: 2, a: 3, b: 4 }
```

#### Explanation 
#### 설명

##### In iterables (like arrays)
##### 반복적인 것 - 배열처럼

아래 두개의 배열이 있다면:

```js
const arr1 = ["a", "b", "c"];
const arr2 = [arr1, "d", "e", "f"]; // [["a", "b", "c"], "d", "e", "f"]
```
*arr2* 의 첫번째 요소에 *arr1*배열 넣어서 *arr2* 이다. 그러나 우리는 *arr2* 배열 안에 배열이 아닌 문자로 들어고길 원한다면, 우리는 *arr1*에 *spread*를 넣어 *arr2*를 만들 수 있다.

스프레드로 쓰면:

```js
const arr1 = ["a", "b", "c"];
const arr2 = [...arr1, "d", "e", "f"]; // ["a", "b", "c", "d", "e", "f"]
```

##### Function rest parameter
##### 함수의 나머지 요소

In function parameters, we can use the rest operator to inject parameters into an array we can loop in. There is already an **arguments** object bound to every function that is equal to an array of all the parameters passed into the function.

함수 안 파라미터에서, 우리는 나머지 파라미터들의 배열에 loop를 돌리는것 처럼 사용 할 수 있습니다. 거기엔 이미 **arguments** 객체가 모두 묶여서 함수안을 모든 파라미터가 통과 한 것과 같습니다.

```js
function myFunc() {
  for (var i = 0; i < arguments.length; i++) {
    console.log(arguments[i]);
  }
}

myFunc("Nick", "Anderson", 10, 12, 6);
// "Nick"
// "Anderson"
// 10
// 12
// 6
```

그러나 우리가 이 함수로 새로운 학생의 등급을 또는 그것의 평균을 원한다고 해보자. 
처음에 두개의 요소를 확장한 변수로 배열 안에 모든 등급을 넣고 그걸 반복해서 할 수 있는 더 편한 방법이 없을까 ?

맞아요 아래처럼 하면 돼요! :

```js
function createStudent(firstName, lastName, ...grades) {
  // firstName = "Nick"
  // lastName = "Anderson"
  // [10, 12, 6] -- "..." takes all other parameters passed and creates a "grades" array variable that contains them

  const avgGrade = grades.reduce((acc, curr) => acc + curr, 0) / grades.length; // computes average grade from grades

  return {
    firstName: firstName,
    lastName: lastName,
    grades: grades,
    avgGrade: avgGrade
  }
}

const student = createStudent("Nick", "Anderson", 10, 12, 6);
console.log(student);
// {
//   firstName: "Nick",
//   lastName: "Anderson",
//   grades: [10, 12, 6],
//   avgGrade: 9,33
// }
```

> **Note:** createStudent 함수는 별로입니다. 왜냐하면 우리가 만약 등급갯수의 존재 또는 0이 아닌걸 체크할 수 없습니다. 이 방법이 읽기는 쉽지만 나는 이렇게 처리하지 않습니다.

##### Object properties spreading

이걸로, 나는 rest operator상의 반복과 함수 요소에 대한 앞쪽 설명들을 먼저 읽기를 추천합니다.

```js
const myObj = { x: 1, y: 2, a: 3, b: 4 };
const { x, y, ...z } = myObj; // object destructuring here
console.log(x); // 1
console.log(y); // 2
console.log(z); // { a: 3, b: 4 }

// z is the rest of the object destructured: myObj object minus x and y properties destructured

const n = { x, y, ...z };
console.log(n); // { x: 1, y: 2, a: 3, b: 4 }

// Here z object properties are spread into n
```

#### External resources

- [TC39 - Object rest/spread](https://github.com/tc39/proposal-object-rest-spread)
- [Spread operator introduction - WesBos](https://github.com/wesbos/es6-articles/blob/master/28%20-%20Spread%20Operator%20Introduction.md)
- [JavaScript & the spread operator](https://codeburst.io/javascript-the-spread-operator-a867a71668ca)
- [6 Great uses of the spread operator](https://davidwalsh.name/spread-operator)

### Object property shorthand 
### 객체 속성 짧게 쓰기

객체의 속성값을 변수로 할당할때, 만약 변수 명이 그 객체의 요소 명과 같다면, 아래처럼 쓸 수 있습니다. : 
```js
const x = 10;
const myObj = { x };
console.log(myObj.x) // 10
```

#### Explanation 
#### 설명

보통 (ES2015이전에) 당신이 새로운 객체를 선언할 때나 객체의 값을 변수로 사용하고 싶을때, 아래 코드들 처럼 썼을 것입니다. : 
```js
const x = 10;
const y = 20;

const myObj = {
  x: x, // assigning x variable value to myObj.x
  y: y // assigning y variable value to myObj.y
};

console.log(myObj.x) // 10
console.log(myObj.y) // 20
```

당신이 보는거처럼 , 이건 완전 반복입니다. 왜냐면 객체들이 이미 변수와 같은 걸 쓰고 있기 때문입니다.
ES2015에 변수의 이름이 객체요소의 이름과 같다면 아래처럼 짧게 쓸 수 있습니다.:

```js
const x = 10;
const y = 20;

const myObj = {
  x,
  y
};

console.log(myObj.x) // 10
console.log(myObj.y) // 20
```

#### External resources
#### 외부 리소스

- [Property shorthand - ES6 Features](http://es6-features.org/#PropertyShorthand)

### Promises 

promise는 비동기적 함수를 동기적으로 반환 할 수 있는 어떤 객채 같은 겁니다.([ref](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-promise-27fc71e77261#3cd0)).
promise들은 [callback hell](http://callbackhell.com/)을 피할때 사용할 수 있습니다. 그리고 그것들은 요즘 보는 자바스크립트 프로젝트에서 점점 더 자주 보여집니다.

#### Sample code

```js
const fetchingPosts = new Promise((res, rej) => {
  $.get("/posts")
    .done(posts => res(posts))
    .fail(err => rej(err));
});

fetchingPosts
  .then(posts => console.log(posts))
  .catch(err => console.log(err));
```

#### Explanation

당신이 *Ajax request*를 할 때, 응답이 동기적이지 않습니다. 당신이 원하는 리소스가 도착하기까지 시간이 좀 걸리기 때문입니다. 그것은  만약 그 리소스가  몇가지 이유로 사용할 수 없는 요청 일 때  심지어 오지 않을 수도 있습니다.(404).
저런 상황들에 대처하기 위해서, ES2015는 *promises*를 우리에게 가져다 주었습니다. Promises 는 3가지 서로 다른 상태를 가질 수 있습니다. :  

- Pending :: 대기
- Fulfilled :: 성공
- Rejected :: 거절

우리가 리소스 x를 가져올때 Ajax요청을 promises를 통해 하고 싶다고 해보자.

##### Create the promise

우리는 먼저 promise를 생성할 것입니다. jQuery에 get method를 이용해 x를 Ajax 요청을 할때 사용할 수 있습니다.

```js
const xFetcherPromise = new Promise( // Create promise using "new" keyword and store it into a variable
  function(resolve, reject) { // Promise constructor takes a function parameter which has resolve and reject parameters itself
    $.get("X") // Launch the Ajax request
      .done(function(X) { // Once the request is done...
        resolve(X); // ... resolve the promise with the X value as parameter
      })
      .fail(function(error) { // If the request has failed...
        reject(error); // ... reject the promise with the error as parameter
      });
  }
)
```

위에서 보는 것처럼, promise 객체는 함수의 *executor* 로 두개의 파라미터 **resolve** 와 **reject** 를 취합니다.
이런 파라미터들은 promise로 부를때 *pending* 상태에서 각각 *fulfilled* 와 *rejected* 상태로 움직여집니다. 

promise는 pending상태에서 인스턴스를 생성하고 그것의 실행 함수를 통해 바로 실행합니다. 일단 함수에서 *resolve* 또는 *reject* 중에 하나가 실행 함수로 불려집니다.
promise는 그것들과 관련된 핸들러를 부를 것입니다.

##### Promise handlers usage

결과 또는(에러)를 promise에서 얻으면, 우리는 해당 핸들로 접근해야처리해야 합니다.: 

```js
xFetcherPromise
  .then(function(X) {
    console.log(X);
  })
  .catch(function(err) {
    console.log(err)
  })
```

만약 Promise가 성공했다면, *resolve* 는 함수에서 ```.then```파라미터를 통해서 실행하면 됩니다.
만약 실패했다면, *reject*는 함수에서  ```.catch``` 파라미터를 통해서 실행하면 됩니다.

> **Note :** 만약 promise에서 이미 성공 또는 거절되었다면 거기에 상응하는 핸들러에 접근합니다. 그 핸들러는 비동기적인 작업이고 그것들이 핸들러를 통해 순차적으로 처리된다고 말합니다. [(Ref: MDN)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise#Description)


#### External Resources
#### 외부 리소스들

- [JavaScript Promises for dummies - Jecelyn Yeen](https://scotch.io/tutorials/javascript-promises-for-dummies)
- [JavaScript Promise API - David Walsh](https://davidwalsh.name/promises)
- [Using promises - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)
- [What is a promise - Eric Elliott](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-promise-27fc71e77261)
- [JavaScript Promises: an Introduction - Jake Archibald](https://developers.google.com/web/fundamentals/getting-started/primers/promises)
- [Promise documentation - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)

### Template literals
### 템플릿 리터럴

Template literals은 하나 또는 여러줄의 string을 표현하는 표현 방식[*expression interpolation*](https://en.wikipedia.org/wiki/String_interpolation)입니다.

다른말로, 그것은 당신이 자바스크립트에서 편하게 쓸 수 있는 새로운 string문법입니다. (variables for instance)

#### Sample code

```js
const name = "Nick";
`Hello ${name}, the following expression is equal to four : ${2+2}`;

// Hello Nick, the following expression is equal to four: 4
```

#### External resources 
#### 외부 리소스들

- [String interpolation - ES6 Features](http://es6-features.org/#StringInterpolation)
- [ES6 Template Strings - Addy Osmani](https://developers.google.com/web/updates/2015/01/ES6-Template-Strings)

### Tagged template literals
### 태그에 사용되는 템플릿 리터럴

템플릿 태그들은 함수에서 [template literal](#template-literals)로 사용할 수 있습니다. 함수가 첫번째 파라미터는 템플릿의 변수들이  *strings* 배열처럼 표현될때, 그리고 그 다음 파라미터들의 값도 그럴때 이런 방법으로 불려집니다.
스프레드 방식  `...` 을 쓸 때도 사용합니다. [(Ref: MDN)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals#Tagged_template_literals).

> **Note :** 유명한 라이브러리 [styled-components](https://www.styled-components.com/) 이런 부분들에 많이 쓰여진다.

아래 그것들이 작동하는 약간의 샘플들이 있다.:
```js
function highlight(strings, ...values) {
  const interpolation = strings.reduce((prev, current) => {
    return prev + current + (values.length ? "<mark>" + values.shift() + "</mark>" : "");
  }, "");

  return interpolation;
}

const condiment = "jam";
const meal = "toast";

highlight`I like ${condiment} on ${meal}.`;
// "I like <mark>jam</mark> on <mark>toast</mark>."
```

더 흥미로운 예제 :
```js
function comma(strings, ...values) {
  return strings.reduce((prev, next) => {
    let value = values.shift() || [];
    value = value.join(", ");
    return prev + next + value;
  }, "");
}

const snacks = ['apples', 'bananas', 'cherries'];
comma`I like ${snacks} to snack on.`;
// "I like apples, bananas, cherries to snack on."
```

#### External resources
#### 외부 리소스들
- [Wes Bos on Tagged Template Literals](http://wesbos.com/tagged-template-literals/)
- [Library of common template tags](https://github.com/declandewet/common-tags)

### Imports / Exports
### 불러오기/ 내보내기

ES6 모듈들은 변수들에 접근하거나 함수 안에 모듈을 명시적으로 내보내거나 그것을 불러올때 사용합니다.
나는 이걸 MDN 리소스들을 찾아서 내보내고 불러 올 때 (see external resources below) 적극 추천합니다. 그것은 똑똑하고 완전한 것입니다.

#### Explanation with sample code

##### Named exports
##### exports들의 명명법

exports의 이름은 모듈의 여러가지 변수들을 내보낼때 사용할 수 있습니다. 

> **Note :** 당신은 단지 name-export [first-class citizens](https://en.wikipedia.org/wiki/First-class_citizen) 에 있는 이름을 사용할 수 있습니다.

```js
// mathConstants.js
export const pi = 3.14;
export const exp = 2.7;
export const alpha = 0.35;

// -------------

// myFile.js
import { pi, exp } from './mathConstants.js'; // Named import -- destructuring-like syntax
console.log(pi) // 3.14
console.log(exp) // 2.7

// -------------

// mySecondFile.js
import * as constants from './mathConstants.js'; // Inject all exported values into constants variable
console.log(constants.pi) // 3.14
console.log(constants.exp) // 2.7
```

불러올 때 이름들을 보면 *destructuring*처럼 보이는데. 그것들은 다른 문법을 가지고 있어서 같지는 않다. 그것들은 기본 변수나  *deep* destructuring를 지원히자 않는다.
게다가 , 너는 문법이 destructuring 안 에서 다르게 사용되고 있을때 별칭을 줄 수 있다 :

```js
import { foo as bar } from 'myFile.js'; // foo is imported and injected into a new bar variable
```

##### Default import / export
##### 기본 불러오기/ 내보내기

기본 내보내기에 관하여, 모듈당 기본 단 1개를 내보낸다. 기본 내보내기는 함수, 클래스 , 객체 또는 그밖에 것을 할 수 있다. 이 변수는 주요 내보내기 변수로 가장 간단하게 불러오기 할 때 고려되어진다. [Ref: MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export#Description)

```js
// coolNumber.js
const ultimateNumber = 42;
export default ultimateNumber;

// ------------

// myFile.js
import number from './coolNumber.js';
// Default export, independently from its name, is automatically injected into number variable;
console.log(number) // 42
```

함수 내보내기:

```js
// sum.js
export default function sum(x, y) {
  return x + y;
}
// -------------

// myFile.js
import sum from './sum.js';
const result = sum(1, 2);
console.log(result) // 3
```

#### External resources
#### 외부 리소스들

- [ES6 Modules in bulletpoints](https://ponyfoo.com/articles/es6#modules)
- [Export - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export)
- [Import - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import)
- [Understanding ES6 Modules](https://www.sitepoint.com/understanding-es6-modules/)
- [Destructuring special case - import statements](https://ponyfoo.com/articles/es6-destructuring-in-depth#special-case-import-statements)
- [Misunderstanding ES6 Modules - Kent C. Dodds](https://medium.com/@kentcdodds/misunderstanding-es6-modules-upgrading-babel-tears-and-a-solution-ad2d5ab93ce0)
- [Modules in JavaScript](http://exploringjs.com/es6/ch_modules.html#sec_modules-in-javascript)

### <a name="this_def"></a> JavaScript *this* 
### 자바스크립의 *this*

*this* 연산자는 다른 언어들과 다르게 움직이고, 대부분의 경우 함수를 부르는 방법에 따라 결정됩니다.([Ref: MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this)).

this의 개념은 미묘하면서 어려운 뜻을 많이 가지고 있습니다. 더 알아보려면, 당신은 아래 제공되는 외부 리소스들을 봐야 합니다. 그렇게 나는 내가 가진 *this*에 대한 내용을 제공할 것 입니다. 나는 this에 대한 팁을 [this article written by Yehuda Katz](http://yehudakatz.com/2011/08/11/understanding-javascript-function-invocation-and-this/)에서 배웠습니다.


```js
function myFunc() {
  ...
}

// After each statement, you find the value of *this* in myFunc

myFunc.call("myString", "hello") // "myString" -- first .call parameter value is injected into *this*

// In non-strict-mode
myFunc("hello") // window -- myFunc() is syntax sugar for myFunc.call(window, "hello")

// In strict-mode
myFunc("hello") // undefined -- myFunc() is syntax sugar for myFunc.call(undefined, "hello")
```

```js
var person = {
  myFunc: function() { ... }
}

person.myFunc.call(person, "test") // person Object -- first call parameter is injected into *this*
person.myFunc("test") // person Object -- person.myFunc() is syntax sugar for person.myFunc.call(person, "test")

var myBoundFunc = person.myFunc.bind("hello") // Creates a new function in which we inject "hello" in *this* value
person.myFunc("test") // person Object -- The bind method has no effect on the original method
myBoundFunc("test") // "hello" -- myBoundFunc is person.myFunc with "hello" bound to *this*
```

#### External resources
#### 외부 리소스들

- [Understanding JavaScript Function Invocation and "this" - Yehuda Katz](http://yehudakatz.com/2011/08/11/understanding-javascript-function-invocation-and-this/)
- [JavaScript this - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this)

### Class
### 클래스

자바스크립트는 [prototype-based](https://en.wikipedia.org/wiki/Prototype-based_programming) 언어입니다 (예를 들어 자바는 [class-based](https://en.wikipedia.org/wiki/Class-based_programming)언어).
ES6에서 자바스크립트의 class들이 구문상의 prototype-based 상속과 **not** 새로운 class-based 상속 모델([ref](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes))이 소개 되었습니다.

*class*는 만약 당신이 다른 언어들에서 많이 썼다면, 쉽게 에러 찾을때 였을 겁니다. 만약 당신이 자바스크립트의 class들을 이런 기초적인 일에 쓰는건 피하세요, 전적으로 다른 개념입니다. 

이 문서는 위에서 본 것 처럼 언어를 가르치려는건 아닙니다.
나는 당신이 프로토타입이 뭐고 그것들이 어떻게 작동하는지 안다는 가정하에 설명합니다. 
만약 당신이 모른다면, 외부 리소스들이랑 아래 샘플 코드들을 보시면 됩니다.

#### Samples
#### 샘플들

ES6이전의 prototype 문법 : 

```js
var Person = function(name, age) {
  this.name = name;
  this.age = age;
}
Person.prototype.stringSentence = function() {
  return "Hello, my name is " + this.name + " and I'm " + this.age;
}
```

ES6에서 클래스를 사용한 문법:

```js
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  stringSentence() {
    return `Hello, my name is ${this.name} and I am ${this.age}`;
  }
}

const myPerson = new Person("Manu", 23);
console.log(myPerson.age) // 23
console.log(myPerson.stringSentence()) // "Hello, my name is Manu and I'm 23
```

#### External resources
#### 외부 리소스들

prototype을 이해하기 위한 자료 : 

- [Understanding Prototypes in JS - Yehuda Katz](http://yehudakatz.com/2011/08/12/understanding-prototypes-in-javascript/)
- [A plain English guide to JS prototypes - Sebastian Porto](http://sporto.github.io/blog/2013/02/22/a-plain-english-guide-to-javascript-prototypes/)
- [Inheritance and the prototype chain - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)

class들을 이해하기 위한 자료 :

- [ES6 Classes in Depth - Nicolas Bevacqua](https://ponyfoo.com/articles/es6-classes-in-depth)
- [ES6 Features - Classes](http://es6-features.org/#ClassDefinition)
- [JavaScript Classes - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)

### `Extends` and `super` keywords
### `Extends`와 `super` 키워드

`extends` 는 클래스를 선언할때나 다른 클래스의 자식에 어떤 클래스를 만들때 사용 됩니다.([Ref: MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/extends)) 서브 클래스는 superclass의 모든 요소들을 상속됩니다. 게다가 새로운 요소 또는 상속된 뭔가를 수정해서 더할 수 있습니다.

`super`는 객체의 부모, 그것의 constructor포함 한 함수들을 부를때 사용됩니다. 

- `super`는 constructor에 `this` 를 사용 하기 전에 써야 합니다. 
- `super()` 부모 클래스의 constructor에 호출하세요. 만약에 당신이 클래스의 constructor에 부모의 constructor 인자를 보내기 원한다면, 당신은 `super(arguments)`이렇게 부르면 됩니다.
- 만약에 그 부모 클래스가 가진 메소드`X`를 부르고 싶다면, 당신은 자식 클래스에서 `super.X()` 이렇게 부르면 됩니다.

#### Sample Code

```js
class Polygon {
  constructor(height, width) {
    this.name = 'Polygon';
    this.height = height;
    this.width = width;
  }

  getHelloPhrase() {
    return `Hi, I am a ${this.name}`;
  }
}

class Square extends Polygon {
  constructor(length) {
    // Here, it calls the parent class' constructor with lengths
    // provided for the Polygon's width and height
    super(length, length);
    // Note: In derived classes, super() must be called before you
    // can use 'this'. Leaving this out will cause a reference error.
    this.name = 'Square';
    this.length = length;
  }

  getCustomHelloPhrase() {
    const polygonPhrase = super.getHelloPhrase(); // accessing parent method with super.X() syntax
    return `${polygonPhrase} with a length of ${this.length}`;
  }

  get area() {
    return this.height * this.width;
  }
}

const mySquare = new Square(10);
console.log(mySquare.area) // 100
console.log(mySquare.getHelloPhrase()) // 'Hi, I am a Square' -- Square inherits from Polygon and has access to its methods
console.log(mySquare.getCustomHelloPhrase()) // 'Hi, I am a Square with a length of 10'
```

**Note :** 만약 우리가 Square클래스에서 `super()`를 부르기전에 `this`를 사용하려고 하면, ReferenceError가 뜨는 걸 볼 수 있을 것 입니다:


```js
class Square extends Polygon {
  constructor(length) {
    this.height; // ReferenceError, super needs to be called first!

    // Here, it calls the parent class' constructor with lengths
    // provided for the Polygon's width and height
    super(length, length);

    // Note: In derived classes, super() must be called before you
    // can use 'this'. Leaving this out will cause a reference error.
    this.name = 'Square';
  }
}
```

#### External Resources 
#### 외부리소스들

- [Extends - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/extends)
- [Super operator - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/super)
- [Inheritance - MDN](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Inheritance)

### Async Await 

[Promises](#promises)에 따르면, *async / await* 이름의 비동기적 코드를 제어할 수 있는 새로운 문법입니다.

async/await 함수의 목적은  Promise들 안에서도 몇가지 동기적으로 사용되야 할 부분들을 간단하게 만들어 준 것입니다. 단 Promise와 비슷한 콜백 구조로 async/await은 하나의 세트고 promise들과 비슷합니다. Async 함수들은 *항상* promise들을 반환합니다.([Ref: MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function))

> **Note :** 당신은 async / await를 이해하는 것은 promise들이 무슨 일을 어떻게 하는지 이해하는 것에 달려있습니다. 


> **Note 2:** [*await* must be used in an *async* function](https://hackernoon.com/6-reasons-why-javascripts-async-await-blows-promises-away-tutorial-c7ec10518dd9#f3f0), 비동기 함수 안쪽에 있지 않다면 당신의 코드 상위 레벨에 await을 쓸 수 없다는 걸 의미합니다.

#### Sample code

```js
async function getGithubUser(username) { // async keyword allows usage of await in the function and means function returns a promise
  const response = await fetch(`https://api.github.com/users/${username}`); // Execution is paused here until the Promise returned by fetch is resolved
  return response.json();
}

getGithubUser('mbeaudru')
  .then(user => console.log(user)) // logging user response - cannot use await syntax since this code isn't in async function
  .catch(err => console.log(err)); // if an error is thrown in our async function, we will catch it here
```

#### Explanation with sample code 
#### 설명과 샘플코드

*Async / Await* 은 promise들로 만들어집니다. 그러나 그것들은 좀 더 피하기 힘든 코드를 만들 때 쓰면 됩니다.

비동기 함수에서 *async*를 표시하면 항상 *Promise*를 반환할 것입니다. 당신은 *async* 함수 안에  *await* 을 쓸 수 있고 그 함수 줄을 만나면 promise로 resolves또는 reject 같은 표현을 반환해 줍니다.

```js
async function myFunc() {
  // we can use await operator because this function is async
  return "hello world";
}

myFunc().then(msg => console.log(msg)) // "hello world" -- myFunc's return value is turned into a promise because of async operator
```

비동기 함수에 *return*을 보면 Promise의 return값을 줍니다. 만약에 비동기함수에 에러를 던지면, promise의 값은 *rejected*로 변할 것입니다. 만약 비동기 함수에서 값 없음이 반환된다면, Promise는 비동기 함수를 실행하고 값이 없음을 받아 해결을 리턴 할 것 입니다.  

*await*은 *async*함수 안에서 *Promise*가 완료 되길 기다릴 때 사용합니다. 실행코드를 만나 promise가 완료 될 면 끝납니다.

> **Note :** *fetch*는 AJAX요청 시 Promise를 반환하는 함수입니다.
 
github user가  fetch로 어떻게 promise들을 처음에 사용하는지 보자: 

```js
function getGithubUser(username) {
  return fetch(`https://api.github.com/users/${username}`).then(response => response.json());
}

getGithubUser('mbeaudru')
  .then(user => console.log(user))
  .catch(err => console.log(err));
```

여기에 *async / await*와 같이 쓴 것: 

```js
async function getGithubUser(username) { // promise + await keyword usage allowed
  const response = await fetch(`https://api.github.com/users/${username}`); // Execution stops here until fetch promise is fulfilled
  return response.json();
}

getGithubUser('mbeaudru')
  .then(user => console.log(user))
  .catch(err => console.log(err));
```

*async / await* 문법은 특히 좋은데, 당신이 chain promises 필요로 할 때 입니다. 

예를들어서, 만약 당신이 블로그 글에 기본데이터 토큰을 얻은 담에 작가의 정보가 필요할 때:  

> **Note :** *await* 표현은 괄호로 감싸서 같은 줄에 값이 resolved 됐는지 불러 볼 수 있습니다.

```js
async function fetchPostById(postId) {
  const token = (await fetch('token_url')).json().token;
  const post = (await fetch(`/posts/${postId}?token=${token}`)).json();
  const author = (await fetch(`/users/${post.authorId}`)).json();

  post.author = author;
  return post;
}

fetchPostById('gzIrzeo64')
  .then(post => console.log(post))
  .catch(err => console.log(err));
```

##### Error handling 
##### 에러 다루기

우리는 *await* 으로 표현된 블록 안에 잡히지 않는 부분을 위해 *try / catch* 를 추가합니다. -  *async* 함수에 *await*를 대기하는 동안 어떤걸 던지는 상관없이 promise는 *async* 함수에 reject를 던질 것입니다. 비동기 함수에서 `throw` 이름으로 promise의 reject를 던지는 걸 사용해 보세요 [(Ref: PonyFoo)](https://ponyfoo.com/articles/understanding-javascript-async-await#error-handling).

> **Note :** Promise들 처럼 행동함!!

Promise들과 함께 여기에 에러 chain 사용법이 있습니다. : 

```js
function getUser() { // This promise will be rejected!
  return new Promise((res, rej) => rej("User not found !"));
}

function getAvatarByUsername(userId) {
  return getUser(userId).then(user => user.avatar);
}

function getUserAvatar(username) {
  return getAvatarByUsername(username).then(avatar => ({ username, avatar }));
}

getUserAvatar('mbeaudru')
  .then(res => console.log(res))
  .catch(err => console.log(err)); // "User not found !"
```

*async / await* 과 함께 사용하기:

```js
async function getUser() { // The returned promise will be rejected!
  throw "User not found !";
}

async function getAvatarByUsername(userId) => {
  const user = await getUser(userId);
  return user.avatar;
}

async function getUserAvatar(username) {
  var avatar = await getAvatarByUsername(username);
  return { username, avatar };
}

getUserAvatar('mbeaudru')
  .then(res => console.log(res))
  .catch(err => console.log(err)); // "User not found !"
```

#### External resources
#### 외부 리소스들

- [Async/Await - JavaScript.Info](https://javascript.info/async-await)
- [ES7 Async/Await](http://rossboucher.com/await/#/)
- [6 Reasons Why JavaScript’s Async/Await Blows Promises Away](https://hackernoon.com/6-reasons-why-javascripts-async-await-blows-promises-away-tutorial-c7ec10518dd9)
- [JavaScript awaits](https://dev.to/kayis/javascript-awaits)
- [Using Async Await in Express with Node 8](https://medium.com/@Abazhenov/using-async-await-in-express-with-node-8-b8af872c0016)
- [Async Function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)
- [Await](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await)
- [Using async / await in express with node 8](https://medium.com/@Abazhenov/using-async-await-in-express-with-node-8-b8af872c0016)

### Truthy / Falsy
### 참/거짓

자바스크립트에서 참 또는 거짓값은 boolean을 통해 만들어진 값이다. boolean 문맥의 예는 ```if``` 쓰는거에 따라 나눠집니다.:

모든 값은 ```true```가 아닌 한 아래 값들과 같음:

- ```false```
- ```0```
- ```""``` (empty string)
- ```null```
- ```undefined```
- ```NaN```

 *boolean context*에 대한 예시:

- ```if``` 상태 알아보기

```js
if (myVar) {}
```

```myVar```는 어떤 것[first-class citizen](https://en.wikipedia.org/wiki/First-class_citizen) (변수, 함수, 블린)이든 될 수 있다. 그러나 그것은 boolean으로 될 것 입니다. 그것은 boolean문맥 안에 있기 때문입니다.

- **NOT** 을 표현하는 방법 ```!``` 

이 표현은 false를 반환합니다. 만약 그것을 연산하는 값이 true이면 반환 값도 true입니다.

```js
!0 // true -- 0 is falsy so it returns true
!!0 // false -- 0 is falsy so !0 returns true so !(!0) returns false
!!"" // false -- empty string is falsy so NOT (NOT false) equals false
```

- *Boolean* 객체 생성자

```js
new Boolean(0) // false
new Boolean(1) // true
```

- 삼항 연산자

```js
myVar ? "truthy" : "falsy"
```

myVar는 블린을 넘기는 곳에 있습니다.

조심스럽게 두값을 비교할. 그 객체 값은 (true로 던저지는)은 **not**으로 던져진 블린값이다.그러나 그것은 그것은 원래값을 사용하는 것으로 바뀐다. [ToPrimitives specification](http://javascript.info/object-toprimitive)
내부적으로 객체의 블린값을 비교할 때는`[] == true`처럼 쓰거나 `[].toString() == true` 처럼 쓴 다.


```js
let a = [] == true // a is false since [].toString() give "" back.
let b = [1] == true // b is true since [1].toString() give "1" back.
let c = [2] == true // c is false since [2].toString() give "2" back.
```

#### External resources
#### 외부 리소스들

- [Truthy (MDN)](https://developer.mozilla.org/en-US/docs/Glossary/Truthy)
- [Falsy (MDN)](https://developer.mozilla.org/en-US/docs/Glossary/Falsy)
- [Truthy and Falsy values in JS - Josh Clanton](http://adripofjavascript.com/blog/drips/truthy-and-falsy-values-in-javascript.html)

### Anamorphisms and Catamorphisms

#### Anamorphisms

Anamorphisms은 어떤 객체를 더 복잡한 구조의 객체형으로 조합해주는 함수 입니다. 그것은 *unfolding* 과정으로 간단한 구조에서 더 복잡한 뭔가를 하는 것을 말합니다.
안 묶여있는 숫자값을 묶을때 쓰세요. 그 숫자는 우리가 초기화 시킨 객체랑 더 복잡한 구조를 통해 묶은 숫자들입니다. 

**Sample code**

```js
function downToOne(n) {
  const list = [];

  for (let i = n; i > 0; --i) {
    list.push(i);
  }

  return list;
}

downToOne(5)
  //=> [ 5, 4, 3, 2, 1 ]
```

#### Catamorphisms

Catamorphisms은 Anamorphisms의 반대입니다., 그걸로 그것들은 더 복잡하고  *fold*된 걸 간단한 구조로 된 객체로 해준다. `product`예시를 보면 숫자들의 목록을 하나의 숫자로 반환해서 준다.

**Sample code**

```js
function product(list) {
  let product = 1;

  for (const n of list) {
    product = product * n;
  }

  return product;
}

product(downToOne(5)) // 120
```

#### External resources (외부 리소스들)

* [Anamorphisms in JavaScript](http://raganwald.com/2016/11/30/anamorphisms-in-javascript.html)
* [Anamorphism](https://en.wikipedia.org/wiki/Anamorphism)
* [Catamorphism](https://en.wikipedia.org/wiki/Catamorphism)

### Generators

`downToOne` 함수를 Generator를 사용해 다르게 쓰는 방법이 있습니다. `Generator`객체를 인스턴스화 해서 `function *`를 선언해서 사용해야 합니다. 
Generator들은 빠져나오고, 다시 또 입력하고 새로 만들어진 값을 다른데 저장할 수 있는 함수입니다. 

예를 들어, `downToOne` 위에껄로 다시 쓸 수 있습니다.:

```js
function * downToOne(n) {
  for (let i = n; i > 0; --i) {
    yield i;
  }
}

[...downToOne(5)] // [ 5, 4, 3, 2, 1 ]
```

Generator들은 반복되는 객체를 반환합니다. 반복되는 거에 `next()`함수를 부를때, 그건 처음으로 `yield` 이 표현이 나올때까지만 실행하고,  지정된 어떤 값을 `yield*`와  반복해서 반환하고, 또 다른 generator 함수로 위임합니다.
generator안에서 `return`을 호출할때 그것은 그것은 generator를 지난 값을 표시할 것입니다. 게다가 새로 리턴할 값이 없어도 `next()`로 부를 것입니다.

**Sample code**

```js
// Yield Example
function * idMaker() {
  var index = 0;
  while (index < 2) {
    yield index;
    index = index + 1;
  }
}

var gen = idMaker();

gen.next().value; // 0
gen.next().value; // 1
gen.next().value; // undefined
```

`yield*` 표현은 함수의 반복문을 도는 동안 generator에서 또다른 generator를 부를 수 있게 해줍니다.

```js
// Yield * Example
function * genB(i) {
  yield i + 1;
  yield i + 2;
  yield i + 3;
}

function * genA(i) {
  yield i;
  yield* genB(i);
  yield i + 10;
}

var gen = genA(10);

gen.next().value; // 10
gen.next().value; // 11
gen.next().value; // 12
gen.next().value; // 13
gen.next().value; // 20
```

```js
// Generator Return Example
function* yieldAndReturn() {
  yield "Y";
  return "R";
  yield "unreachable";
}

var gen = yieldAndReturn()
gen.next(); // { value: "Y", done: false }
gen.next(); // { value: "R", done: true }
gen.next(); // { value: undefined, done: true }
```

#### External resources (외부 리소스들)

* [Mozilla MDN Web Docs, Iterators and Generators](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Iterators_and_Generators#Generators)

### Static Methods (static 메소드)

#### Short explanation (간략한 설명)

`static`이라는 단어는 클래스 안에서 static 메소드를 선언 할 때 사용됩니다. Static메소드들은 클래스에서 클래스 객체에 속하는 함수이고,해당 클래스의 인스턴스에는 사용할 수 없습니다.

#### Sample code

```js
class Repo{
  static getName() {
    return "Repo name is modern-js-cheatsheet"
  }
}

// Note that we did not have to create an instance of the Repo class
console.log(Repo.getName()) // Repo name is modern-js-cheatsheet

let r = new Repo();
console.log(r.getName()) // Uncaught TypeError: r.getName is not a function
```

#### Detailed explanation (자세한 설명)

Static 메소드들은 속에 또다른 static 메소드를 `this` 로 불러서 쓸수 있고, 이건 non-static메소드에서 작동하지 않는다. Non-static 메소드들은 직접적으로 static메소드들에 접근해  `this`를 사용 할 수는 없습니다.

##### Calling other static methods from a static method. (static메소드에서 또 다른 static 메소드를 부르는 것)

또 다른 static메소드로 부터 static메소드를 불러 `this` 를 그렇게 사용할 수 있음 : 

```js
class Repo{
  static getName() {
    return "Repo name is modern-js-cheatsheet"
  }

  static modifyName(){
    return this.getName() + '-added-this'
  }
}

console.log(Repo.modifyName()) // Repo name is modern-js-cheatsheet-added-this
```

##### Calling static methods from non-static methods. (non-static메소드에서 static메소드를 부르는 것)

Non-static 메소드들이 static 메소드들을 부르는 2가지 방법:

1. ###### 클래스 이름을 사용하는 것

non-static 메소드에 static 메소드로 접근해 가죠오는 건 우리는 클래스 이름을 사용 한다. 그리고 static 메소드를 다음과 같이 부른다. e.g `ClassName.StaticMethodName`

```js
class Repo{
  static getName() {
    return "Repo name is modern-js-cheatsheet"
  }

  useName(){
    return Repo.getName() + ' and it contains some really important stuff'
  }
}

// we need to instantiate the class to use non-static methods
let r = new Repo()
console.log(r.useName()) // Repo name is modern-js-cheatsheet and it contains some really important stuff
```

2. ###### constructor를 사용하는 것

Static 메소드들은 constructor객체에 요소로 부를 수 있습니다.

```js
class Repo{
  static getName() {
    return "Repo name is modern-js-cheatsheet"
  }

  useName(){
    // Calls the static method as a property of the constructor
    return this.constructor.getName() + ' and it contains some really important stuff'
  }
}

// we need to instantiate the class to use non-static methods
let r = new Repo()
console.log(r.useName()) // Repo name is modern-js-cheatsheet and it contains some really important stuff
```

#### External resources (외부 리소스들)
- [static keyword- MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/static)
- [Static Methods- Javascript.info](https://javascript.info/class#static-methods)
- [Static Members in ES6- OdeToCode](http://odetocode.com/blogs/scott/archive/2015/02/02/static-members-in-es6.aspx)

## Glossary (어휘)

### <a name="scope_def"></a> Scope (범위)

어떤 값과 표현들이 문맥상 "변수",참조 가능 한 범위입니다. 만약 변수또는 다른 표현이  "in the current scope," 아니면  그것을 사용할 수 없습니다.

Source: [MDN](https://developer.mozilla.org/en-US/docs/Glossary/Scope)

### <a name="mutation_def"></a> Variable mutation (변수 변화)

변수는 말그대로 변하고 그것의 초기값에서 나중에 가지는 값으로 변하는 걸 말합니다.

```js
var myArray = [];
myArray.push("firstEl") // myArray is being mutated
```

변수가 변하지 않으면 *immutable* 이라고 말합니다. 

[Check MDN Mutable article](https://developer.mozilla.org/en-US/docs/Glossary/Mutable) 더 상세하게.
