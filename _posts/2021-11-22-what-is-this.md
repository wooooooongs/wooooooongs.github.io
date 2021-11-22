---
title:  "[공사중] this란?"
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
밑줄을 친 구간! **함수를 호출한 방법** 요 부분이 중요하다.<br>
this는 한 줄로 요약해서: ***누가 나를 호출했는지 확인*** 하는 방법이다.

<br>
<br>

지금 당장 콘솔창에서 this를 출력하면
```js
console.log(this); // Window {Infinity: Infinity, window: Window, NaN: NaN, undefined: undefined,어쩌구…}
```
<br>

JavaScript의 전역객체인 window가 나오게 된다.
<details>
  <summary>window란?</summary>
  <div markdown="1">
  

  [javascript bom](https://www.google.co.kr/search?q=javascript+bom&newwindow=1&client=safari&channel=iphone_bm&sxsrf=AOaemvLdw96oEIyRTta5kcTuUc77u8D-uw%3A1637563858331&source=hp&ei=0j2bYdnGEe670PEP8L-oyAY&iflsig=ALs-wAMAAAAAYZtL4hXwh3z8VsTR8NLXJjhx8GGfuDPa&ved=0ahUKEwjZ98fgsKv0AhXuHTQIHfAfCmkQ4dUDCAo&uact=5&oq=javascript+bom&gs_lcp=Cgdnd3Mtd2l6EAMyBQgAEIAEMgUIABDLATIFCAAQgAQyBQgAEMsBMgUIABDLATIFCAAQywEyBwgAEAoQywEyBQgAEMsBMgQIABAeMgQIABAeOgQIIxAnOhEILhCABBCxAxCDARDHARDRAzoLCAAQgAQQsQMQgwE6BQguEIAEOg4IABCABBCxAxCDARCLAzoLCAAQgAQQsQMQiwM6BwgjEOoCECc6CAguEIAEELEDOg4ILhCABBCxAxCDARCLAzoICAAQgAQQiwM6CwguEIAEELEDEIsDOggIABCABBCxAzoLCC4QgAQQsQMQgwE6BwgAELEDEEM6BAgAEEM6EAgAEIAEEIcCELEDEIMBEBQ6CggAELEDEIMBEEM6BwgjELECECc6BwgAELEDEAo6CggAELEDEIMBEAo6BAgAEAo6BAgAEA06BwgjELACECc6BwgAELEDEA06CggAEIAEEIcCEBRQAFjKMmCeNGgUcAB4A4ABpAGIAd8gkgEEMS4zMZgBAKABAbABCrgBAg&sclient=gws-wiz)<br>
  위 주소, google에서 JavaScript의 BOM(Browser Object Model) 에 대해 검색해보면 알 수 있다.
  절대 귀찮아서 링크만 달아논거 아님~~
  </div>
</details>

코드를 보면서 설명하는게 빠르겠다.<br>
객체를 통해 살펴보자면 이렇다.
```js
var bar = {
  이름: '떡볶이',
  함수: function(){
    console.log(this);
  }
}
```
이러한 객체가 있다고 했을 때,
```js
bar.함수();
```