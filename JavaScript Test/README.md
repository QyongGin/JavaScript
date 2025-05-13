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

### 분수의 덧셈
```javascript
funtion gcd (a,b) { // 기약분수 구하기
  while (b !== 0) {
    let temp = b;
    b = a % b;
    a = temp;
}
  return a;
}

function solution(numer1, denom1, numer2, denom2) { // numerator 분자 denominator 분모
  if (denom != denom2) {
    newDenom = denom1 * denom2;
    newNumer1 = numer1 * denom2;
    newNumer2 = numer2 * denom1;
    sumNumer = newNumer1 + newNumer2;
}
else {
  newDenom = denom1;
  sumNumer = numer1 + numer2;
}

const divisor = gcd(sumNumer, newDenom);
let answer = [(sumNumer / divisor), (newDenom / divisor)];
return answer;
}
```
### 배열 두 배 만들기
```javascript
const solution = (numbers) => numbers.map((number) => number * 2)
```
.map 메서드를 사용한다. numbers 배열의 요소를 number에 순회하며 대입한다. number * 2 값을 return해서
solution은 numbers 요소에 두 배를 곱한 요소가 모인 배열이 생성된다.

