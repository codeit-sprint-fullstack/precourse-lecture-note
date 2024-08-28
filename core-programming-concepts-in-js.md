# 2. JavaScript 핵심 개념

> 코드잇 영상으로 확인하기 : [프로그래밍 핵심 개념 in JavaScript](https://www.codeit.kr/topics/core-concept-of-javascript-programming)

## 개요

> ❤️‍🔥 **학습 목표**
>
> - 자료형, 추상화, 제어문에 대해 익히기
> - JavaScript의 보다 복잡한 기능을 이해하고 사용하는 능력 갖추기

> ✅ 그전에 잠깐!
>
> 프리코스 토픽을 다 들으신 분들이라면 동일한 내용이니 패스하셔도 좋습니다 !

## 목차

- [2. JavaScript 핵심 개념](#2-javascript-핵심-개념)
  - [개요](#개요)
  - [목차](#목차)
  - [자료형](#자료형)
    - [숫자형](#숫자형)
    - [문자열](#문자열)
    - [형 변환](#형-변환)
    - [문자열 포매팅](#문자열-포매팅)
    - [불린형](#불린형)
    - [타입 검사 함수](#타입-검사-함수)
    - [null과 undefined](#null과-undefined)
    - [자료형 퀴즈 (5분)](#자료형-퀴즈-5분)
  - [추상화](#추상화)
    - [변수 지정 연산자](#변수-지정-연산자)
    - [함수 실행 순서](#함수-실행-순서)
    - [return vs console.log](#return-vs-consolelog)
    - [옵셔널 파라미터](#옵셔널-파라미터)
    - [Syntactic Sugar](#syntactic-sugar)
    - [변수의 범위 (Scope)](#변수의-범위-scope)
    - [상수](#상수)
    - [함수 변수 퀴즈 (5분)](#함수-변수-퀴즈-5분)
  - [제어문](#제어문)
    - [while 반복문](#while-반복문)
    - [if문](#if문)
    - [elif문](#elif문)
    - [break문](#break문)
    - [continue문](#continue문)
    - [switch문](#switch문)
  - [피보나치 수열 퀴즈 (10분)](#피보나치-수열-퀴즈-10분)

---

## 자료형

### 숫자형

JavaScript에서 숫자형 데이터는 다양한 연산이 가능합니다.

- **덧셈, 뺄셈, 곱셈, 나눗셈**

  ```javascript
  let a = 10;
  let b = 3;
  console.log(a + b); // 13
  console.log(a - b); // 7
  console.log(a * b); // 30
  console.log(a / b); // 3.3333...
  ```

- **거듭제곱**

  ```javascript
  console.log(a ** b); // 1000 (10^3)
  ```

- **몫과 나머지**

  ```javascript
  console.log(Math.floor(a / b)); // 3 (몫)
  console.log(a % b); // 1 (나머지)
  ```

- **반올림**
  ```javascript
  console.log(Math.round(3.5)); // 4
  ```

### 문자열

문자열은 텍스트 데이터를 표현하며, 따옴표로 감싸서 표현합니다.

- **문자열 연결**

  ```javascript
  let greeting = "Hello" + " " + "World!";
  console.log(greeting); // "Hello World!"

  console.log("5" + "3"); // 8이 아닌 53이 출력됩니다.
  ```

- **Syntax Error 및 백슬래시 사용**
  - 따옴표 안에 따옴표를 넣어야 할 때는 백슬래시(`\`)를 사용해 처리합니다.
  ```javascript
  let quote = 'He said, "JavaScript is awesome!"';
  console.log(quote); // He said, "JavaScript is awesome!"
  ```

### 형 변환

JavaScript에서 형 변환은 자동으로 이루어질 수도 있고, 수동으로 변환할 수도 있습니다.

- **수동 형 변환**

  - `Number(값)`을 사용하여 문자열을 숫자로 변환할 수 있습니다. 변환하려는 문자열이 숫자 형태가 아닐 경우 `NaN`이 반환됩니다.

  ```javascript
  let str = "123";
  let num = Number(str); // 문자열을 숫자로 변환
  console.log(num); // 123
  ```

  - `Boolean(값)`을 사용하여 값을 불린형으로 변환할 수 있습니다. 대부분의 값은 `true`로 변환되지만, 일부 값은 `false`로 평가됩니다.
    - `falsy` 값들:
      - 빈 문자열 `""`
      - 숫자 `0`, `NaN`
      - `null`, `undefined`

  ```javascript
  console.log(Boolean("")); // false
  console.log(Boolean(0)); // false
  console.log(Boolean("Hi")); // true
  ```

- **자동 형 변환**

  - `+` 연산자를 사용할 때, 하나라도 문자열이 포함되면 모든 요소가 자동으로 문자열로 변환됩니다.

  ```javascript
  console.log("5" + 10); // "510" (숫자 10이 문자열로 변환됨)
  ```

  - 연산 중 `NaN`이 포함되면 결과는 항상 `NaN`이 됩니다.

  ```javascript
  console.log(5 * NaN); // NaN
  ```

- **비교 연산에서의 형 변환**

  - `==` 연산자는 자동 형 변환을 수행하며, 자료형이 다르더라도 비교를 시도합니다.
  - `===` 연산자는 자동 형 변환을 하지 않으며, 자료형과 값이 모두 동일할 때만 `true`를 반환합니다.

  ```javascript
  console.log(2 == "2"); // true (자동 형 변환)
  console.log(2 === "2"); // false (형 변환 없음)
  ```

### 문자열 포매팅

JavaScript에서는 문자열을 포맷하는 여러 가지 방법이 있습니다.

- **`format()` 메서드**는 존재하지 않으며, 대신 `+` 연산자 또는 템플릿 리터럴을 사용합니다.

- **템플릿 리터럴**

  ```javascript
  let name = "Eva";
  console.log(`내 이름은 ${name}입니다.`);
  ```

🔥 **퀴즈**: 아래 코드의 결과는 무엇일까요?

```javascript
let year = 2000;
console.log(`${name}의 나이는 ${2023 - year}입니다.`); // 결과는?
```

### 불린형

- **불린형**은 참(`true`) 또는 거짓(`false`)을 나타내는 자료형입니다.
  ```javascript
  let isJavaScriptFun = true;
  console.log(isJavaScriptFun); // true
  ```

### 타입 검사 함수

- **`typeof()` 함수**는 값의 자료형을 확인하는 데 사용됩니다.

  ```javascript
  console.log(typeof "Hello"); // "string"
  console.log(typeof 42); // "number"
  console.log(typeof true); // "boolean"

  console.log(typeof 4 - 2); // NaN
  /* 해설
  typeof 4 - 2는 연산 우선순위에 따라, typeof 4의 결과인 문자열 'number' 와 숫자 2의 뺄셈이 됩니다. 
  다시 정리하면 'number' - 2가 되는데요, 문자열과 숫자는 뺄셈을 할 수 없기 때문에, 결과는 NaN이 됩니다.
  */
  ```

### null과 undefined

JavaScript에서 `null`과 `undefined`는 값이 없음을 나타내는 두 가지 방법입니다.

- **null**

  `null`은 '값이 없다'는 것을 **의도적으로** 표현할 때 사용하는 값입니다. 즉, 변수에 의도적으로 아무런 값도 넣지 않았음을 명시할 때 사용됩니다.

  ```javascript
  let value = null;
  console.log(value); // null
  ```

- **undefined**

  `undefined`는 변수가 선언되었지만, 값이 **할당되지 않았을 때** 나타나는 값입니다. 이는 값이 아직 정의되지 않았음을 의미합니다.

  ```javascript
  let notAssigned;
  console.log(notAssigned); // undefined
  ```

- **비교**

  - `null == undefined`는 `true`를 반환합니다. 이는 두 값이 모두 '비어 있음'을 나타내지만, JavaScript에서 느슨한 비교를 할 때는 동등하게 취급되기 때문입니다.
  - `null === undefined`는 `false`를 반환합니다. 이는 두 값의 자료형이 다르기 때문입니다. `null`은 객체(`object`)로 취급되지만, `undefined`는 자료형이 정의되지 않았음을 나타냅니다.

  ```javascript
  console.log(null == undefined); // true
  console.log(null === undefined); // false
  ```

### 자료형 퀴즈 (5분)

- [자료형 응용하기](https://www.codeit.kr/topics/core-concept-of-javascript-programming/lessons/3398?topicVersion=1&lessonVersion=1)

---

## 추상화

### 변수 지정 연산자

- **변수 지정 연산자** `=`를 사용해 값을 변수에 저장합니다.
  ```javascript
  let x = 5;
  ```

### 함수 실행 순서

- 함수는 호출된 시점에 실행되며, 호출된 순서에 따라 실행됩니다.

  ```javascript
  function sayHello() {
    console.log("Hello!");
  }

  sayHello(); // "Hello!" 출력
  ```

### return vs console.log

- **`return`**: 함수의 결과값을 반환합니다.
- **`console.log()`**: 함수의 실행 결과를 콘솔에 출력합니다.

🔥 **퀴즈**: 아래 함수를 수정하여, 두 수의 합을 반환하도록 하세요.

```javascript
function sum(a, b) {
  console.log(a + b); // 수징이 필요합니다
}

let result = sum(1 + 2);
console.log(result); // 이 줄에서 3이 출력되도록 하세요
```

### 옵셔널 파라미터

- **옵셔널 파라미터**: 함수에서 기본값을 제공하여, 인수가 전달되지 않을 때 사용됩니다.

  - 기본값을 가진 파라미터는 반드시 함수의 파라미터 목록에서 가장 뒤쪽에 위치해야 합니다. 그렇지 않으면 의도하지 않은 동작이 발생할 수 있습니다.

  ```javascript
  function greet(name = "Guest") {
    console.log(`Hello, ${name}!`);
  }

  greet(); // "Hello, Guest!"
  greet("Eva"); // "Hello, Eva!"
  ```

### Syntactic Sugar

동일한 기능을 하는 코드를 더 간결하고 가독성 있게 작성할 수 있도록 제공되는 문법적 편의입니다. 이는 프로그래밍 언어에서 개발자가 코드를 더 직관적이고 간결하게 작성할 수 있도록 도와줍니다.

1.  복합 할당 연산자

    복합 할당 연산자는 값을 업데이트할 때, 더 간단하고 효율적으로 표현할 수 있게 해줍니다.

    ```javascript
    // 이 두 줄은 같은 의미입니다.
    x = x + 1;
    x += 1;

    // 이 두 줄도 같은 의미입니다.
    x = x * 2;
    x *= 2;

    // 이 두 줄 역시 같습니다.
    x = x - 3;
    x -= 3;
    ```

2.  증가(increment), 감소(decrement) 연산자

    증가(`++`)와 감소(`--`) 연산자는 숫자 값을 1씩 증가시키거나 감소시킬 때 사용됩니다. 이 연산자는 **전위**와 **후위**에 따라 동작 방식이 다릅니다.

    - **`x++` (후위 증가 연산자)**: 현재 값을 반환한 후에 값을 증가시킵니다.

      ```javascript
      let x = 1;
      console.log(x++); // 1 (현재 값을 먼저 반환)
      console.log(x); // 2 (그 후에 값이 증가)
      ```

    - **`++x` (전위 증가 연산자)**: 값을 먼저 증가시키고, 증가된 값을 반환합니다.

      ```javascript
      let y = 1;
      console.log(++y); // 2 (먼저 값을 증가시키고 그 값을 반환)
      console.log(y); // 2
      ```

### 변수의 범위 (Scope)

- **로컬 변수**: 함수 내에서 선언되며, 함수 외부에서는 접근할 수 없습니다.
- **글로벌 변수**: 함수 외부에서 선언되며, 모든 코드에서 접근할 수 있습니다.

  ```javascript
  let globalVar = "I am global";

  function checkScope() {
    let localVar = "I am local";
    console.log(globalVar); // 가능
    console.log(localVar); // 가능
  }

  checkScope();
  console.log(globalVar); // 가능
  console.log(localVar); // 오류
  ```

🔥 [스코프 퀴즈](https://www.codeit.kr/topics/core-concept-of-javascript-programming/lessons/3410?topicVersion=1&lessonVersion=1)
: 아래 코드의 결과는 무엇일까요?

```javascript
function myFunction() {
  let x = "코드잇";
  x = "을지로";
}

myFunction();
console.log(x);
```

### 상수

- **상수**: `const` 키워드를 사용해 선언되며, 재할당이 불가능합니다.
  ```javascript
  const PI = 3.14;
  // PI = 3.14159; // 오류 발생: 상수는 재할당할 수 없습니다.
  ```

### 함수 변수 퀴즈 (5분)

- [교통 카드 단말기](https://www.codeit.kr/topics/core-concept-of-javascript-programming/lessons/3413?topicVersion=1&lessonVersion=1)

---

## 제어문

### while 반복문

- **while 반복문**은 조건이 참일 동안 코드를 반복 실행합니다.
  ```javascript
  let i = 0;
  while (i < 5) {
    console.log(i);
    i++;
  }
  ```

### if문

- **if문**은 조건이 참일 때만 코드를 실행합니다.
  ```javascript
  let score = 85;
  if (score >= 80) {
    console.log("합격");
  }
  ```

### elif문

- **elif문**은 앞의 조건이 거짓일 때 새로운 조건을 평가합니다.
  ```javascript
  let score = 70;
  if (score >= 80) {
    console.log("우수");
  } else if (score >= 60) {
    console.log("합격");
  } else {
    console.log("불합격");
  }
  ```

### break문

- **break문**은 반복문을 중단하고 빠져나올 때 사용합니다.
  ```javascript
  let i = 0;
  while (i < 10) {
    if (i === 5) {
      break;
    }
    console.log(i);
    i++;
  }
  ```

### continue문

- **continue문**은 반복문에서 현재 실행을 중단하고 다음 반복으로 넘어갑니다.
  ```javascript
  let i = 0;
  while (i < 10) {
    i++;
    if (i % 2 === 0) {
      continue;
    }
    console.log(i); // 홀수만 출력
  }
  ```

### switch문

- **switch문**은 주어진 표현식의 값과 일치하는 `case` 문을 실행합니다. `break`를 사용해 다른 `case`로 넘어가는 것을 방지할 수 있습니다.

  ```javascript
  let fruit = "apple";

  switch (fruit) {
    case "banana":
      console.log("I am a banana.");
      break;
    case "apple":
      console.log("I am an apple.");
      break;
    default:
      console.log("I am a fruit.");
  }
  ```

- **break문이 없는 경우**

  - `switch`문에서 `break`를 사용하지 않으면, 일치하는 `case` 이후의 모든 `case` 문이 실행됩니다.

  ```javascript
  let fruit = "apple";

  switch (fruit) {
    case "banana":
      console.log("I am a banana.");
    case "apple":
      console.log("I am an apple.");
    default:
      console.log("I am a fruit.");
  }
  // 출력:
  // I am an apple.
  // I am a fruit.
  ```

- **자료형 구분**

  - `switch`문은 **자료형을 엄격하게 구분**합니다. 만약 `switch`문을 `if`문으로 변환하고자 한다면, `===` 연산자를 사용하여 자료형까지 일치하는지 확인해야 합니다.

  ```javascript
  let value = 10;

  switch (value) {
    case "10":
      console.log("String 10");
      break;
    case 10:
      console.log("Number 10");
      break;
    default:
      console.log("Not 10");
  }
  // 출력: Number 10
  ```

## [피보나치 수열 퀴즈 (10분)](https://www.codeit.kr/topics/core-concept-of-javascript-programming/lessons/3432?topicVersion=1&lessonVersion=1)
