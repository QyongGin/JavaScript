# 함수
함수는 프로그램을 구성하는 주요 '구성 요소(building block)'이다. 함수를 이용하면 중복 없이 유사한 동작을 하는 코드를 여러 번 호출할 수 있다.
## 함수 선언
함수 선언(function declaration) 방식을 이용하면 함수를 만들 수 있다.
```javascript
function showMessage() {
    alert( '함수 출력.' ); // 함수 본문
    }
```
function 키워드, 함수 이름, 매개변수를 차례로 입력하여 함수를 선언한다. javascript에서 함수는 <script> 안에서 선언하고 괄호를 붙여 사용한다.<br>
매개변수가 여러 개 있다면 콤마로 구분한다. 함수를 구성하는 코드의 모임인 '함수 본문(body)'을 중괄호로 감싸 붙여준다.
함수의 주요 용도 중 하나는 중복 코드 피하기이다. 

## 지역 변수
함수 내에서 선언한 변수인 지역 변수(local variable)는 함수 안에서만 접근할 수 있다.
```javascript
function showMessage() {
    let message = '지역 변수'; // 지역 변수
    alert(message);
}
showMessage(); // 지역 변수
alert(message); // message는 함수 내 지역 변수기 때문에 ReferenceError가 발생한다.
```
