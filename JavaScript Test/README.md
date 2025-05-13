### 두 수의 합을 구하라.
```javascript
const solution = (num1,num2) => num1 + num2
```
단 한줄로 표현이 가능했다. return 값이 하나라는 가정하에 가능하다.

### 두 수의 나눗셈을 정수로 표현하라.
```javascript
function solution(num1, num2) {
  return Math.trunc(num1 / num2 * 1000);
}
```
'Math.trunc()'는 소수점 이하는 다 버린다. 'Math.floor()'는 소수점을 내림한다.

### 숫자 비교하기
```javascript
const solution = (num1, num2) => num1 === num2 ? 1 : -1
```
== 연산자(Equal Operator)는 1과 "1" 1과 true를 참이라 하지만, === 연산자(Strict Equal Operator)는 엄격한 비교 연산자로 자료형까지 비교 대상에 포함된다. 정확한 1과 1이여야지 참이 된다. 
