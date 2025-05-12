# let과 const

## block-level-scope
```javascript
let box = 'red'; // 전역 변수
{
  console.log(box); // ReferenceError: box is not defined
  let box = 'blue'; // 지역 변수
  console.log(box); // blue
}
```
console.log는 지역 변수를 우선적으로 찾는다. 밖에서 box가 이미 선언되고 초기화 되었지만, body에서 let box로 동일한 변수명으로
선언을 해서 console은 지역 변수 box를 찾다가 box가 초기화되기 전에 console.log가 되었기에 오류가 발생한다. <br>
오류를 막으려면 변수명을 다르게 하거나 동일명 변수를 선언하고 초기화 후 console.log로 불러온다.
## 변수 중복 선언 불가
var에서는 변수를 선언 후 다시 밑에서 재선언이 가능했지만 let, const는 재선언 시 문법 에러가 발생한다.
```javascript
let box = 'red';
let box = 'blue'; // Identifier 'box' has already been declared
```
## 호이스팅 불가
let,const는 변수 생성 시 선언과 초기화가 분리되어서 진행이 된다. 변수를 생성하고 선언까지 한 후 일시적 사각지대(TDZ)가 선언과
초기화 사이에 생기며, 할당문에서 변수 값이 할당될 때 초기화 및 값 할당이 이루어 진다.
```javascript
console.log(box); // error: box is not defined
let box = 'red';
```
## let과 const의 차이점
let은 변수 선언 후 값을 재할당 할 수 있지만, const는 재할당하지 못한다. 
```javascript
let box1 = 'red';
box = 'blue'; // success

const box2 = 'green';
box2 = 'orange'; // error: Assigment to constant variable.
```
