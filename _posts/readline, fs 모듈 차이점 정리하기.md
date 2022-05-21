## readline, fs 모듈 차이점 정리하기
### readline으로 input 넣을 때 한 줄에 하나씩 / 한 줄에 여러 항목 넣을 때



https://yeoncoding.tistory.com/13
https://yoon-dumbo.tistory.com/entry/NODEJS-기반으로-알고리즘-풀때-입력받는-방법
https://silverlibrary.tistory.com/236
https://nyang-in.tistory.com/156









readline에서 input 값을 

한 줄에 하나씩 넣을 때
```javscript
rl.on('line', function(value) {
  input.push(parseInt(value));
})
```

한 줄에 여러 항목 넣을 때
``` javascript
rl.on('line', function(value) {
  input = value.split(' ').map((n) => parseInt(n))
})
```



fs모듈의 경우

``` javascript
let input = require('fs').readFileSync('/dev/stdin').toString();
// 1. 터미널에서 입력을 받거나
// 입력 후 control + D를 이용하여 빠져나온다.

const fs = require('fs');
const filePath = process.platform === 'linux' ? '/dev/stdin' : './input.txt';
let input = fs.readFileSync(filePath).toString()
// 2. input.txt를 통해 입력을 받을 수 있다.
```