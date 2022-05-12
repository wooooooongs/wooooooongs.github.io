---
title:  "[GitHub] private repository 생성 시 에러"
excerpt: "Permission denied 발생"

categories:
  - gitgub
tags:
  - [github]

toc: true
toc_sticky: true
 
date: 2022-03-10
last_modified_at: 2022-03-10
---

## 사건의 전말

깃헙에서 private 레포지토리를 만들고 기존의 절차대로 README.md 파일 추가 및 푸시를 했다. 하지만 에러 발생! `git remote -v` 를 통해 현재 레포지토지 경로에 문제가 없었음을 확인했는데도 이러한 에러메시지가 떴다.

```
사용자ID@깃헙ID 레포지토리명 % git push -u origin main
git@github.com: Permission denied (publickey).

fatal: Could not read from remote repository.
Please make sure you have the correct access rights
and the repository exists.
```

권한이 없다는 내용인데, 검색해보니 유독 MacOS에서는  private 레포지토리에서는 깃헙 access token을 매번 물어봐서 환경 문제로 꼬이는 경우가 대다수라고 한다.     

<br>

## 해결방법

방법은 간단하다. 우선 `git remote remove origin`명령어를 이용해 현재 레포지토리를 연결 해제한 다음,

개인 access token 해쉬키 값을 레포지토리를 연결 하는 명령어`git remote add origin`에 깃헙 아이디 앞에 추가해주는 것이다. `git remote add origin https://해쉬키값@github.com/깃헙아이디/레포지토리이름.git`

 <br>
 
## 해쉬키 값 생성하기

Settings*(레포지토리 세팅이 아니다. 깃허브 세팅임!)* - Developer settings - Personal access tokens - 토큰 생성(무기한)
<p  align="center"><img width="290" alt="image" src="https://user-images.githubusercontent.com/69746360/157176387-69a8518e-d4ca-4f24-847a-ad492a666198.png"></p>