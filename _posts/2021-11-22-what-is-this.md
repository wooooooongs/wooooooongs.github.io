---
title:  "this란?"
excerpt: "this에 대해 정리해보자"

categories:
  - JavaScript
tags:
  - [JS, JavaScript, js, this, scope]

toc: true
toc_sticky: true
 
date: 2021-11-18
last_modified_at: 2021-11-18
---
# this에 대해 알아보기

this는 다른 언어와 혼동되기 쉬운 개념이라고 한다해서 여기에 적어놓는다.<br>
나는 다른 언어는 아직 제대로 안다뤄봐서 모르겠음

먼저 무엇을 검색하든 먼저 뜨는 MDN에서의 정의를 살펴보면 이러하다.
<br>
<br>

<p align="center"><img src="https://user-images.githubusercontent.com/69746360/142815457-4106ae80-db6a-434a-acd8-aff38e643408.jpg" width="50%" height="50%"/></p>


음 무슨 말인지 1도 모르겠다.
하지만 여기서 우리가 주목해야 할 점은
밑줄을 친 구간! <br> **함수를 호출한 방법.** 요 부분이 중요하다.<br>
this는 한 줄로 요약해서: ***누가 나를 호출했는지 확인*** 하는 방법이다.

<br>
<br>

지금 당장 콘솔창에서 this를 출력하면
```js
console.log(this); // Window {Infinity: Infinity, window: Window, NaN: NaN, undefined: undefined,어쩌구…}
```
<br>

JavaScript의 전역객체인 window가 나오게 된다.
왜냐면 호출한 곳은 window이기 때문임!

<details>
  <summary>여기서 잠깐 window란?</summary>
  <div markdown="1">
  

  [javascript bom](https://www.google.co.kr/search?q=javascript+bom&newwindow=1&client=safari&channel=iphone_bm&sxsrf=AOaemvLdw96oEIyRTta5kcTuUc77u8D-uw%3A1637563858331&source=hp&ei=0j2bYdnGEe670PEP8L-oyAY&iflsig=ALs-wAMAAAAAYZtL4hXwh3z8VsTR8NLXJjhx8GGfuDPa&ved=0ahUKEwjZ98fgsKv0AhXuHTQIHfAfCmkQ4dUDCAo&uact=5&oq=javascript+bom&gs_lcp=Cgdnd3Mtd2l6EAMyBQgAEIAEMgUIABDLATIFCAAQgAQyBQgAEMsBMgUIABDLATIFCAAQywEyBwgAEAoQywEyBQgAEMsBMgQIABAeMgQIABAeOgQIIxAnOhEILhCABBCxAxCDARDHARDRAzoLCAAQgAQQsQMQgwE6BQguEIAEOg4IABCABBCxAxCDARCLAzoLCAAQgAQQsQMQiwM6BwgjEOoCECc6CAguEIAEELEDOg4ILhCABBCxAxCDARCLAzoICAAQgAQQiwM6CwguEIAEELEDEIsDOggIABCABBCxAzoLCC4QgAQQsQMQgwE6BwgAELEDEEM6BAgAEEM6EAgAEIAEEIcCELEDEIMBEBQ6CggAELEDEIMBEEM6BwgjELECECc6BwgAELEDEAo6CggAELEDEIMBEAo6BAgAEAo6BAgAEA06BwgjELACECc6BwgAELEDEA06CggAEIAEEIcCEBRQAFjKMmCeNGgUcAB4A4ABpAGIAd8gkgEEMS4zMZgBAKABAbABCrgBAg&sclient=gws-wiz)
  <br>
  위 주소, google에서 JavaScript의 BOM(Browser Object Model) 에 대해 검색해보면 알 수 있다.
  절대 귀찮아서 링크만 달아논거 아님~~
  </div>
</details>

<br>

***

<br>

## 첫번째 호출
<br>

코드를 보면서 설명하는게 빠르겠다.<br>
객체를 통해 살펴보자면 이렇다.
```js
var bar = {
  이름: '떡볶이',
  나는함수: function(){
    console.log(this);
  }
}
```
'나는함수'안에 this를 로그로 찍는 함수가 있다고 했을 때, 바로 실행을 시켜보면
```js
bar.나는함수() // {이름: "떡볶이", 나는함수: function}
```
bar를 출력한다.<br>
아하! 그냥 this를 출력하면 전역변수(window)가 나오지만<br>
객체 안에서 this를 출력하였기 때문에 bar객체가 출력되는 것이다.<br>
<br>
<br>

## 두번째 호출
<br>

하지만 우리는 처음 밑줄 친 정의에 의하면 **호출된 방식**에 따라 다르다고 했다.<br>
진짜 누가 호출했는냐에 따라 지 맴대로 이랬다 저랬다 하는거다.
<br><br>

그럼 이제 다른 곳에서 나는함수를 호출해보자.
```js
var 나는함수를_호출 = bar.나는함수; // 나는함수를_호출 안에 bar의 나는함수를 넣었다.

나는함수를_호출(); // Window {Infinity: Infinity, window: Window, NaN: NaN, undefined: undefined,어쩌구…}
```
엥. bar.나는함수를 그대로 담았을 뿐인데, 결과가 달라졌다.<br>
왜냐면 함수만 쏙 꺼내서 window에서 함수를 실행시켰기 때문임!!!!<br>

또 다른 곳에서 나는함수를 호출해보자.

<br>
<br>

## 세번째 호출

<br>

```html

  <!-- 가정 1: JS로 eventListener 달기-->
  <button id="call">클릭</button>

  <!-- 가정 2: 버튼에 onclick 달기 -->
  <button id="call" onclick="bar.나는함수()">클릭</button>

```

가정 1(addEventListner) 결과
<p align="center"><img width="243" alt="가정1" src="https://user-images.githubusercontent.com/69746360/142999376-1cd87ade-f3a6-4ba4-aa61-283df8378422.png"></p>
<br>
가정 2(onclick) 결과
<p align="center"><img alt="가정2" width="243" src="https://user-images.githubusercontent.com/69746360/142999394-1d5f404b-0342-4119-82f2-e1232d8b3686.png"></p>

<br>

엥! 이벤트리스너를 달 때와 온클릭으로 호출했을 때와 또 결과가 다르다.
*둘의 차이점은 좀 더 공부해봐야 한다.*

<br>

일단 주목해야 할 점은 이벤트리스너를 달았을 때 button을 출력하는 것을 보아하니<br>
두번째 호출 처럼 나는함수만을 꺼내서 버튼에 넣은 것이기 때문에 버튼 그 자체를 출력하는 것이다. 

추가로 bind를 이용해 this의 값을 고정시킬 수도 있다!

이 모든 것은 
유튜브 채널 코드종님의 영상을 참고했으며,
글로 이해가 안된다면 영상 10분 보는 것이 백만배 나을 것 같다.<br>
<https://www.youtube.com/watch?v=PAr92molMHU>