## map
map 메서드는 다음과 같이 사용한다. <br>
배열.map( (요소, 인덱스, 배열) => { return 요소} ); <br>
map의 기본 원리는 간단하다. 반복문을 돌며 배열 안의 요소들을 1대1로 짝지어준다. 매핑한다고 표현한다. 어떻게 짝지어줄지 정의한 함수를
메서드의 인자로 넣어주면 된다.
```javascript
const numbers = [1,2,3];
let result = numbers.map( (v) => {
  console.log(v);
  return v;
});
// console 1,2,3 출력
numbers; // [1, 2, 3]
result; // [1, 2, 3]]
numbers === result; // false
// map을 실행하는 배열과 결과로 나오는 배열은 다른 객체.
// 단, 배열 안에 객체가 들었다면 객체는 공유된다.

result = numbers.map( (v) => {
  return v + 1; // 각 요소에 1씩 더한 값 반환.
});
result; // [2, 3, 4]

result = numbers.map( (v) => {
  if ( v % 2 ) {
    return '홀수';
}
return '짝수';
});
result; // ['홀수','짝수','홀수']
```
map은 배열을 1대1로 짝짓되 기존 객체를 수정하지 않는 메서드이다.
## reduce, reduceRight
reduce 메서드는 다음과 같이 사용한다. <br>
배열.reduce( (누적값, 현재값, 인덱스, 요소) => { return 결과 }, 초깃값);<br>
이전값이 아닌 누적값이라는 점에 주의하자. 누적값이기 때문에 다양한 활용이 가능하다. 
```javascript
result = numbers.reduce( (acc, cur, i) => {
  console.log(acc, cur, i);
  return acc + cur;
}, 0);
// 0 1 0
// 1 2 1
// 3 3 2
result; // 6
```
