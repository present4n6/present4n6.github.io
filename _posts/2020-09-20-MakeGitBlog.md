---
title: GitHub 블로그 따라하며 쉽게 만들기(1) - jekyll 사용
comments: true
author: Present4n6
categories: [GitHub, GithubBlog]
date: 2020-09-20 00:36:00 +0900
tags: [GitHub,GitHubBlog]
math: true
---

## **왜 깃허브 블로그인가?**  
블로그 플랫폼은 다양한 종류가 있습니다.  
tistory, github, velog, notion, naver 등이 있습니다.   
개인적으로 기술 블로그를 운영하고 싶어서 여러 플랫폼을 찾아봤는데요,  
제가 찾아보고 느낀점으로 플랫폼들을 평가해보자면 다음과 같습니다.  
* tistory
	* 장점 : 다루기 쉽다, 사용하는 사람이 많다, 무난하다
	* 단점 : 마크다운 문법에 뒤쳐지고 있다, 스킨찾기 힘들다
* github
	* 장점 : 코드 수정해서 입맛대로 개조 가능, GitHub와 연동
	* 단점 : 진입장벽이 높다
* velog
	* 장점 : 개발자 친화적, 간단하다
	* 단점 : 꾸미는 맛이 없다
* notion
	* 장점 : 편하다, 정리하기 좋음
	* 단점 : 구글 검색하기 까다로움, 용량 제한 
* naver
	* 장점 : 네이버에서 검색 잘 됨, 익숙하다
	* 단점 : 구글에서 검색 잘 안됨  

저는 깃허브 블로그를 선택했습니다.   
블로그는 꾸미는 맛이 있어야 하는데 벨로그는 너무 단순해서 꾸미는 맛이 없고  
티스토리에서는 제 마음에 드는 스킨을 못 찾았습니다.  
그래서 깃블로그를 선택하게 되었고 그렇게 해서 이 블로그가 만들어졌습니다.  
블로그를 만들고 첫 포스팅이 이번 게시물입니다 ㅎㅎ  
* * *

## **깃허브 블로그 만들기**  

### **1. 깃허브 레파지토리 생성하기**
* 깃허브 블로그를 만들기 위해서는 깃허브와 연동을 해야 합니다.  
깃허브와 연동을 하기 위해서는 레파지토리를 생성해줘야 합니다.  

![upload-image](/assets/post/makegitblog/1.png)  

* 그 후 Repository name에 Owner(본인 ID).github.io 로 입력합니다.  
또한 Initialize this repository with: 에 Add a README file 을 체크해줍니다.  

![upload-image](/assets/post/makegitblog/2.png)  

* 이 과정을 잘 완료했다면 웹 주소 창에 ID.github.io 로 검색을 해보면 창이 뜨는 것을 확인할 수 있습니다.  
이어서 Clone and Download 버튼을 누르면 주소가 나오는데 그 주소를 복사합니다.(저는 테스트로 만들어서 Code라고 뜹니다)  

![upload-image](/assets/post/makegitblog/3.png)  

* 그리고 Git 이 설치되어 있어야 하는데 설치를 안 하신 분들은 <https://git-scm.com/> 에서 할 수 있습니다.  
설치 파일을 실행하고 쭉 Next 넘기시면 됩니다.  

![upload-image](/assets/post/makegitblog/4.png) 

* Git이 설치되어 있으신 분들은 Git Bash를 실행하고 다음과 같이 입력하면 됩니다.

```console
$ cd [Repository를 저장할 폴더]
$ git clone [복사했던 주소]
```  
잘 진행했다면 해당 경로에 다음과 같이 레파지토리가 생성된 것을 확인할 수 있습니다.  

![upload-image](/assets/post/makegitblog/5.png) 
* * *

### **2. 깃허브 블로그 테마 입히기**  

* 깃허브 블로그는 깃허브에 올린 소스코드가 작동해서 보여주는 원리입니다.  
따라서 사용자가 소스코드를 마음대로 바꿀 수 있다는 장점이 있습니다.  
그렇다고 無에서 하나하나 개발할 필요는 없습니다.  
Jekyll 라는 미리 만들어져 있는 테마를 가져와서 입맛에 맞게 수정해주면 됩니다.  
<http://jekyllthemes.org/>  

* 위 링크에서 여러 개의 테마를 확인할 수 있습니다.  

![upload-image](/assets/post/makegitblog/6.png) 

* 마음에 드는 테마를 고른 후 소스코드 파일을 다운로드해서 압축을 해제하고 만들었던 레파지토리 폴더에 복사해서 붙여줍니다.  

![upload-image](/assets/post/makegitblog/7.png) 

* 레파지토리에 파일을 넣었다면 다음과 같이 입력해서 Github에 파일이 연동될 수 있도록 commit 해줘야 합니다.  

```console
$ cd [Repository를 저장할 폴더]
$ git add .
$ git commit -m '메시지 입력'
$ git push origin master
```  
* \_config.yml 파일에서 블로그의 주소를 지정해주어야 한다.  
이 외에도 여러가지 소스코드들을 보고 본인 입맛대로 수정해서 커스터마이징하면 된다.  

![upload-image](/assets/post/makegitblog/8.png) 




