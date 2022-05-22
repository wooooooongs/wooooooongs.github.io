## var, const, let의 차이

var는 기존 사용하던 변수 선언으로, 함수 레벨 스코프에 해당하며
ES6부터 const, let의 등장으로 블록 레벨 스코프도 지원하기 시작.

```
var global_scope = 'global';  // 전역 스코프

var local_function = function() {
    var local_scope = 'goorm';  // 지역 스코프
    console.log(global_scope);  // 전역 스코프 참조 가능. global 출력
    console.log(local_scope);  // 함수 내이기 때문에 지역 스코프 참조 가능. goorm 출력
};

console.log(local_scope);  // name은 지역스코프이기 때문에 에러 발생.
```