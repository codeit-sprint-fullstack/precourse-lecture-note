# 1. JavaScript로 프로그래밍 시작히기

> 코드잇 영상으로 확인하기 : [프로그래밍 시작하기 in JavaScript](https://www.codeit.kr/topics/getting-started-with-javascript)

## 개요

> ❤️‍🔥 **학습 목표**
>
> - 세부 문법보다는 프로그래밍의 기본 개념과 원리를 이해하기
> - JavaScript를 능숙하게 사용할 수 있는 능력을 갖추기

> ✅ 그전에 잠깐!
>
> 프리코스 토픽을 다 들으신 분들이라면 동일한 내용이니 패스하셔도 좋습니다 !

## 목차

- [1. JavaScript로 프로그래밍 시작히기](#1-javascript로-프로그래밍-시작히기)
  - [개요](#개요)
  - [목차](#목차)
  - [JavaScript 소개](#javascript-소개)
    - [웹 기술의 중요성](#웹-기술의-중요성)
    - [JavaScript의 등장과 발전](#javascript의-등장과-발전)
    - [JavaScript의 중요성과 수요](#javascript의-중요성과-수요)
  - [프로그래밍 기본 개념](#프로그래밍-기본-개념)
    - [코멘트(주석)](#코멘트주석)
    - [자료형 (Data type)](#자료형-data-type)
    - [추상화(Abstraction)](#추상화abstraction)
    - [변수](#변수)
    - [함수](#함수)
    - [매개변수(파라미터)](#매개변수파라미터)
    - [return문](#return문)

## JavaScript 소개

### 웹 기술의 중요성

- 현대 사회에서 웹 기술은 모든 산업에 걸쳐 필수적입니다. IT 기업뿐만 아니라 거의 모든 회사가 웹 사이트를 통해 자신을 홍보하고, 심지어 개인들도 웹 사이트를 구축합니다.
- 1989년에 처음 등장한 웹은 단순한 정보 공유 도구에서 시작하여, 현재는 다양한 미디어와 기능을 포함하는 일상적인 플랫폼으로 발전했습니다.

### JavaScript의 등장과 발전

- 웹의 발전에 가장 크게 기여한 프로그래밍 언어 중 하나가 바로 JavaScript입니다.
- JavaScript는 처음 등장했을 때는 큰 인기를 끌지 못했으나, 2015년을 기점으로 급격히 개선되며 개발자들 사이에서 긍정적인 평가를 받기 시작했습니다.
- 현재 JavaScript는 웹 개발을 넘어 모바일 앱, PC 프로그램, VR/AR, 블록체인 등 다양한 분야에서 사용되며 범용적인 기술로 자리 잡았습니다.

### JavaScript의 중요성과 수요

- JavaScript의 활용 범위가 확장됨에 따라, JavaScript 개발자에 대한 수요도 폭발적으로 증가하고 있습니다.
- JavaScript를 배우는 것은 개인의 가치를 높이고, 다양한 기술을 습득하여 경쟁력을 갖추는 데 도움이 됩니다.

## 프로그래밍 기본 개념

### 코멘트(주석)

- **주석 (Comment)**: 자바스크립트에서는 `//` 뒤에 오는 내용은 주석으로 처리됩니다. 주석은 실행되지 않으며, 코드에 대한 설명을 적는 데 사용됩니다.
- **주석의 사용 목적**: 1) 복잡한 코드 설명 2) 작업 중인 부분 표시 3) 다른 개발자와 소통

```javascript
// 이것은 주석입니다
console.log("Hello World"); // 이것도 주석입니다
```

### 자료형 (Data type)

- **자료형**: 자바스크립트뿐만 아니라 모든 프로그래밍에서 사용하는 기본적인 자료형입니다.

  - **숫자 (Number)**: 정수와 실수를 포함하며, 수학적 연산에 사용됩니다.
  - **문자열 (String)**: 문자로 구성된 데이터이며, `+` 기호를 사용해 문자열을 연결할 수 있습니다.
  - **불린 (Boolean)**: 참(`true`) 또는 거짓(`false`)을 나타내며, 조건문에서 자주 사용됩니다.

```javascript
console.log("안녕" + "하세요");
// 출력: 안녕하세요

console.log(2 + 5);
// 출력: 7

console.log(7 > 3);
// 출력: true

console.log(3 > 7);
// 출력: false
```

### 추상화(Abstraction)

- **추상화**: 복잡한 것들을 목적에 맞게 단순화하는 것!
  - 복잡한 자료, 모듈, 시스템 등으로부터 핵심적인 개념 또는 기능을 간추려 내는 것
  - 즉, 복잡한 것들을 목적에 맞게 단순화하는 것

### 변수

- **변수**: 어떤 값을 담기 위해 이름이 붙은 상자입니다.
  getting-started-with-javascript/lessons/3367)
  - 반복 입력하는 구체적인 숫자는 오타를 만들어 낼 수 있습니다. 또한 숫자에 대한 의미 전달이 어렵기 때문에 이를 방지하기 위해 변수를 활용합니다.

```javascript
let burgerPrice = 4990;
console.log(burgerPrice);
// 출력: 4990
```

- **활용 예제**: [칼로리 계산기 예제 링크](https://www.codeit.kr/topics/

### 함수

- **함수**: 반복적으로 사용되는 코드를 묶어서 하나의 단위로 만든 것
  - **함수 선언**: `function [함수명]() { }`
  - **함수 호출**: `[함수명]();`
  - **함수의 장점**:
    - 내부에 작성한 코드들의 포괄적인 의미를 이름을 통해 한 번에 드러낼 수 있습니다.
    - 다양한 명령어를 하나로 묶을 수 있어 반복해서 사용할 때 더욱 효율적입니다.
  - `console.log`도 JS를 만든 개발자들이 미리 작성해둔 함수입니다.
    - 내부적으로 복잡한 로직을 가지고 있을 수 있지만, 단순히 `console.log`라는 함수의 이름만 알고 있으면 간단하게 문자열을 출력할 수 있습니다.
    - ⇒ 즉, 함수에도 추상화의 개념이 녹아져 있습니다.
- **활용 예제**: [자랑스러운 애국가 예제 링크](https://www.codeit.kr/topics/getting-started-with-javascript/lessons/3369)

```javascript
function sayHello() {
  console.log("안녕하세요!");
}

sayHello();
// 출력: 안녕하세요!
```

### 매개변수(파라미터)

- **매개변수(파라미터)**: 함수의 소괄호 안에 입력하는 값
  - `console.log(값1, 값2, 값3)`
  - 함수 내에서 파라미터는 변수처럼 사용할 수 있습니다.
  - 함수 호출 시 소괄호 안에 입력한 값이 파라미터에 전달되는 개념입니다.

```javascript
function greet(name) {
  console.log("안녕하세요, " + name + "님!");
}

greet("김철수");
// 출력: 안녕하세요, 김철수님!
```

- **활용 예제**: [Codeit 예제 링크](https://www.codeit.kr/topics/getting-started-with-javascript/lessons/3373)

### return문

- **return문**: 함수가 실행된 결과를 돌려주는 역할을 합니다.

```javascript
function add(a, b) {
  return a + b;
}

let sum = add(3, 5);
console.log(sum);
// 출력: 8
```

- **활용 예제**: [Codeit 예제 링크](https://www.codeit.kr/topics/getting-started-with-javascript/lessons/3375)
