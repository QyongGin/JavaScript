# 함수
함수는 프로그램을 구성하는 주요 '구성 요소(building block)'이다. 함수를 이용하면 중복 없이 유사한 동작을 하는 코드를 여러 번 호출할 수 있다.
### 함수 선언
함수 선언(function declaration) 방식을 이용하면 함수를 만들 수 있다.
```javascript
function showMessage() {
    alert( '함수 출력.' ); // 함수 본문
    }
```
```function``` 키워드, 함수 이름, 매개변수를 차례로 입력하여 함수를 선언한다. javascript에서 함수는 ```<script>``` 안에서 선언하고 괄호를 붙여 사용한다.<br>
매개변수가 여러 개 있다면 콤마로 구분한다. 함수를 구성하는 코드의 모임인 '함수 본문(body)'을 중괄호로 감싸 붙여준다.
함수의 주요 용도 중 하나는 중복 코드 피하기이다. 

### 지역변수
함수 내에서 선언한 변수인 지역 변수(local variable)는 함수 안에서만 접근할 수 있다.
```javascript
function showMessage() {
    let message = '지역변수'; // 지역변수
    alert(message);
}
showMessage(); // 
alert(message); // message는 함수 내 지역변수기 때문에 ReferenceError가 발생한다.
```
### 외부변수
함수 내부에서 함수 외부의 변수인 외부변수(outer variable)에 접근할 수 있다.
```javascript
let userName = 'John';
function showMessage() {
    let message = 'Hello,' + userName;
    alert(message);
}
showMessage(); // Hello, John
```
함수에선 외부변수에 접근과 수정이 가능하다.
```javascript
let name = 'John';
function showMessage() {
    name = "yong";
    let message = 'Hello,' + name;
    alert(message);
}
alert(name); // 함수 호출 전이므로 John 출력
showMessage();
alert(name); // 함수에 의해 yong으로 바뀐다.
```
함수 내부에 외부변수와 동일한 이름을 가진 변수가 선언되었다면, 함수는 내부 변수를 우선시한다.<br>
따라서, 함수 내부에 외부변수와 동일명 지역변수가 선언되었다면 지역변수를 사용하지, 외부변수는 건드리지 않는다.
```javascript
let name = 'John';

function showMessage() {
  let name = "Bob"; // 같은 이름을 가진 지역변수를 선언한다.

  let message = 'Hello, ' + name; // Bob
  alert(message);
}

// 함수는 내부변수인 name만 사용한다.
showMessage();

alert(name); // 함수는 외부변수에 접근하지 않았다. 따라서 값은 그대로 John이 출력된다.
```

### 전역변수
함수 외부에 선언된 변수는 전역변수(global variable)라고 부른다.<br><br>
전역변수는 같은 이름을 가진 지역 변수에 의해 가려지지 않는다면 모든 함수에서 접근 가능하다.<br><br>
변수는 연관되는 함수 내에 선언하고 전역변수는 되도록 사용을 지양하자. 근래 작성된 코드들은 대부분 전역변수를 사용하지 않거나
최소한으로만 사용한다. <br>
다만 프로젝트 전반에서 사용되는 데이터는 전역변수에 저장하는 것이 유용한 경우도 있다.

### 매개변수
매개변수(parameter)를 이용하면 임의의 데이터를 함수 안에 전달할 수 있다. 매개변수는 인자(parameter)라고도 한다.
```javascript
function showMessage(from, text) {

  // 매개변수 from을 지역 변수 from으로 인지하여 지역변수 from에 저장된다.
  from = '*' + from + '*';


  alert( from + ': ' + text );
}

let from = "Ann";

showMessage(from, "Hello"); // *Ann*: Hello

// 매개변수를 지역변수로 인지하여 지역 변수 from만 번경되었으므로 여전히 'Ann'
alert( from ); // Ann
```
함수의 매개변수에 전달된 값을 인수(argument)라고 부르기도 한다.
- 매개변수 : 함수 선언 방식에서 괄호 사이에 위치한 변수 (선언 시 용어)
- 인수 : 함수 호출 시 매개변수에 전달되는 값 (호출 시 용어)
함수 선언 시에는 매개변수를 나열하고 호출 시에는 인수를 전달하여 호출한다. <br>

### 기본값
함수 호출 시 매개변수에 인수를 전달하지 않으면 그 값은 ```undefined```가 된다.<br>
```undefined```가 되지 않게 하려면 함수 선언 시 ```=```를 사용해 '기본값(default value)을 설정한다.
```javascript
// showMessage(from, text)는 매개변수가 2개지만 인수를 하나만 넣어서 호출할 수 있다.
// text는 undefined가 된다. 
showMessage("Ann"); // "Ann : undefined"

function showMessage(from, text = "no text given") {
    alert from + ": " + text );
}
showMessage("Ann"); // Ann: no text given
showMessage("Ann", undefined) // 값이 undefined와 일치하여 기본값 할당 Ann: no text given

function showMessage(from, text = anotherFunction()) {
    // anotherFunction()은 text값이 없을 때 호출.
}

// 또 다른 방법
function showMessage(text) {
    if ( text === undefiend) { // 매개변수 생략 시
        text = '빈 문자열';
    }
    alert(text);
}

function showMessage(text) {
    text = text || '빈 문자열';
}

// nullish 병합 연산자(unllish coalescing operator)??
// 0처럼 falsy로 평가되는 값 일반 값처럼 처리 가능
// undefined 또는 null 이면 "unknown"
function showCount(count){
    alert(count ?? "unknown");
}
```
### 매개변수 기본값 평가 시점
자바스크립트에선 함수를 호출할 때 마다 매개변수 기본값을 평가한다. 해당 매개변수가 없을 때만 평가.<br>

### 반환 값
함수를 호출했을 때 함수를 호출한 곳에 특정 값을 반환하게 할 수 있다. 이 특정 값을 반환 값(return value)라고 부른다.
```javascript
function sum(a, b) {
    return a + b;
    alert("Hi!") // return 시 함수는 즉시 종료되기에 alert는 실행되지 않는다.
}
let result = sum(1, 2);
alert( result ); // 3
```
지시자 ```return```은 함수 내 어디서든 사용할 수 있다. 실행 흐름이 ```return```을 만나면 함수 실행은 즉시 중단되고 
함수를 호출한 곳에 값을 반환한다. <br>
```return``` 문이 없거나 ```return``` 지시자만 있는 함수는 ```undefined```를 반환한다. 
### ```return```과 값 사이에 절대 줄을 삽입하지 않는다.
```javascript
return
(some ... )
```
반환하려는 값의 표현식이 길다면 return과 반환하려는 값 사이에 새 줄을 넣어 코드를 작성하고 싶을 수 있다.<br>
하지만, 자바스크립트는 ```return```문 끝에 자동으로 세미콜론```;```을 넣기 때문에 절대 이렇게 작성하면 안된다. <br>

### 함수 이름짓기
함수는 어떤 동작을 수행하기 위한 코드를 모아놓은 것이다. 그에 따라 함수의 이름은 대개 동사이다. <br>
함수의 이름은 가능한 간결하고 명확해야 한다. 이름만 보고도 어떤 동작을 하는지 설명이 가능케 지어야 한다.
```javascript
// show : 무언가를 보여준다.
// get : 값을 반환한다.
// calc : 무언가를 계산한다.
// create : 무언가를 생성한다.
// check : 무언가를 확인하고 불린값을 반환한다.

showMessage(..)     // 메시지를 보여줌
getAge(..)          // 나이를 나타내는 값을 얻고 그 값을 반환함
calcSum(..)         // 합계를 계산하고 그 결과를 반환함
createForm(..)      // form을 생성하고 만들어진 form을 반환함
checkPermission(..) // 승인 여부를 확인하고 true나 false를 반환함
```

### 함수는 동작 하나만 담당해야 한다.
함수는 이름에 언급된 동작을 정확히 수행하고 그 이외 동작은 수행해선 안된다. <br>
예를 들어 ```getAge``` 함수는 나이를 얻는 동작만 수행하지, ```alert```창에 나이를 출력하는 동작은 하지 않는게 좋다.<br>















