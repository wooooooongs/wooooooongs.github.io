---
title:  "[Jekyll] 블로그 포스팅하는 방법"
excerpt: "공부하는 식빵맘 블로그를 통해 md 파일에 마크다운 문법으로 작성하여 Github 원격 저장소에 업로드 해보자. 에디터는 Visual Studio code 사용! 로컬 서버에서 확인도 해보자. "

categories:
  - Blog
tags:
  - [Blog, jekyll, Github, Git]

toc: true
toc_sticky: true
 
date: 2021-11-16
last_modified_at: 2021-11-16
---


# 첫 게시글! 안뇽하세요

### 드디어 블로그를 개설하게 되었다. <br>
vscode를 이용하여
_posts 폴더 안에 영어제목을 가진 .md파일을 생성하여 마크다운 형식으로 글을 작성한다.

아울러 변경된 사항을 일일이 git에 push할 필요 없이 터미널에서 <br>
```zsh
bundle exec jekyll serve --trace
```
위를 입력한 후 서버가 실행 되면
http://127.0.0.1:4000 주소로 이동하여 확인할 수 있다.  
<br>
**실시간 반영도 된다!**
![image](https://user-images.githubusercontent.com/69746360/141996182-54a537b1-a025-493a-b5f7-dcfe92d7e564.png)