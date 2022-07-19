## forEach(), map(), reduce(), filter() 사용하기

forEach: for문 돌리는 거랑 같은 개념
map: for문을 돌려서 새로운 배열을 만드는 목적. return 필수
reduce: for문을 돌려서 최종적으로 '무언가'(숫자, 문자, 객체 등)를 만드는 목적. return 필수

--

map()에 대하여

Array.prototype.map() 배열 내 모든 값에 함수를 호출한 결과를 모아 새로운 배열을 반환한다. -> 쉽게 말해, 그냥 배열 안에 모든 값에 특정 콜백함수를 실행하는 메소드.

`let arr = [ 1, 10, 13, 16 ];`

이런 배열이 있을 때, 이 모든 값 하나하나에 2를 곱하고 싶다고 가정하면.
그럴 때 for문이나 for of문을 이용할 수도 있다.

```javascript
for(i=0; i<array1.length; i++){
  console.log(array1[i] * 2);
}

출력값
20
2
10
18
```

심지어 배열로 출력을 하지도 못했다!
map을 쓰면 더 간단해진다.

```javascript
const map메소드 = arr.map(x => x * 2);
console.log(map메소드);

출력값
[ 20, 2, 10, 18 ]
```


