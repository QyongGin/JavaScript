# 함수
함수는 프로그램을 구성하는 주요 '구성 요소(building block)'이다. 함수를 이용하면 중복 없이 유사한 동작을 하는 코드를 여러 번 호출할 수 있다.
### 함수 선언
함수 선언(function declaration) 방식을 이용하면 함수를 만들 수 있다.
```javascript
function showMessage() {
    alert( '함수 출력.' ); // 함수 본문
    }
```
function 키워드, 함수 이름, 매개변수를 차례로 입력하여 함수를 선언한다. javascript에서 함수는 <script> 안에서 선언하고 괄호를 붙여 사용한다.<br>
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
함수의 매개변수에 
















