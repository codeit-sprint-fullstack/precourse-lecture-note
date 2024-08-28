# 3. JavaScript로 데이터 다루기

> 코드잇 영상으로 확인하기 : [프로그래밍과 데이터 in JavaScript](https://www.codeit.kr/topics/javascript-programming-and-data)

## 개요

> ❤️‍🔥 **학습 목표**
>
> - JavaScript의 객체, 배열, 자료형 심화 개념을 깊이 있게 이해하고 활용할 수 있는 능력을 기르기
> - 복잡한 자료 구조와 제어문을 사용해 실제 프로그래밍 문제를 해결하는 능력을 갖추기

> ✅ 그전에 잠깐!
>
> 프리코스 토픽을 다 들으신 분들이라면 동일한 내용이니 패스하셔도 좋습니다 !

## 목차

- [3. JavaScript로 데이터 다루기](#3-javascript로-데이터-다루기)
  - [개요](#개요)
  - [목차](#목차)
  - [객체](#객체)
    - [객체와 프로퍼티](#객체와-프로퍼티)
    - [객체 다루기](#객체-다루기)
    - [객체와 메소드](#객체와-메소드)
    - [for...in 반복문 주의사항](#forin-반복문-주의사항)
  - [내장 객체](#내장-객체)
    - [Date 객체](#date-객체)
  - [배열](#배열)
    - [배열의 개념](#배열의-개념)
    - [배열 메소드](#배열-메소드)
    - [for...of 반복문](#forof-반복문)
  - [자료형 심화](#자료형-심화)
    - [숫자형 메소드](#숫자형-메소드)
    - [Math 객체](#math-객체)
    - [문자열 심화](#문자열-심화)
    - [기본형과 참조형](#기본형과-참조형)
      - [기본형 (Primitive Type)](#기본형-primitive-type)
      - [참조형 (Reference Type)](#참조형-reference-type)
    - [참조형 데이터 복사](#참조형-데이터-복사)
      - [1. 얕은 복사 (Shallow Copy)](#1-얕은-복사-shallow-copy)
      - [2. 깊은 복사 (Deep Copy)](#2-깊은-복사-deep-copy)
    - [변수 선언: `var`, `let`, `const`](#변수-선언-var-let-const)
      - [1. `var`](#1-var)
      - [2. `let`](#2-let)
      - [3. `const`](#3-const)
    - [`var`, `let`, `const`의 사용 권장 사항](#var-let-const의-사용-권장-사항)
    - [퀴즈 풀며 복습하기](#퀴즈-풀며-복습하기)

---

## 객체

### 객체와 프로퍼티

- **객체(Object)**: 관련된 데이터나 기능을 `key: value` 형식의 **프로퍼티**로 묶어서 관리할 수 있는 구조입니다.

  ```javascript
  console.log(
    typeof {
      name: "코드잇",
      bornYear: 2017,
      isVeryNice: true,
      worstCourse: null,
      bestCourse: {
        title: "자바스크립트 프로그래밍 기초",
        language: "JavaScript",
      },
    }
  ); // 출력: object
  ```

### 객체 다루기

- **데이터 접근**:

  - **점 표기법(`.`)**: `objectName.propertyName` 형식으로 사용하며, 변수를 사용할 수 없습니다.
  - **대괄호 표기법(`[]`)**: `objectName['propertyName']` 형식으로 사용하며, 프로퍼티 이름을 문자열로 전달해야 합니다.

- **데이터 조작**:
  - 데이터 추가: `objectName.propertyName = propertyValue`
  - 데이터 삭제: `delete objectName.propertyName`
  - **in 연산자**: 특정 프로퍼티가 객체에 존재하는지 확인합니다. `propertyName in objectName`

### 객체와 메소드

- **메소드(Method)**: 객체의 프로퍼티 중 함수가 할당된 경우 이를 메소드라고 합니다.
  ```javascript
  let person = {
    name: "Alice",
    greet: function () {
      console.log("Hello!");
    },
  };
  person.greet(); // "Hello!"
  ```

### for...in 반복문 주의사항

- **for...in**은 객체의 모든 열거 가능한 프로퍼티를 순회합니다.
- **주의사항**:
  - 정수형 프로퍼티는 오름차순으로 먼저 정렬되고, 나머지 프로퍼티는 추가된 순서대로 정렬됩니다.(즉, 자동으로 정렬되는 특성이 있음. 대부분의 경우에는 의도치 않은 결과를 가져올 수도 있기 때문에, 일반적으로 정수형 프로퍼티는 잘 사용되지 않음)
  - 배열에는 사용하지 않는 것이 좋으며, 배열에는 **for...of**를 사용하는 것이 더 적합합니다.

---

## 내장 객체

### Date 객체

- **Date 객체**: JavaScript의 내장 객체로, 날짜와 시간을 다루기 위해 사용됩니다.
  - **생성 방법**: `new Date();`
  - 다양한 형식의 입력값을 받아 객체를 생성할 수 있습니다.
  - **주요 메소드**:
    - `getTime()`: 1970년 1월 1일 00:00:00 UTC부터 몇 밀리초가 지났는지 반환합니다.
    - `getFullYear()`, `getMonth()`, `getDate()`, `getDay()`: 각각 연도, 월, 날짜, 요일을 반환합니다.
    - `set`으로 시작하는 메소드를 통해 객체의 정보를 수정할 수 있습니다.
    - `toLocaleDateString()`, `toLocaleTimeString()`, `toLocaleString()`: 로컬 형식으로 날짜와 시간을 출력합니다.

---

## 배열

### 배열의 개념

- **배열(Array)**: 여러 값을 하나의 변수에 저장할 수 있는 자료 구조로, 각 값은 인덱스를 통해 접근됩니다.
  ```javascript
  let fruits = ["Apple", "Banana", "Cherry"];
  console.log(fruits[0]); // "Apple"
  ```

### 배열 메소드

- 자주 사용하는 배열 메소드:
  - `.splice(startIndex, deleteCount, 추가할값...)`: 배열의 요소를 제거하거나 추가합니다.
  - `.push()`, `.pop()`: 배열의 마지막에 요소를 추가하거나 제거합니다.
  - `.shift()`, `.unshift()`: 배열의 첫 번째 요소를 추가하거나 제거합니다.
  - `.indexOf(item)`, `.lastIndexOf(item)`: 배열에서 특정 요소의 인덱스를 찾습니다.
  - `.includes(item)`: 배열에 특정 요소가 포함되어 있는지 확인합니다.
  - `.reverse()`: 배열의 순서를 뒤집습니다.

### for...of 반복문

- **for...of** 반복문은 배열의 각 요소를 순회하며 값을 불러옵니다.
  ```javascript
  for (let fruit of fruits) {
    console.log(fruit);
  }
  ```

---

## 자료형 심화

### 숫자형 메소드

- **숫자형 메소드**:
  - `toFixed(n)`: 소수점 이하 n자리까지 반올림한 값을 문자열로 반환합니다.
  - `toString(n)`: n진수로 변환한 값을 문자열로 반환합니다.

### Math 객체

- **Math 객체**: 수학적 연산을 위한 내장 객체입니다.
  - 주요 메소드: `Math.abs()`, `Math.max()`, `Math.min()`, `Math.pow()`, `Math.sqrt()`, `Math.round()`, `Math.floor()`, `Math.ceil()`, `Math.random()`

### 문자열 심화

- **문자열 메소드**:
  - `.toUpperCase()`, `.toLowerCase()`: 대소문자 변환
  - `.trim()`: 양쪽 공백 제거
  - `.slice(start, end)`: 문자열의 일부를 추출

### 기본형과 참조형

JavaScript에서 변수에 저장되는 데이터는 **기본형(Primitive Type)**과 **참조형(Reference Type)**으로 나뉩니다.

#### 기본형 (Primitive Type)

- **기본형 값**: 숫자, 문자열, 불린, `null`, `undefined`, `symbol`, `bigint` 등이 있습니다.
- **특징**: 변수에 값 자체가 저장됩니다. 기본형 데이터는 불변(immutable)하며, 해당 값이 저장된 변수를 다른 변수에 할당하면, 새로운 변수에 복사된 값이 저장됩니다.

  ```javascript
  let a = 10;
  let b = a; // b에 10이 복사됨
  b = 20;
  console.log(a); // 10 (변하지 않음)
  ```

#### 참조형 (Reference Type)

- **참조형 값**: 객체, 배열, 함수 등이 포함됩니다.
- **특징**: 변수에는 실제 값이 아닌 데이터의 **주소값**이 저장됩니다. 참조형 데이터를 다른 변수에 할당하면, 두 변수는 동일한 주소를 참조하게 됩니다. 따라서 하나의 변수를 통해 데이터를 변경하면, 동일한 주소를 참조하는 다른 변수의 데이터도 변경됩니다.

  ```javascript
  let obj1 = { name: "Alice" };
  let obj2 = obj1; // obj2에 obj1의 주소값이 복사됨
  obj2.name = "Bob";
  console.log(obj1.name); // "Bob" (변경됨)
  ```

### 참조형 데이터 복사

때로는 참조형 데이터를 그대로 복사하여 서로 독립적인 값을 갖도록 하고 싶을 때가 있습니다. 이는 **얕은 복사**와 **깊은 복사**로 나뉩니다.

#### 1. 얕은 복사 (Shallow Copy)

- **배열 복사**: `slice()` 메소드를 사용하여 배열을 복사할 수 있습니다. 이 메소드는 배열의 원본을 변경하지 않고, 동일한 요소를 가진 새로운 배열을 생성합니다.

  ```javascript
  let arr1 = [1, 2, 3];
  let arr2 = arr1.slice(); // 새로운 배열 복사
  arr2.push(4);
  console.log(arr1); // [1, 2, 3] (변경되지 않음)
  console.log(arr2); // [1, 2, 3, 4]
  ```

- **객체 복사**: `Object.assign()` 메소드를 사용하여 객체를 복사할 수 있습니다. 첫 번째 매개변수로 빈 객체를 전달하고, 두 번째 매개변수로 복사할 객체를 전달하면, 새로운 객체가 생성됩니다.

  ```javascript
  let obj1 = { title: "JavaScript" };
  let obj2 = Object.assign({}, obj1); // 새로운 객체 복사
  obj2.title = "Python";
  console.log(obj1.title); // "JavaScript" (변경되지 않음)
  console.log(obj2.title); // "Python"
  ```

#### 2. 깊은 복사 (Deep Copy)

- **문제점**: 얕은 복사는 객체나 배열 내부에 다른 객체나 배열이 중첩된 경우, 중첩된 참조형 값은 여전히 동일한 주소를 참조합니다. 이로 인해 예상치 못한 결과가 발생할 수 있습니다.

  ```javascript
  let obj1 = {
    title: "JavaScript",
    prerequisites: ["HTML", "CSS"],
  };
  let obj2 = Object.assign({}, obj1);
  obj2.prerequisites.push("React");
  console.log(obj1.prerequisites); // ["HTML", "CSS", "React"] (변경됨)
  ```

- **깊은 복사 방법**: 깊은 복사를 위해서는 객체 내부의 모든 중첩 객체와 배열까지 복사해야 합니다. 이를 위해서는 재귀적 방법을 사용할 수 있으며, 라이브러리(예: Lodash의 `_.cloneDeep`)를 활용하기도 합니다.

### 변수 선언: `var`, `let`, `const`

JavaScript에서 변수를 선언하는 방법에는 `var`, `let`, `const` 세 가지가 있습니다. 이들은 각각의 특성과 사용 목적에 따라 다르게 사용됩니다.

#### 1. `var`

- **중복 선언 허용**: 동일한 변수명을 중복해서 선언할 수 있습니다.
  ```javascript
  var myVariable = "codeit";
  var myVariable = "Codeit!"; // 중복 선언 허용
  ```
- **함수 스코프**: `var`는 함수 스코프를 따르며, 함수 내부에서 선언된 변수는 함수 외부에서 접근할 수 없습니다. 하지만, 블록 스코프(`if`, `for`, `while` 블록 등)를 무시합니다.
  ```javascript
  function example() {
    var x = 10;
    if (true) {
      var x = 20;
      console.log(x); // 20
    }
    console.log(x); // 20
  }
  example();
  ```
- **호이스팅(Hoisting)**: `var`로 선언된 변수는 선언이 끌어올려지며, 선언 전에 변수를 사용할 수 있습니다. 단, 초기화는 호이스팅되지 않으므로 `undefined` 값이 반환됩니다.
  ```javascript
  console.log(myVariable); // undefined
  var myVariable = 2;
  ```

#### 2. `let`

- **블록 스코프**: `let`은 블록 스코프를 따릅니다. 이는 변수가 선언된 블록 내부에서만 접근 가능함을 의미합니다.
  ```javascript
  if (true) {
    let x = 10;
    console.log(x); // 10
  }
  console.log(x); // ReferenceError: x is not defined
  ```
- **중복 선언 불가**: `let`으로 선언된 변수는 동일한 스코프 내에서 중복 선언이 불가능합니다.
  ```javascript
  let myVariable = "codeit";
  let myVariable = "Codeit!"; // SyntaxError: Identifier 'myVariable' has already been declared
  ```
- **호이스팅**: `let` 변수도 호이스팅되지만, 초기화 전에 접근할 수 없어서 `Temporal Dead Zone (TDZ)`에 의해 오류가 발생합니다.
  ```javascript
  console.log(myVariable); // ReferenceError: Cannot access 'myVariable' before initialization
  let myVariable = 2;
  ```

#### 3. `const`

- **상수(Immutable Binding)**: `const`로 선언된 변수는 재할당이 불가능합니다. 변수 자체는 상수로 취급되지만, 변수에 할당된 객체나 배열의 프로퍼티는 변경이 가능합니다.
  ```javascript
  const x = { name: "Codeit" };
  x.birth = 2017; // 가능
  x = {}; // TypeError: Assignment to constant variable.
  ```
- **블록 스코프**: `const`는 `let`과 마찬가지로 블록 스코프를 따릅니다.
- **중복 선언 불가**: 동일한 스코프 내에서 중복 선언이 불가능합니다.
  ```javascript
  const myVariable = "codeit";
  const myVariable = "Codeit!"; // SyntaxError: Identifier 'myVariable' has already been declared
  ```
- **호이스팅**: `const`도 호이스팅되지만, `let`과 마찬가지로 `Temporal Dead Zone`에 의해 초기화 전에 접근할 수 없습니다.

### `var`, `let`, `const`의 사용 권장 사항

- **`var` 사용 지양**: `var`는 함수 스코프, 호이스팅 등으로 인한 예상치 못한 버그가 발생할 수 있기 때문에, 가급적 사용을 피하는 것이 좋습니다.
- **`let` 사용 권장**: 변수가 변경될 가능성이 있을 때, 재할당이 필요할 때는 `let`을 사용합니다.
- **`const` 기본 사용**: 재할당이 필요 없는 변수는 `const`로 선언하여 코드의 안정성을 높입니다.

이 세 가지 개념을 이해하고 상황에 맞게 적절히 사용하는 것이 중요합니다. `const`와 `let`을 기본으로 사용하고, 특별한 이유가 없는 한 `var`는 사용하지 않는 것이 현대적인 JavaScript 코드 작성의 권장 사항입니다.

### 퀴즈 풀며 복습하기

- [순이들의 시험결과](https://www.codeit.kr/topics/javascript-programming-and-data/lessons/3443)
- [우수사원 재상이](https://www.codeit.kr/topics/javascript-programming-and-data/lessons/3446)
- [팀 나누기](https://www.codeit.kr/topics/javascript-programming-and-data/lessons/3459)
- [레시피 만들기](https://www.codeit.kr/topics/javascript-programming-and-data/lessons/3472)
- [거스름돈 구하기](https://www.codeit.kr/topics/javascript-programming-and-data/lessons/3478)
